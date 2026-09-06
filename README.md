# n8n-screenshot

n8n sticky notes support Markdown, including images — so you just add a Markdown image tag pointing to the **raw** file URL (not the GitHub "blob" page URL, which is an HTML viewer, not the actual image).

## Steps

1. **Get the raw image URL.** Take your link and change it from the `blob` format to the `raw` format:
   - Your link: `https://github.com/mashunterbd/n8n-screenshot/blob/9316ba33c6226d4949cb12e95910bfc74238c796/threads-insights-report.png`
   - Raw link: `https://raw.githubusercontent.com/mashunterbd/n8n-screenshot/9316ba33c6226d4949cb12e95910bfc74238c796/threads-insights-report.png`
   
   (Just swap `github.com` → `raw.githubusercontent.com` and remove `/blob`.) Alternatively, GitHub also serves it via `?raw=true` on the original blob URL, but the `raw.githubusercontent.com` link is cleaner for embedding.

2. **Add a Sticky Note** in your n8n canvas (right-click → Add Sticky Note, or from the node panel).

3. **Double-click the sticky note** to edit it, and add Markdown image syntax:

```markdown
![Threads Insights Report](https://raw.githubusercontent.com/mashunterbd/n8n-screenshot/9316ba33c6226d4949cb12e95910bfc74238c796/threads-insights-report.png)
```
![Threads Insights Report](https://raw.githubusercontent.com/mashunterbd/n8n-screenshot/9316ba33c6226d4949cb12e95910bfc74238c796/threads-insights-report.png)

4. Click outside the note — n8n renders sticky notes as Markdown, so the image preview should now show inline.

## Notes
- Make sure the repo is **public** (yours appears to be), otherwise the raw URL won't load without auth.
- If the image doesn't render, resize the sticky note larger — n8n sometimes clips large images inside small note boxes.
- You can also just drag-and-drop or paste an image directly into some newer n8n versions' sticky notes, but the Markdown method above is the most reliable across versions.
