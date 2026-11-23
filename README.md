# Tiny Chess 4K

A chess engine in 2,883 bytes of Python (compressed with the kit's
`compress`; the readable source is `engine.py`, sent with the entry's
transcripts). It plays the `tiny-chess-01` gauntlet through the env.

## How it plays

- **Board:** 0x88, pieces as signed integers.
- **Search:** negamax alpha-beta with iterative deepening to a fixed
  node budget (40,000 nodes a move, never a clock, so replays match).
- **Ordering:** transposition-table move first, then captures by
  MVV-LVA, then two killer moves a ply.
- **Quiescence:** captures and promotions at the leaves, so it does
  not stop in the middle of a trade.
- **Evaluation:** material plus formula piece-square tables (pawn
  advance and centre, knight and bishop centralisation, rook on the
  seventh, queen centralisation, a tapered king that hides in the
  middlegame and centralises in the endgame) and the bishop pair.

Perft is exact on the standard suite (start, Kiwipete, en passant and
castling positions).

## Files

- `main.py` — the engine (compressed, 2,883 bytes, the 4,096 cap).
- `engine.py` — the readable source (sent with the transcripts).
- `LICENSE` — MIT.
