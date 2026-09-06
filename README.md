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

# Sticky notes in n8n only render **Markdown**, and Markdown has no native video-embed syntax — no `<iframe>`, no player. So you can't get an actual playable video inside a sticky note. But there are two practical workarounds:

## Option 1: Thumbnail image that links to the video (most common)
Use the video's thumbnail image, wrapped in a link — clicking it opens the video in a new tab.

**YouTube:**
```markdown
[![Watch the video](https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg)](https://www.youtube.com/watch?v=VIDEO_ID)
```
Replace `VIDEO_ID` with the part after `v=` in the YouTube URL (e.g. `dQw4w9WgXcQ`).

**Facebook:**
Facebook doesn't expose a predictable public thumbnail URL like YouTube does, so the easiest approach is:
1. Grab a screenshot/thumbnail of the video yourself (or use Facebook's Graph API `/video_id/picture` endpoint if you have API access).
2. Host that image somewhere public (GitHub raw link, imgur, etc., like you did with the screenshot earlier).
3. Link it the same way:
```markdown
[![Watch the video](YOUR_HOSTED_THUMBNAIL_URL)](https://www.facebook.com/watch/?v=VIDEO_ID)
```

## Option 2: Plain text link
If you don't need a thumbnail, just:
```markdown
[▶ Watch on YouTube](https://www.youtube.com/watch?v=VIDEO_ID)
```

## Syntax

```
@[youtube](VIDEO_ID)
```

Just the video ID (the part after `v=` in the URL), not the full link. For your example:
```
@[youtube](qsrVPdo6svc)
```

## For Facebook

Following the same pattern, n8n's embed syntax also supports other providers. Try:

```
@[facebook](VIDEO_ID_OR_URL)
```

Since I can't verify the exact Facebook syntax from search results, I'd suggest testing it directly in your sticky note — if `@[facebook](...)` doesn't render, fall back to the thumbnail-link method I mentioned earlier for Facebook specifically, since n8n's embed providers are typically limited to a fixed list (YouTube being the most commonly documented one) n8n added Markdown support to sticky notes allowing teams to embed images and YouTube videos directly, turning sticky notes into rich documentation surfaces where developers can show examples of expected inputs or outputs without switching tools.

If Facebook isn't on the supported provider list, other common ones worth trying are `@[vimeo]`, `@[loom]`, or similar — n8n modeled this after common "oEmbed-style" shortcodes. Let me know what you find and I can help troubleshoot further.
