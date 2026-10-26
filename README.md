# Raju & Prathyusha — Digital Wedding Invitation

A static, mobile-friendly wedding invitation for GitHub Pages. It uses the supplied temple-door opening video, exact wedding artwork, ivory-gold decorative frame, lotus divider, a scratch-to-reveal date, IST countdown, Instagram post embed, Google Maps, and guest messages.

## 1. Edit before publishing

Open `index.html` and find `const CONFIG` near the bottom.

- `weddingDate`: enter the actual muhurtham date/time with the India offset `+05:30`. Example: `2026-10-30T11:30:00+05:30` for 11:30 AM IST. The current `00:00:00` is a placeholder because the ceremony time hasn't been supplied.
- `venueName`, `venueAddress`: enter the actual venue details.
- `mapQuery`: use the venue name and address for the embedded map.
- `mapUrl`: paste the Google Maps share/directions URL.
- `instagramPostUrl`: already configured to the supplied post `https://www.instagram.com/p/DeJwS33E51p/`. Change it only if you want another public post or Reel.

The former local photo gallery has been replaced by an Instagram embed. It loads only when a guest presses **Load Instagram Post**. This avoids loading Instagram's third-party embed script until the guest chooses to view it. The post must be public and allow embedding. If Instagram blocks the embed, the **Open on Instagram** fallback remains available. Stories and private posts cannot be embedded.

## 2. Publish to GitHub Pages

1. Create a new GitHub repository. If using GitHub Free, make it public for the simplest setup.
2. Extract this ZIP and upload **the contents** of the `raju_prathyusha_github_pages` folder to the repository root. `index.html` must be at the root.
3. In the repository, open **Settings → Pages**.
4. Under Build and deployment, choose **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then Save.
6. Wait for the deployment and open the URL shown under Settings → Pages.

The included `.nojekyll` file tells GitHub Pages to serve static files without Jekyll processing. All asset paths are relative, so the site also works as a project site under `https://USERNAME.github.io/REPOSITORY/`.

## 3. Media / asset notes

- The opening video and local artwork are stored in `assets/`, so they do not depend on Google Drive viewer pages or thumbnail endpoints.
- Replace files in `assets/` if you'd like to use a different video or artwork. Keep the same filenames, or update the matching paths in `index.html`.
- Google Drive `/file/d/.../view` links are file-viewer pages, not direct video-stream URLs. For reliable opening-video playback on GitHub Pages, keep the MP4 bundled in `assets/`.
- Instagram is an external service. Browser privacy settings, content blockers, login requirements, private accounts, or the account's embed setting may prevent the embed from appearing. The direct Instagram link is provided as fallback.

## 4. Bug and security review applied

- Removed the photo slider and replaced it with a public-post Instagram embed flow.
- Instagram URLs are validated against `instagram.com` and allowed public post types (`/p/`, `/reel/`, `/tv/`); arbitrary embed domains are not accepted.
- The Instagram embed script is only loaded after a guest clicks to load the post.
- Uses `textContent` for configured venue strings rather than injecting them as HTML.
- External links use `rel="noopener noreferrer"` and HTTPS URL validation for the map button.
- Scratch canvas initializes only after the invitation is visible and samples progress less frequently to reduce repeated pixel-read work.
- Countdown interval is cleared when the target time has passed and on restarts.
- Video playback has an error/skip fallback, and the cover is removed from layout after the clip ends.
- Responsive styles, visible focus states, semantic labels, and reduced-motion support are included.

This is a static front-end site; it does not store personal data or use a backend.


## 5. Detailed GitHub hosting walkthrough (recommended: GitHub Desktop)

### Create the repository
1. Sign in at https://github.com/ and verify your email if prompted.
2. Open https://github.com/new.
3. Repository name: `raju-prathyusha-wedding` (or another short name).
4. Choose **Public** for the simplest GitHub Free setup.
5. Optionally select **Add a README file**, then click **Create repository**.

### Upload the full site reliably
1. Install GitHub Desktop: https://desktop.github.com/.
2. Open the new repository on GitHub and use **Code → HTTPS → Copy URL**.
3. In GitHub Desktop choose **File → Clone repository**, select the URL, and choose a local folder.
4. Extract this ZIP on your computer.
5. Copy all extracted website contents into the cloned repository folder. The repository root must contain `index.html`, `.nojekyll`, `README.md`, `INSTAGRAM_SETUP.txt`, and the `assets/` folder.
6. Do not put `index.html` inside an extra nested folder.
7. In GitHub Desktop, review changes, enter a commit message such as `Add wedding invitation`, click **Commit to main**, then **Push origin**.

### Enable GitHub Pages
1. Open the repository on GitHub.com.
2. Select **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Select branch `main` and folder `/(root)`, then click **Save**.
5. Wait for deployment. Return to **Settings → Pages** and open the published URL displayed there. A project site URL usually looks like `https://YOUR-USERNAME.github.io/raju-prathyusha-wedding/`; use the exact URL GitHub shows.

### Mobile test
1. Open the published URL on your phone.
2. Tap **Open Invitation**, confirm the video plays, then confirm the original invitation artwork appears.
3. Scroll to **Moments on Instagram** and tap **Load Instagram Post**.
4. If the embedded post doesn't render, tap **Open on Instagram**. Embedding requires a public post and can be affected by account settings or browser privacy controls.
5. Test scratch-to-reveal, countdown, map, buttons, and links.

## 6. Mobile UI/UX updates
- Comfortable 46–48px touch targets, adaptive button lettering, safe-area padding, responsive heading sizes, and smaller-screen spacing.
- Instagram actions become a single column on phones; the embed is constrained to the screen width.
- Instagram's third-party script only loads after the guest taps the load button.
- Opening video and original artwork remain bundled in `assets/` for reliable GitHub Pages delivery.

## 7. Public-site privacy
GitHub Pages content is publicly accessible on the internet. Only publish wedding photos, video, and details you are comfortable sharing publicly.
