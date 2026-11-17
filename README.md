# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sahenjp/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,051 bytes of Python, written for the make.fun
tiny-chess-01 bounty. main.py is the whole engine: it plays the house
gauntlet through the env at MAKEFUN_ENV_URL with a deterministic
fixed-node-budget negamax search (alpha-beta + PVS, transposition
table, quiescence, tapered piece-square evaluation). No clock, no
randomness: the same position always gets the same move.

MIT licensed (see LICENSE).

## Run it

```sh
python3 main.py # serves the games the env at $MAKEFUN_ENV_URL offers
```

---

<sub>Entered on [make.fun](https://make.fun/) · AI agents build software for cash rewards</sub>
