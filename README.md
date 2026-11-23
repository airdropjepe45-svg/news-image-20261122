# THE WORLD — 22 November 2026

[![make.fun · news-image-20261122](https://make.fun/badge/news-image-20261122.svg)](https://make.fun/bounty/news-image-20261122)
[![rank](https://make.fun/badge/news-image-20261122/airdropjepe45-svg/news-image-20261122/rank.svg)](https://make.fun/bounty/news-image-20261122)
[![reward](https://make.fun/badge/news-image-20261122/airdropjepe45-svg/news-image-20261122/reward.svg)](https://make.fun/bounty/news-image-20261122)

A newspaper-style front page summing up world news of Sunday 22 November 2026.
Every story carries its source in the image itself (BBC News, Al-Monitor, AFP,
Reuters, AP, SCMP, Yonhap, France 24, Euronews, the Guardian and more), and
nothing in the paper was invented: all 50 stories were first reported on
22 November 2026.

## Stories at a glance — the 3 top stories

1. Russia fires 186 drones at Ukraine
2. COP31 climate talks collapse without fossil-fuel deal
3. Iran strikes Bahrain as Gulf confrontation deepens

Then 10 mid stories with small illustrations — the Democrats' record House
majority, the AI sell-off that sank global stocks, Nvidia's SEC inquiry and
CEO resignation, Wembanyama's 50-point night, Verstappen's Las Vegas Grand
Prix win, India's record 720-9 in New Zealand, South Korea's AI-cheating
ministerial resignation, the Russian warship hit at Benghazi, Alcaraz's
first ATP Finals title and the Indonesia candy factory fire — and 37
numbered stories in the list at the foot of the page, ten of them pinned on
the world map.

## The image

`entry.png` (1024 × 1024) is an illustrated newspaper front page in colour:

- Masthead **THE WORLD** with **Sunday 22 November 2026** prominent, and
  a colour legend for the seven regions (Middle East, Europe, Asia-Pacific,
  Americas, Africa, World, Sport & Culture).
- **3 illustrated top stories** with flat vector-style scenes drawn in code:
  a night sky over Kyiv with drone silhouettes and air-defence bursts for
  the 186-drone attack, a globe and a crossed-out oil drop for the COP31
  collapse, and a night blast over a Bahraini industrial site.
- **10 mid stories**, each with a small icon, a headline and a one-line deck.
- **A dot-matrix world map** with ten numbered pins, and a numbered list
  carrying the remaining **37 stories**, one line each.
- A **DATE CHECK** box stating that every story on the page happened or was
  first reported on Sunday 22 November 2026, and none is from any earlier
  day or from 23 November.
- A footer line crediting the sources.

That is **50 stories in total, all first reported on 22 November 2026** — from
the 186-drone attack on Ukraine and the COP31 collapse in Antalya, through
the Iranian strike on Bahrain and the Democrats' record House majority, to
Alcaraz in Turin, Marquez's eighth MotoGP title and Cyclone Xavier near the
Cook Islands.

## How it is made

The image is drawn entirely in code by `main.ts` (Node 22, standard library
only, no network). It embeds real vector font outlines (DejaVu Serif Bold
for the masthead and headlines, DejaVu Sans for body text), filled with a
3x-supersampled scanline rasterizer so the letterforms read as normal
newspaper type, draws the masthead, the three illustrated scenes, the
mid-story icons, the dot-matrix world map (land as a union of ellipses) and
the DATE CHECK box, and encodes the PNG itself with `node:zlib` (deflate)
and a hand-rolled CRC32 — so the output is deterministic: no timestamps,
no randomness.

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
```

Running it twice produces a byte-identical `out/entry.png`.

## Verify

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
sha256sum out/entry.png
```

Expected: a 1024 × 1024 PNG of 116,519 bytes, SHA-256
`7bfe02c489661a25798be2765e2fbcb321a5b9917ff709fed3017a1ef6994bb6`.
Two runs in different directories produce byte-identical files.

The build also runs a fit check first and prints `fitOk=true` only when every
top headline fits in two lines, every top deck in two, every mid headline
in two, every mid deck in one line, and every numbered story in one line.
After a visual check, the map pins were re-spaced so no two overlap, the
Bahrain scene got a brighter factory and a bigger blast, and the lead story
is now the 186-drone attack on Kyiv with its own night-sky scene.

## License

MIT — see [LICENSE](LICENSE).
