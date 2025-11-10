## Quick orientation for AI coding agents

This repository implements an assignment-style Sudoku solver (student project). The key goals for an agent working here are to implement and/or fix the solver functions in `a5.py` so the provided puzzles can be solved and the interactive player in `play_sudoku.py` works correctly.

Keep guidance concise and focused on discoverable patterns in this repo (not generic coaching).

### Big-picture architecture
- `a5.py` contains the `Board` class and the core algorithm entry points: `find_most_constrained_cell()`, `failure_test()`, `goal_test()`, `update()`, and search functions `DFS()` / `BFS()`.
- `stack_and_queue.py` provides lightweight `Stack` and `Queue` classes used by `DFS` and `BFS`.
- `play_sudoku.py` contains a small interactive UI and `is_valid()` helper; it imports `Board` from `a5.py` and uses `play_sudoku()` to drive a game loop.
- `rubric.md` and `README.md` explain expected behaviors and grading rules (useful for implementing precise requirements and tests).

### Important project-specific conventions
- Board representation: `Board.rows` is a 9x9 structure where each cell is either
  - a list of possible numbers (e.g. `[1,2,3]`) for an unassigned cell, or
  - an int (e.g. `7`) for an assigned cell. Code must handle both shapes.
- Required attribute names: `num_nums_placed`, `size`, and `rows` must retain these exact names (autograder relies on them).
- Use `copy.deepcopy()` when expanding states for DFS/BFS so successor states do not share mutable lists.
- Use the provided helper `remove_if_exists(lst, elem)` when removing a value from possibility lists.

### Workflow / run commands (Windows PowerShell)
Make sure Python 3 is used. There are no external dependencies beyond the standard library.

Run the interactive player (reads input):
```powershell
python play_sudoku.py
```

Run the solver/tests in `a5.py`: the file contains commented test harness and sample runs. To execute, open `a5.py`, uncomment the bottom block that runs `test_dfs_or_bfs()` or the example `__main__` code, then:
```powershell
python a5.py
```

Before submitting / running autograder: the README explicitly requests students to comment out all `assert` statements and any calls to `test_dfs_or_bfs()` — preserve that behavior when preparing commits intended for grading.

### Typical modification targets with examples
- Implement `find_most_constrained_cell()` to scan `self.rows` and return coordinates of the shortest list (tie: first found). See the README/rubric for expected test cases used in the starter asserts.
- Implement `update(row, column, assignment)` to:
  1. Set `self.rows[row][column] = assignment` (an int).
  2. Increment `self.num_nums_placed`.
  3. Remove `assignment` from possibility lists in the same row, column, and 3x3 subgrid (use `subgrid_coordinates`).
- Implement `failure_test()` by scanning for any cell that is an empty list `[]` (unassigned but no possibilities).
- Implement `goal_test()` by comparing `self.num_nums_placed` to 81 (complete board) — the README notes this is an acceptable check.
- Implement `DFS()` / `BFS()` to push the initial board onto `Stack` / `Queue`, loop until empty, test goal/failure, find most constrained cell, iterate over its possible assignments, deepcopy the board, call `update()` on the copy, and push/enqueue.

### Debugging notes and pitfalls to avoid
- Be careful not to rename or remove the provided helper functions/attributes — autograder and `play_sudoku.py` import them directly.
- Cells switch types (list -> int) after `update()`; code that assumes a list in all cells will break.
- When creating new board states during search, always deepcopy. Mutating a shared list will introduce subtle bugs.
- The `Stack` and `Queue` classes copy the `initial` list in the constructor. That avoids shared default-list pitfalls — you can use them directly.

### Example small tasks for an agent
- Fill in `find_most_constrained_cell()` and run the small asserts in `a5.py` (uncomment tests, run, then re-comment before push).
- Implement `update()` and validate with the `update` tests present in the bottom of `a5.py`.
- Implement `DFS()` and `BFS()` and run the example puzzles included in `a5.py`.

If any parts of the repository are unclear, ask a short clarifying question referencing the exact file and function name (e.g., "Should `update()` treat assignments already present in the row as errors, or just ignore them?").

---
If you'd like, I can now create or merge this file into `.github/copilot-instructions.md` (I will preserve any existing content if present). Tell me to proceed or request edits to the draft above.
