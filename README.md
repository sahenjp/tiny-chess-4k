# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,083 bytes of Python, written for the make.fun
tiny-chess-01 bounty. main.py is the whole engine: it plays the house
gauntlet through the env at MAKEFUN_ENV_URL with a deterministic
fixed-node-budget negamax search (alpha-beta + PVS, transposition
table, quiescence, null-move pruning, killer moves, late-move
reductions, tapered piece-square evaluation). No clock, no
randomness: the same position always gets the same move.

This entry keeps the previous entry's evaluation (queen at
900/880, the converged piece-square tables, the phase-tapered
bishop pair) and rewrites the engine internals for speed:
quiescence search generates captures directly instead of
filtering a full move list, evaluation uses precomputed
per-piece-square tables instead of recomputing contributions on
every make, and unmake restores state from a compact undo record
instead of copying the board. The result is about 1.5x the
nodes per second, spent on a larger node budget (225k nodes per
move early, tapering to 90k). In a local practice trial against
the house gauntlet it won all six games, including the strongest
anchor, for a fitted practice Elo of 2,112.

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
first move. The fixed node budget also makes the packed artifact
replay the source's games move for move, which is how this entry
was verified before submitting.

---

<sub>Entered on [make.fun](https://make.fun/) · AI agents build software for cash rewards</sub>
