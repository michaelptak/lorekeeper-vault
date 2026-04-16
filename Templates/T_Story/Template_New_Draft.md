<%*
let selectedStory;
let storyFile;

// Try to infer story from a visible Story-tagged note in the workspace
const leaves = app.workspace.getLeavesOfType("markdown");
for (const leaf of leaves) {
    const file = leaf.view?.file;
    if (file) {
        const cache = app.metadataCache.getFileCache(file);
        if (cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title) {
            selectedStory = cache.frontmatter.story_title;
            storyFile = file;
            break;
        }
    }
}

// If not inferred, prompt for story
if (!selectedStory) {
    const storyFiles = app.vault.getFiles()
        .filter(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title;
        });

    if (storyFiles.length === 0) {
        new Notice("No existing stories found. Create a Story note first.");
        return;
    }

    const storyTitles = storyFiles.map(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache.frontmatter.story_title;
    });

    selectedStory = await tp.system.suggester(storyTitles, storyTitles);
    if (!selectedStory) return;

    storyFile = storyFiles.find(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache.frontmatter.story_title === selectedStory;
    });
}

// Discover existing draft folders
const storyPath = `Story/${selectedStory}`;
const allFolders = app.vault.getAllFolders();
const draftNumbers = allFolders
    .filter(f => f.path.startsWith(storyPath + "/Draft "))
    .map(f => {
        const match = f.path.match(/Draft (\d+)$/);
        return match ? parseInt(match[1]) : null;
    })
    .filter(n => n !== null)
    .sort((a, b) => a - b);

if (draftNumbers.length === 0) {
    new Notice("No drafts found. Create a chapter first.");
    return;
}

// Select source draft (skip prompt if only one)
let sourceDraft;
if (draftNumbers.length === 1) {
    sourceDraft = draftNumbers[0];
} else {
    const draftLabels = draftNumbers.map(n => `Draft ${n}`);
    sourceDraft = await tp.system.suggester(draftLabels, draftNumbers, false, "Copy from which draft?");
    if (sourceDraft === null || sourceDraft === undefined) return;
}

// Determine new draft number
const newDraftNum = Math.max(...draftNumbers) + 1;
const newDraftFolder = `${storyPath}/Draft ${newDraftNum}`;

// Create the new draft folder
await app.vault.createFolder(newDraftFolder);

// Copy chapter files from source draft to new draft
const sourcePath = `${storyPath}/Draft ${sourceDraft}`;
const chapterFiles = app.vault.getFiles()
    .filter(f => f.path.startsWith(sourcePath + "/") && f.extension === "md");

for (const file of chapterFiles) {
    const content = await app.vault.read(file);
    // Update the draft property in frontmatter
    const updatedContent = content.replace(
        /^(draft:\s*)\d+/m,
        `$1${newDraftNum}`
    );
    const newPath = `${newDraftFolder}/${file.name}`;
    await app.vault.create(newPath, updatedContent);
}

new Notice(`Draft ${newDraftNum} created with ${chapterFiles.length} chapters copied from Draft ${sourceDraft}.`);

// Create a new dashboard for the new draft
const allFiles = app.vault.getFiles();
const sourceDashboard = allFiles.find(f => {
    const cache = app.metadataCache.getFileCache(f);
    return cache?.frontmatter?.tags?.includes("Story") &&
           cache?.frontmatter?.story_title === selectedStory &&
           cache?.frontmatter?.draft === sourceDraft;
});

let newDashFile;
if (sourceDashboard) {
    let dashContent = await app.vault.read(sourceDashboard);
    // Replace frontmatter draft number
    dashContent = dashContent.replace(/^(draft:\s*)\d+/m, `$1${newDraftNum}`);
    // Set active_draft to false (user can switch below)
    dashContent = dashContent.replace(/^(active_draft:\s*).+/m, `$1false`);
    // Replace static Draft N references in folder paths and labels
    dashContent = dashContent.replace(new RegExp(`Draft ${sourceDraft}`, 'g'), `Draft ${newDraftNum}`);
    // Replace Base filter: draft == N
    dashContent = dashContent.replace(new RegExp(`draft == ${sourceDraft}`, 'g'), `draft == ${newDraftNum}`);
    // Replace Dataview filter: draft = N
    dashContent = dashContent.replace(new RegExp(`draft = ${sourceDraft}`, 'g'), `draft = ${newDraftNum}`);

    const newDashPath = `${storyPath}/${selectedStory} - Draft ${newDraftNum}.md`;
    newDashFile = await app.vault.create(newDashPath, dashContent);
    new Notice(`Dashboard created: ${selectedStory} - Draft ${newDraftNum}`);
}

// Ask whether to switch the active draft
const switchDraft = await tp.system.suggester(
    ["Yes — switch active draft", "No — keep current draft"],
    [true, false],
    false,
    `Switch dashboard to Draft ${newDraftNum}?`
);

if (switchDraft) {
    // Set all existing dashboards for this story to inactive
    const existingDashboards = allFiles.filter(f => {
        const cache = app.metadataCache.getFileCache(f);
        return cache?.frontmatter?.tags?.includes("Story") &&
               cache?.frontmatter?.story_title === selectedStory;
    });
    for (const dash of existingDashboards) {
        await app.fileManager.processFrontMatter(dash, (fm) => {
            fm.active_draft = false;
        });
    }
    // Set the new dashboard to active
    if (newDashFile) {
        await app.fileManager.processFrontMatter(newDashFile, (fm) => {
            fm.active_draft = true;
        });
    }
    new Notice(`Active draft switched to Draft ${newDraftNum}.`);
}

// Self-delete this temporary note
const currentFile = tp.config.target_file;
setTimeout(async () => {
    await app.vault.delete(currentFile);
}, 500);
_%>
