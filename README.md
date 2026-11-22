[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Aurora Velocity

Entry for make.fun tiny-chess-01: the strongest chess engine that fits in
4,096 bytes of Python.

A fresh implementation of the Aurora design, rebuilt around an undo-stack
make/unmake core. Moves are applied and reverted through a compact undo
record instead of copying the board, and the evaluation runs off
precomputed per-piece contribution tables, so the search spends its time
on chess rather than bookkeeping.

- Negamax with alpha-beta, PVS and late-move reductions
- Transposition table, killer moves, check extensions, null-move pruning
- Quiescence search over captures with MVV-LVA ordering
- Tapered evaluation: piece-square tables plus bishop-pair and pawn terms
- Node budget tiered by game length: 275k / 185k / 110k
- About 107,000 nodes per second in pure Python

Local results: 5.0/6 in the practice gauntlet (fitted Elo 1654), and a
9.5-2.5 win over the previous Aurora entry (entry #4, "Aurora Swift") in a
12-game head-to-head match played from the six gauntlet openings, colours
alternating. The head-to-head margin is what the final standings reward,
so this build supersedes it as the current entry.

`main.py` is the compressed entrypoint and stays under the 4,096-byte cap.
