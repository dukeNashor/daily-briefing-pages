# Daily briefing Pages

Public static briefings containing source-linked AI news and market charts. The website reports its data cutoff and any incomplete or rejected market rows; it is not investment advice.

## Publication layout

- `index.html`: latest briefing
- `briefing-YYYY-MM-DD.html`: preserved daily edition
- `archive.html`: edition index
- `[a-f0-9]{16}.png`: content-addressed chart and editorial illustration assets
- `manifest-YYYY-MM-DD.json`: public-only metadata and SHA256 checksums
- `.nojekyll`: static publication without Jekyll

## Update procedure

1. Generate and validate the final briefing in the existing source workflow. Freeze its cutoff, content, public source links and SHA256. Keep partial-data warnings intact.
2. Extract embedded PNG bytes into content-addressed files and replace only matching image src values. Confirm restoring data URLs reproduces the source HTML byte-for-byte. All relative assets must resolve.
3. Publish only the files listed above. Exclude private links, account data, credentials, raw inputs, configuration, logs, delivery receipts, local paths and source-code history.
4. Add the dated edition, update latest index and archive, and preserve all previous editions and referenced assets. Revisions must keep an explicitly named prior revision.
5. Commit the validated files atomically to main. Small updates may use the GitHub connector's tree/commit/ref operations. For bulk files, GitHub's Add file → Upload files accepts the flat bundle without embedding large payloads in API requests. Check remote state before retrying an uncertain write. Never force-push.
6. GitHub Pages source is main, /(root), Deploy from a branch. A push starts publication. This repository has no cron or independent data collection schedule.
7. Confirm the build/deployment for the exact commit, then check the live page date/cutoff, manifest and image hashes, all three tabs, 5/20/60-session range controls, candle selection and keyboard navigation. A pending build is not a completed publication.

Source and archive workflows remain separate from this public output repository. Do not broaden repository, credential or account permissions to resolve publication failures.
