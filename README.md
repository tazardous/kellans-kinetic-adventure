# Kellan's Kinetic Adventure

An EGA-style side-scrolling platformer, in the spirit of the 1992 shareware
classics, starring Kellan and his big sister Diana, with their dog Bernie. One self-contained HTML file with no build step. The only
network request is for the Press Start 2P font from Google Fonts. Offline, the
game falls back to a system monospace font.

## Deploy

Settings -> Pages -> Deploy from a branch -> main -> / (root). Then open the URL in
Chrome on the phone and use the menu to Add to Home screen. The installed app
opens full screen in landscape.

Everything is relative-pathed, so a project subdirectory works.

## Heroes

- **Kellan** — four, blond hair, blue eyes, blue space suit.
- **Diana** — Kellan's big sister, six, reddish hair in a ponytail, brown eyes,
  purple space suit.
- **Bernie** — their dog, who gives the hints and rides along in the truck.

Pick Kellan or Diana on the title screen (↓ or C on a keyboard, BOMB on touch).
Both have the same sticky-mitten moves. Whoever isn't playing drives the rescue
truck at the end of each level. The choice is remembered.

## Playing

| Action      | Keyboard               | Touch            |
|-------------|------------------------|------------------|
| Run         | ← → or A D             | ◀ ▶              |
| Jump        | ↑, Space, W or Z       | ▲                |
| Throw bomb  | X, J or B              | BOMB             |
| Pause       | P or Esc               | II               |
| Music/sound | M (cycles music + sound, sound only, quiet) | ♪ |

- **Sticky mittens** — jump at a wall and keep pushing toward it to stick. Jump
  again to climb. Blue ice walls are too slippery.
- **Bop bad guys** by landing on them: slime blobs, bunny-hoppers and buzzing
  bugs. Spiky plants need a bomb.
- **Bombs** blow up cracked rocks and anything nearby. Kellan is never hurt by his
  own bombs.
- **Bernie** gives the hints, and **checkpoint flags** save your spot.
- **Red springs** bounce Kellan high. In Dino Valley he can ride the triceratops
  and the long-neck dinosaur.
- Reach the **red rescue truck** to finish the level.

There is no game over. Running out of hearts or falling in the goo puts Kellan back
at the last flag. Progress and best score are kept in localStorage.

## Music

Each screen has its own original chiptune loop in the style of an old PC speaker:
a bouncy march on the title, an oom-pah tune in Bubble Meadow, a spooky echo in
Crystal Caverns and a stompy dinosaur tune in Dino Valley. The tunes are written
as note strings in `TUNES` inside `index.html`, for example `C5:2` is C in octave 5
for two sixteenths and `R:4` is a rest.

## Levels

1. **Bubble Meadow** — the tutorial: running, bopping, wall climbing and bombs.
2. **Crystal Caverns** — a tall shaft, ice walls, springs, goo pits and a big cliff.
3. **Dino Valley** — dinosaur rides, floating leaves and volcanoes.

Levels are built in code with `mk(width, height, theme, name, hints, builder)` in
`index.html`. The builder uses `ground`, `fill`, `goo`, `set` and `e` (entity), so
adding a level means writing one more builder function.

## Updating

Edit, bump `CACHE` in `sw.js`, push. Without the version bump the phone keeps
serving the cached copy.
