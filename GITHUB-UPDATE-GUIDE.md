# Safe GitHub update workflow for version 3

Recommended branch:

`feature/apple-health-sync-v3`

Recommended commit message:

`Add Apple Health Shortcut bridge v3`

## Before changing GitHub

1. Open the currently published Recomp app.
2. Tap **Export backup** and keep the JSON file.
3. Confirm that the GitHub repository and Pages URL will remain the same.

## Create the branch in GitHub

1. Open the repository on GitHub.
2. Open the branch selector, which currently shows `main`.
3. Type `feature/apple-health-sync-v3`.
4. Choose **Create branch: feature/apple-health-sync-v3 from main**.
5. Confirm the branch selector now shows the new branch.

## Upload this release to the branch

1. On the new branch, choose **Add file → Upload files**.
2. Upload the files from this release folder into the same repository location as the current `index.html`.
3. Replace the existing files when GitHub reports matching names.
4. Commit with `Add Apple Health Shortcut bridge v3`.

At minimum, replace:

- `index.html`
- `manifest.webmanifest`
- `sw.js`

Also upload the icons if they are not already present. The Markdown guides, `.nojekyll`, `CHANGELOG.md`, and `VERSION` are recommended but do not affect the app runtime.

## Review before publishing

On the branch, verify:

- `index.html` contains `rt_activity`;
- `sw.js` contains `recomp-pwa-v3-apple-health`;
- the original storage keys still appear unchanged;
- GitHub shows only the intended files in the branch comparison.

## Merge to main

1. Choose **Contribute → Open pull request**, or open the repository’s **Pull requests** tab.
2. Base branch: `main`.
3. Compare branch: `feature/apple-health-sync-v3`.
4. Create the pull request.
5. Review the file changes.
6. Choose **Merge pull request** and confirm.

If GitHub Pages is configured to deploy from `main` and the repository root, the merge publishes version 3.

## Refresh the iPhone app

1. Open the GitHub Pages URL once in Safari and refresh it.
2. Fully close the Recomp Home Screen app.
3. Reopen it. A second close/reopen may be needed while the new service worker takes control.
4. Confirm the **Apple Watch activity** card appears.
5. Do not delete the Home Screen icon and do not clear Safari website data.

## Rollback

If the new release has a problem, revert the merge commit in GitHub or restore the old files on `main`. The new `rt_activity` key is independent, so rolling back the code does not alter the original tracker data.
