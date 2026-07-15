# open-pool

Live scoreboard for a 4-person golf pool at The Open, published as a single static
`index.html` on GitHub Pages. Scores come from ESPN's public PGA leaderboard feed,
polled every 90 seconds in the browser — no backend, no build step.

## Updating the rosters

All the editable settings live in one `<script>` block near the top of
[`index.html`](./index.html), marked `EDIT ONLY THIS BLOCK`. Four knobs:

- **`POOL_NAME`** — the label in the top-right of the board.
- **`ROSTERS`** — one entry per team. Each has six `players` and one `alt`.
  Player names must match ESPN's `athlete.displayName` spelling exactly.
  Anything that doesn't match shows up in a banner on the page so you can fix it.
  Leave a slot as `''` if it isn't drafted yet.
- **`MC_RULE`** — `'worst'` or `'best'`. How missed-cut players are charged for
  R3 and R4 (highest round in the field vs. lowest).
- **`EVENT_ID`** — leave `null` to let the page find The Open automatically.
  If ESPN ever grabs the wrong tournament, set the ESPN `tournamentId` here,
  or append `?event=<id>` to the URL.

Commit and push to `main`; GitHub Pages picks it up within a minute or two.

## House rules

Best 4 of 6, combined to par. Lowest wins. Withdrawal → alternate takes the spot
(one alternate only). DQ → no substitute. Missed cut → keeps the 36-hole score,
then gets charged the field's worst (or best) round for R3 and R4.
