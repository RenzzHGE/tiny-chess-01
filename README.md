# tiny-chess-01

A compact chess engine in at most 4,096 bytes of Python (stdlib only) for
make.fun's tiny-chess-01: it plays the house gauntlet of 8 engines through
the env at `MAKEFUN_ENV_URL` and searches to a fixed node budget, never to
a clock, so every trial replays move for move.

## Run

    MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py

`main.py` is the whole engine: 0x88 board, alpha-beta with quiescence,
transposition table, MVV-LVA + killer move ordering, and a piece-square
evaluation. It reads, imports and runs no other file of this repository.

## Validation

Move generation is verified by perft (startpos 20/400/8902/197281,
Kiwipete 48/2039/97862, and two en-passant positions, all identical
before and after the final cleanup). Measured strength is about Elo
1177 against the house Sunfish baseline (1360).
