# GuinnGaming website

Plain HTML + CSS for the GuinnGaming studio site. No build step, no JavaScript, no cookies, analytics or trackers.
Fonts (Creepster for logos, Nunito for text) load from Google Fonts.

## What's here

| Path | Page |
|---|---|
| `index.html` | Studio home: hero, **Our games** grid, About, Contact |
| `fill-the-void/index.html` | Fill The Void game page |
| `fill-the-void/privacy/index.html` | Fill The Void privacy policy (the URL to give Play Console) |
| `404.html` | Not-found page (GitHub Pages serves it automatically) |
| `assets/css/style.css` | Shared styles for every page |
| `assets/img/` | Favicon, touch icon, Fill The Void icon |
| `fill-the-void/img/` | Game screenshots (WebP) |
| `_template/game/` | Copy-me template for a new game page + privacy policy |

## Publishing on GitHub Pages (later, with your own sign-in)

1. Create a GitHub account (e.g. `GuinnGaming`).
2. Create a repository named exactly `<username>.github.io` (e.g. `guinngaming.github.io`).
3. Push this folder to it. In the repo: **Settings > Pages > Deploy from a branch > main / (root)**.
4. The site appears at `https://<username>.github.io/`, and the privacy policy at
   `https://<username>.github.io/fill-the-void/privacy/`.
5. Put that privacy URL into Play Console and into section 10 of the policy, then delete the
   yellow "Review before publishing" note at the top of the policy page.

Notes:
- Pages link to each other with relative paths, so they also work when opened as local files.
  `404.html` uses root paths (`/...`), which is correct for a `<username>.github.io` site.
  (If you ever host it as a project site like `/<repo>/` instead, update the links in `404.html`.)
- Folders starting with `_` (like `_template/`) are **not published** by GitHub Pages' default
  Jekyll step, so the template stays private. Don't add a `.nojekyll` file unless you want it public.
- A custom domain (e.g. `guinngaming.com`) can be added later under Settings > Pages.

## Adding a new game

Each game gets a card on the home page, its own page at `/<game-slug>/`, and its own privacy policy at
`/<game-slug>/privacy/` (each Play listing needs its own policy URL). Existing URLs never move, so links
already in Play Console keep working.

1. **Copy the template:** copy `_template/game/` to a new folder named after the game, lowercase with
   dashes, e.g. `cp -r _template/game space-snacks`.
2. **Fill in the page:** in `space-snacks/index.html` replace every ALL-CAPS placeholder (GAME NAME,
   GAME TAGLINE, ONE-LINE PITCH, feature headings, alt text). Copy or delete feature blocks as needed.
3. **Add screenshots:** put WebP images in `space-snacks/img/` (about 540x960 for phone shots, quality
   ~78, under ~80 KB each) and swap them in for `img/placeholder.svg`. Delete `placeholder.svg` when done.
   Quick conversion: `cwebp -q 78 -resize 540 960 in.png -o img/shot-1.webp`
   (or Python Pillow: `Image.open(p).resize((540,960)).save(out, 'WEBP', quality=78)`).
4. **Write its privacy policy:** edit `space-snacks/privacy/index.html`. Start from the Fill The Void
   policy and change anything that differs (ad SDKs, purchases, age rating, date).
5. **Add the card:** in `index.html`, copy the `<article class="card game-card">` block between the
   `GAME CARD` comments, paste it at the top of the grid (newest first), and change the image, icon,
   name, one-line pitch, badge text and link. Badge options: `Coming soon to Google Play`,
   `Join the test`, `Get it on Google Play`.
6. Optionally add the game to the footer links, then commit and push.

## At launch (Fill The Void)

- In `fill-the-void/index.html`, replace the "Coming soon" `<span class="play-badge">` with a link to
  `https://play.google.com/store/apps/details?id=com.dutrut.fillthevoid` (instructions are in the HTML comment).
- Change the home card badge to `Get it on Google Play`.

## Still to fill in

- Final privacy policy URL (section 10) once the GitHub username is known.
- Postal address in the policy contact section, if required.
- Social links in the footers once the accounts exist.
- Trailer embed on the game page (optional).
