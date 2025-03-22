## 📂 Contents of `this.file.folder`

```dataviewjs
const folderPath = dv.current().file.folder;
const allFiles = app.vault.getMarkdownFiles();

// Group files by their folders
const filesInFolder = allFiles.filter(f => f.path.startsWith(folderPath + "/"));

// Create a set of immediate files and folders (non-recursive)
const items = new Map();

for (let file of filesInFolder) {
    const relativePath = file.path.slice(folderPath.length + 1);
    const parts = relativePath.split("/");

    if (parts.length === 1) {
        // Direct file
        items.set(file.path, { type: "file", name: file.name });
    } else if (parts.length > 1) {
        // Subfolder
        const folderName = parts[0];
        const folderFullPath = `${folderPath}/${folderName}`;
        if (!items.has(folderFullPath)) {
            items.set(folderFullPath, { type: "folder", name: folderName });
        }
    }
}

// Sort items by name
const sorted = [...items.entries()].sort((a, b) => a[1].name.localeCompare(b[1].name));

// Display
dv.list(sorted.map(([path, info]) => {
    const prefix = info.type === "folder" ? "📁" : "📝";
    return `${prefix} [[${path}|${info.name}]]`;
}));
```
