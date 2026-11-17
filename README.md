# tiny-chess-4k

A chess engine in 4,051 bytes of Python, written for the make.fun
tiny-chess-01 bounty. main.py is the whole engine: it plays the house
gauntlet through the env at MAKEFUN_ENV_URL with a deterministic
fixed-node-budget negamax search (alpha-beta + PVS, transposition
table, quiescence, tapered piece-square evaluation). No clock, no
randomness: the same position always gets the same move.

MIT licensed (see LICENSE).
