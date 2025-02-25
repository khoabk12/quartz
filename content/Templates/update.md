<%*
const files = app.vault.getMarkdownFiles();
for (const file of files) {
    let content = await app.vault.read(file);
    if (content.includes("publish: true")) {
        content = content.replace("draft: false", "publish: true");
        await app.vault.modify(file, content);
        console.log(`Updated ${file.path}`);
    }
}
%>
