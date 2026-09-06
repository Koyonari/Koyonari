# Setup

This folder has everything that's safe for me to hand you outright: the
assembled `README.md`, and the two workflows I wrote myself (`snake.yml`,
`stats.yml`).

Two pieces are other people's original SVG art and a fairly large personal
script, so rather than paste their file contents in here (which I'd rather
not do wholesale), grab them directly from the source — it's the same two
minutes either way, and you're guaranteed a working, unmodified copy:

## 1. Head + contributions graph → from andriidrok1/andriidrok1

Go to https://github.com/andriidrok1/andriidrok1 and copy these into your repo:
- `scripts/generate_stats.py` → `scripts/generate_stats.py`
- any `hd-*.svg` heading graphics you want to reuse

(Their `ascii.svg` portrait isn't used standalone here — its animated art was
transplanted directly into the face column of `dark_mode.svg`/`light_mode.svg`
instead. Swap that art for your own portrait by editing the nested `<svg>`
block near the top of those two files.)

No extra secrets needed beyond the default `GITHUB_TOKEN` — the workflow
already passes it in.

## 2. Stats block → from Andrew6rant/Andrew6rant

Go to https://github.com/Andrew6rant/Andrew6rant and copy these into the
root of your repo:
- `today.py`
- `light_mode.svg`
- `dark_mode.svg`

Then:
- Edit the bio fields inside `light_mode.svg` / `dark_mode.svg` (name,
  LinkedIn, languages, etc.) to your own — they're currently Andrew's.
- Create a fine-grained personal access token with: `read:Followers`,
  `read:Starring`, `read:Watching`, `read:Contents`, `read:Metadata`,
  `read:Commit statuses`, `read:Issues`, `read:Pull Requests`.
- Save it as a repo secret named `ACCESS_TOKEN`.
- In `today.py`, change the hardcoded birthday in `daily_readme(...)` near
  the bottom, and remove/adjust the `add_archive()` call — that pulls in
  Andrew's own archived-repo history and doesn't apply to you.

## 3. GitHub graph (snake) → already wired up

`snake.yml` uses the public `Platane/snk` action directly — nothing to copy,
it'll just work once you push it, using `github.repository_owner` as the
username automatically.

## Once both are in place

Push to `main`. `stats.yml` runs once a day (and on manual dispatch) and only
touches the two source scripts if their files are present — so you can drop
in one piece at a time and the rest of the README still renders. `snake.yml`
runs every 6 hours and needs no setup at all.
