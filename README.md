# Brick Park

A sunny toy-brick playground that builds itself as you scroll. Brick Park is a single-page website with ten scroll effects, original minifig-style characters, and a few playable extras, all written in vanilla HTML, CSS, and JavaScript with no dependencies and no build step.

![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)
![Built with](https://img.shields.io/badge/built%20with-HTML%20%7C%20CSS%20%7C%20JS-E3342F)
![Dependencies](https://img.shields.io/badge/dependencies-none-2E9E4F)
![Deploy](https://img.shields.io/badge/deploy-GitHub%20Pages-1F6FD1)

**Live demo:** `https://tambesujal406-design.github.io/brick-park/`

<!-- Add a screenshot: save it as docs/preview.png, then replace this comment with:
![Brick Park preview](docs/preview.png) -->

## Features

### Ten scroll effects

| # | Effect | Where you see it |
|---|--------|------------------|
| 1 | Layered parallax | Hero: sun, clouds, hills, house, and Bo the Builder move at different speeds |
| 2 | Pinned heading | "Built brick by brick" stays fixed while the story plays |
| 3 | 3D card zoom | "Featured world" card tilts and zooms into view |
| 4 | Line-by-line reveal | Story lines appear one at a time |
| 5 | Sideways text | The "BUILD, PLAY, IMAGINE" strip slides as you scroll |
| 6 | Card arc carousel | "Meet the crew" cards fan out into an arc |
| 7 | Fixed 3D model | A spinning 3D brick follows you down the page |
| 8 | Stacking cards | "Pick a world" cards stack on top of each other |
| 9 | Focus-frame slider | "Postcards" gallery highlights the centered card |
| 10 | Scroll-triggered demo | A brick tower builds itself as you scroll |

### Interactive extras

- **Day-to-night sky:** the hero darkens into a starry night, and the house window glows
- **Minifig maker:** choose a hat, torso color, and leg color, or randomize
- **Build your own world:** an 8x8 baseplate where taps place and stack bricks
- **Catch the bricks:** a 15-second tap game with a best score
- **Rocket launch:** a countdown, shaking rocket, flame, and rushing stars
- **Tap-to-talk characters** with a synthesized brick-snap sound (Web Audio API)
- **Small surprises:** a title that assembles from falling letters, brick rain on the final button, and a hidden easter egg (tap the sun 5 times)
- **Light and dark support:** the sky, hills, and page tokens adapt to the visitor's color scheme

## Tech stack

- HTML5, CSS3 (custom properties, `position: sticky`, `scroll-snap`, 3D transforms, `mix-blend-mode`)
- Vanilla JavaScript (one `requestAnimationFrame`-throttled scroll loop)
- Web Audio API for sound effects
- Google Fonts: [Fredoka](https://fonts.google.com/specimen/Fredoka) (falls back to system fonts if blocked)

All characters and scenes are drawn with CSS shapes. There are no image files.

## Project structure

```
brick-park/
├── index.html          # Page markup and section skeletons
├── css/
│   └── style.css       # Design tokens, layout, and effects
├── js/
│   └── main.js         # Characters, scenes, games, and the scroll loop
├── assets/
│   └── favicon.svg     # Brick favicon
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
└── .gitignore
```

## Getting started

### Option 1: open the file

Download or clone the repo and double-click `index.html`.

### Option 2: run a local server (recommended)

```bash
git clone https://github.com/tambesujal406-design/brick-park.git
cd brick-park
python3 -m http.server 8000
```

Then visit `http://localhost:8000`. Any static server works (`npx serve`, VS Code Live Server, and so on).

## Deploy to GitHub Pages

1. Push the repo to GitHub (see [Publish from scratch](#publish-from-scratch)).
2. Open the repo on GitHub and go to **Settings**, then **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Choose branch **main** and folder **/ (root)**, then click **Save**.
5. Wait one to two minutes. Your site appears at `https://tambesujal406-design.github.io/brick-park/`.
6. Copy that link into the **Live demo** line above, and into the repo's **About** box (the gear icon on the repo home page) as the website.

## Publish from scratch

### With Git on a computer

1. Create a new **public** repository named `brick-park` on GitHub. Do not add a README, license, or `.gitignore` (this repo already has them).
2. In the project folder, run:

```bash
git init
git add .
git commit -m "feat: initial release of Brick Park"
git branch -M main
git remote add origin https://github.com/tambesujal406-design/brick-park.git
git push -u origin main
```

### With the GitHub website only

- **Computer:** create the repo, click **Add file**, then **Upload files**, and drag the unzipped project contents in (keep the `css`, `js`, and `assets` folders). Commit the changes.
- **Phone:** create the repo, then use **Add file**, then **Create new file** for each file. Type the full path in the name box (for example `css/style.css`), paste the file contents, and commit. A `/` in the name creates the folder automatically.

## Customize it

| I want to... | Change this |
|--------------|-------------|
| Change the sky, hills, or page colors | CSS variables on `:root` in `css/style.css` (light and dark sets) |
| Change brick and card colors | Hex values in `css/style.css` and `js/main.js` (search for `#E3342F`, `#1F6FD1`, `#FFD21F`) |
| Change parallax speed | `data-y` and `data-x` attributes on hero elements in `index.html` |
| Make the story section longer or shorter | `#story { height: 330vh }` in `css/style.css` |
| Edit characters and their speech | The `crew` array in `js/main.js` |
| Change sound pitch | The frequency numbers passed to `snap()` in `js/main.js` |
| Change the game length | The `15000` (milliseconds) in the `#gb` click handler in `js/main.js` |

Adding a fifth character to the arc also needs two more values in the angle and offset arrays inside `fr()` (`[-14,-5,5,14]` and `[16,0,0,16]`), plus a wider card row.

## Browser support

Works in current versions of Chrome, Edge, Safari 16 or newer, and Firefox. The page uses `overflow: clip`, `svh` units, and `position: sticky`, so very old browsers will fall back to a simpler layout.

## Accessibility notes

- Interactive characters and buttons are keyboard focusable, with a visible focus ring
- CSS transitions are turned off for visitors who prefer reduced motion
- Looping animations (waving, blinking, falling title letters) and scroll-linked movement still run, so a full reduced-motion mode is on the roadmap

## Roadmap

- [ ] Full `prefers-reduced-motion` mode for scroll-linked effects
- [ ] Save the best game score with `localStorage`
- [ ] Share or download your minifig as an image
- [ ] More characters, worlds, and game levels
- [ ] Optional background music toggle
- [ ] Split `main.js` into ES modules
- [ ] Add a preview screenshot and a Lighthouse report

## Contributing

Ideas and pull requests are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

## License

Released under the [MIT License](LICENSE).

## Credits and disclaimer

- The scroll-effect lineup was inspired by the "10 Scroll Effects" list shared by @crownzdesigns.
- Brick Park is an independent fan project. It is not affiliated with, authorized by, or endorsed by the LEGO Group. LEGO is a trademark of the LEGO Group. All characters, scenes, and artwork here are original and built from CSS shapes.
