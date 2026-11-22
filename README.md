[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Aurora Clarity

Entry for make.fun tiny-chess-01: the strongest chess engine that fits in
4,096 bytes of Python.

The Aurora design (undo-stack make/unmake core, evaluation from
precomputed per-piece contribution tables) with one behavioural fix: the
transposition table is cleared before every move. Replaying a lost
gauntlet game showed that entries carried over from earlier searches in
the same game were distorting later decisions — fresh searches chose the
correct moves at every critical position, while sequential play
reproduced the losing ones. Each move now searches with a clean table.

- Negamax with alpha-beta, PVS and late-move reductions
- Transposition table, killer moves, check extensions, null-move pruning
- Quiescence search over captures with MVV-LVA ordering
- Tapered evaluation: piece-square tables plus bishop-pair and pawn terms
- Node budget tiered by game length: 275k / 185k / 110k
- About 107,000 nodes per second in pure Python

Local results across two practice gauntlet sets: 5.0/6 (fitted Elo 1654)
and 5.5/6 (fitted Elo 1809), a combined 10.5/12 against 9.5/12 for the
previous entry ("Aurora Velocity"). Both games that entry lost — the
Slav against the 250k-node anchor and the Ruy Lopez against the
100k-node anchor — are wins for this build.

`main.py` is the compressed entrypoint and stays under the 4,096-byte cap.
