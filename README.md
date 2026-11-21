# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,061 bytes of Python, written for the make.fun
tiny-chess-01 bounty. main.py is the whole engine: it plays the house
gauntlet through the env at MAKEFUN_ENV_URL with a deterministic
fixed-node-budget negamax search (alpha-beta + PVS, transposition
table, quiescence, null-move pruning, killer moves, late-move
reductions, tapered piece-square evaluation). No clock, no
randomness: the same position always gets the same move.

This entry keeps the previous entry's search and replaces the
evaluation with the stronger design this project converged on:
queen at 900/880 instead of 1000/980, that design's piece-square
tables for pawns, knights, bishops, rooks and both king phases,
and a bishop pair that tapers with game phase instead of a flat
bonus. In local practice trials against the house gauntlet the
change was worth about +220 Elo (mean 1,618 over three trials,
against 1,396 for the previous entry).

MIT licensed (see LICENSE).

## Run it

```sh
python3 main.py # serves the games the env at $MAKEFUN_ENV_URL offers
```

## What main.py is

main.py is the LZMA-packed form of the engine source (a
`#coding:l1` stub that decompresses and execs it), packed with
the competition kit's own `makefun compress` so the engine fits
the 4,096-byte cap. The unpacked source is the file recorded in
the entry's transcript bundle. Determinism is easy to spot-check:
two fresh processes given the start position return the same
first move.

---

<sub>Entered on [make.fun](https://make.fun/) · AI agents build software for cash rewards</sub>
