

# Note
For safekeeping - Javascript currently not necessary for the vault and therefore disabled for security.

# Script
```js-engine
const dv = engine.getPlugin('dataview').api;

function makeSuggester(property, value, bindName = null) {
  const pages = dv.pages().where(p => p[property] && p[property].includes(value));
  const options = pages.map(p => `option(${p.file.name})`).join(", ");

  // default bind name: property_value (so "categories_character")
  const bindTarget = bindName ?? `${property}_${value}`;

  return `\`INPUT[inlineListSuggester(${options}):${bindTarget}]\``;
}

// Example usage inside one JS view
const out = [];

out.push("**Organizations** | " + makeSuggester("categories", "organization"));
out.push("**Religions** | " + makeSuggester("categories", "religion"));
out.push("**Owned Locations** | " + makeSuggester("categories", "location", "ownedlocation"));
out.push("**Current Location** | " + makeSuggester("categories", "location", "location"));
out.push("**Allies** | " + makeSuggester("categories", "character", "character"));

return engine.markdown.create(out.join("\n"));

```

