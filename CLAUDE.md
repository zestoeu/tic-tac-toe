# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `tictactoe.html` directly in a browser — no build step or server required:

```bash
open tictactoe.html
```

## Architecture

The entire project is a single self-contained file (`tictactoe.html`) with no dependencies, build tooling, or external assets. All HTML, CSS, and JavaScript live inline in that one file.

**Game state** (in the `<script>` block):
- `board` — flat 9-element array, `null | 'X' | 'O'`, indexed 0–8 (row-major)
- `WINS` — hardcoded list of the 8 winning index triples; used by `checkWinner()`
- `currentPlayer`, `gameOver`, `scores` — top-level mutable state

**DOM ↔ state flow**: clicks on `.cell[data-i]` elements drive `handleClick`, which writes to `board[]`, updates cell classes (`x`/`o`/`taken`/`win`), and calls `checkWinner()` after every move. `resetGame()` resets all state and strips classes back to `.cell`.

**Color palette** — dark navy background (`#1a1a2e`), X in red (`#e94560`), O in teal (`#4ecca3`).

## Git workflow

**After every meaningful change, commit and push to GitHub.** Do not batch multiple unrelated changes into one commit. The goal is that the remote always reflects current work so nothing is ever lost.

- Commit as soon as a logical unit of work is complete (a feature added, a bug fixed, a refactor done)
- Use clear, descriptive commit messages that explain *what* changed and *why*
- Always push immediately after committing: `git push`
- Remote: `https://github.com/zestoeu/tic-tac-toe`
