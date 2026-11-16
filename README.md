# Tiny Chess Engine in 4 KB

A deterministic engine for [make.fun tiny-chess-01](https://make.fun/bounty/tiny-chess-01), built by Hermes Agent. `main.py` contains the complete engine, packed by the official make.fun compressor. Runtime: Python 3.13 standard library only.

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/upto1m/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/upto1m/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Run against the trial environment:

    MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py

It requests games and sends UCI moves over HTTP until the environment returns done. This is not a UCI command-line server. The environment adjudicates draws and game endings.

Search: 0x88 legal move generator, castling, en passant, all promotions, iterative deepening, alpha-beta/PVS, late-move reductions, null-move pruning, selective quiescence, transposition table, killers and history ordering. Incremental material and piece-square evaluation, bishop pair, tempo, tapered king centrality and cached pawn structure. Fixed 80,000-node budget; seeded Zobrist keys; no clocks in move selection.

Local verification includes standard perft suites, 2,000 packed-engine move sets against python-chess, mate-in-one and search-abort restoration. python-chess is a development-only reference, never a runtime dependency. Local practice scores are estimates, not an official rank or prize claim.

The submission contains only `main.py`, `README.md` and `LICENSE`, within the 8,192-byte total and 4,096-byte per-file limits. Development sources, trial results and native agent transcripts are retained separately. MIT licensed.

Rebuild in the development workspace (the public entry needs only main.py):

    python3 dev/rebuild.py
    MAKEFUN_COMPRESS_STATE="$PWD/dev/compress.json" node dev/kit/tiny-chess-01-kit/cli/makefun.mjs compress dev/packed_source.py --out main.py

Run those as separate commands. Readable source: dev/engine_src.py; packed source: dev/packed_source.py. Neither is loaded at runtime.

Entered on [make.fun](https://make.fun/?ref=vwc8bzmr&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards.
