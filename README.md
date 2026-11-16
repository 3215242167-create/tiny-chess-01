[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/3215242167-create/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/3215242167-create/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

A chess engine in 4 KB of Python: alpha-beta search with quiescence
(captures, promotions and check evasions), a transposition table and
piece-square evaluation on a 0x88 board, iterative deepening to a fixed
budget of 50,000 nodes a move. No clock, no randomness: the same
position always gets the same move, so a replayed trial matches.

`main.py` is the whole engine (MIT, see LICENSE). It is stored as an
lzma-compressed payload with a small unpacker (2,576 bytes as
committed); the unpacked program talks to the env at MAKEFUN_ENV_URL:
POST /game serves the game in play, POST /move plays the searched move,
and the loop ends when the env answers status "done". If the searched
move is ever absent from the env's legal-move list, it falls back to
the legal move with the best one-ply evaluation.
