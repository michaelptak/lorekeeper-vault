
# Note
For safekeeping - Javascript currently not necessary for the vault and therefore disabled for security.

# Script

```js-engine
const dv = engine.getPlugin('dataview').api;

const filterProperty = "categories";   // frontmatter property to filter on
const filterValue    = "character";    // value to match - only character notes
const fieldName = "friends";     // the actual field we're populating

// Query: WHERE categories contains "character"
// This finds all notes matching the filter criteria.
const pages = dv.pages()
  .where(p => p[filterProperty] && p[filterProperty].includes(filterValue));

// Turn into Meta Bind options
const options = pages.map(p => `option(${p.file.name})`).join(", ");

// Build the Meta Bind input string
const inputField = `\`INPUT[listSuggester(${options}):${fieldName}]\``;

return engine.markdown.create(inputField);
```

