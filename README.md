# walkies-site

Website for **Walkies** (on the App Store as *Walkies: Dog Walker Arcade*), a one-finger iPhone game about a dog walker and six leashes.
*Six leashes. Try not to tangle.*

The pages assume GitHub Pages at <https://jakeintech.github.io/walkies-site/> (from `main` /), the same pattern as the other `*-site` repos. If the address changes, replace that base URL in every page's `canonical`, `og:url`, `og:image` and `twitter:image`, in `robots.txt`, in `sitemap.xml`, and the `/walkies-site/` prefix in `404.html`.

| Page | URL |
|---|---|
| Home (App Store marketing URL) | `/` |
| Press kit | `/press.html` |
| Support and FAQ (App Store support URL) | `/support.html` |
| Privacy Policy (App Store privacy URL) | `/privacy-policy.html` |
| Terms of Service | `/terms-of-service.html` |
| Not found | `/404.html` |

Keep the home, support and privacy URLs as they are: `appstore/listing.json` in the game repo points at them. The copy on the home page follows that listing; change the two together.

## Image slots to fill

These files do not exist yet. The pages already point at them and fall back as described until they do.

| File | Size | Used for | Until it exists |
|---|---|---|---|
| `assets/screens/screen-1.png` | iPhone portrait, for example 1290 x 2796 | First phone in "On your iPhone" on the home page | A drawing with a "Screenshot soon" chip |
| `assets/screens/screen-2.png` | same | Second phone | same |
| `assets/screens/screen-3.png` | same | Third phone | same |
| `assets/icon.png` | Square, 512 x 512 or larger | Header and closing icon on every page, `apple-touch-icon` | The paw mark, `assets/favicon.svg` |
| `assets/og.png` | 1200 x 630 | Link previews (`og:image`, `twitter:image`) | Link previews show no image |

Each slot is an `<object>` whose inner content is the fallback, so dropping the file in is enough: no HTML change. When the screenshots are real, change each slot's `aria-label` in `index.html` to describe the screenshot, and update the "Screenshots, icon and video" section of `press.html`.

## How it is built

Plain HTML and one stylesheet, `assets/site.css`. No build step and no JavaScript (the one `<script>` is JSON-LD).

- **Look:** "Daylight map" by day (warm paper ground `#F2EEE4`, white surfaces, ink `#1C1C19`) and "Night walk" under `prefers-color-scheme: dark` (ground `#0F1412`, surfaces `#1C2521`). Cards have no border and no shadow, 26px corners, and a touch of dot texture at the right edge. The primary button is ink. Coat yellow `#F5B700` appears only on the walker and on the Big client card. All colours are custom properties at the top of `site.css`.
- **Type:** Inter Tight, 500 for text and 800 for titles and numerals, loaded from Google Fonts. This is the site's only third-party request, and the privacy policy says so. To drop it, self-host the font and edit section 7 of `privacy-policy.html`.
- **Art:** the park scenes are flat inline SVG that use the theme's colours: white paths, thin leashes with no casing, houses as rounded squares with a leash-coloured dot. `assets/dogs/` holds outline-free copies of `design/dogs/` from the game repo, with collars in this site's leash colours. `assets/icons/` is a copy of `design/icons/`. Each dog sits on a faint disc of its leash colour so pale and dark coats stay visible on both grounds.
- **Night colours not in the brief:** the night path, pond, tree and house colours, and the night green, orange and pink leashes, were chosen to sit with the given ones. They are the `--road`, `--pond`, `--tree`, `--house` and `--leash-4` to `--leash-6` values in the dark block of `site.css`.
- **Store state:** the game is not released. Every page keeps `<!-- appmeta -->` and `<!-- store-cta -->` markers, and `press.html` keeps `<!-- store-release -->`, where the Smart App Banner, the App Store link and the release line go on launch day. Add the offer and `downloadUrl` to the JSON-LD in `index.html` then too.
- **404:** GitHub Pages serves `404.html` for a missing path at any depth, so its links start with `/walkies-site/`. Preview it from a server that serves this folder at `/walkies-site/`.
- **robots.txt:** on a project site at `jakeintech.github.io/walkies-site/` crawlers do not read this file; they only read one at the root of the host. It takes effect on a custom domain.

## Contact

info@jakeawilliams.com
