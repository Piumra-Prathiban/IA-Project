# CS188 — Search (Pac-Man Project)

Implementation of the **Berkeley CS188 "Search"** project. Pac-Man agents solve mazes and
eat Food using classic search algorithms (DFS, BFS, UCS, A\*) and custom heuristics.

> Version: **v1.004** · All runnable code lives in the [`search/search/`](search/search) folder.

---

## Section 1: Prerequisites

| Requirement | Version |
| --- | --- |
| Python | 3.9 – 3.11 |
| Package manager | Pip or Conda |
| OS | Windows / macOS / Linux |

Check that Python is available:

```bash
python --version
```

If it prints `3.9` – `3.11`, you are good to go. Otherwise install Python 3.11 from
<https://www.python.org/downloads/> (or use Conda as shown below).

---

## Section 2: Environment & Verification

**Requirements:** Python 3.9 – 3.11 | package manager Pip or Conda.

Create a new Conda environment and install the required packages:

```bash
conda create -n cs188 python=3.11
conda activate cs188
pip install numpy matplotlib
```

Verify the setup by playing a game of Pac-Man from inside the `search` folder:

```bash
cd search/search
python pacman.py
```

If a Pac-Man window opens and the game plays, the environment is correctly set up.

> **Note:** `numpy` and `matplotlib` are only needed for the graphical display. If you cannot
> open a GUI window (e.g. on a remote/headless machine), run with `--textGraphics` instead:
>
> ```bash
> python pacman.py --textGraphics
> ```

---

## Section 3: Running the Project

All commands below must be run **from inside the `search/search` folder**:

```bash
cd search/search
```

**Play a game manually (keyboard):**

```bash
python pacman.py
```

**Watch an agent solve a maze with a search algorithm:**

```bash
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python pacman.py -l bigMaze    -p SearchAgent -a fn=dfs
python pacman.py -l mediumMaze -p SearchAgent -a fn=ucs
python pacman.py -l mediumMaze -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic
```

**Useful options:**

| Option | Meaning |
| --- | --- |
| `-l <layout>` | Maze file from `layouts/` (without `.lay`), e.g. `mediumMaze` |
| `-p <agent>` | Agent class, e.g. `SearchAgent`, `GoWestAgent` |
| `-a fn=<algo>` | Search function to use: `dfs`, `bfs`, `ucs`, `astar` |
| `-a heuristic=<h>` | Heuristic for A\*, e.g. `manhattanHeuristic` |
| `-k <n>` | Number of games to play |
| `-q` | Quiet mode (no graphics window) |
| `--textGraphics` | ASCII graphics instead of a window |

**Run the autograder for your solutions:**

```bash
python autograder.py
python autograder.py -q q1          # grade a single question (q1 … q8)
python autograder.py -t test_cases/q1   # run a specific test case
```

---

## Section 4: Project Structure

```
IA-Project/
├── README.md
├── .gitignore
└── search/
    └── search/            <- run every command from here
        ├── pacman.py          main entry point
        ├── search.py          *** write your search algorithms here ***
        ├── searchAgents.py    *** write your agents/heuristics here ***
        ├── autograder.py      grading script
        ├── game.py            game engine
        ├── util.py            data structures (Stack, Queue, PriorityQueue)
        ├── layouts/           .lay maze files
        └── test_cases/        q1 … q8 autograder cases
```

---

## Section 5: Troubleshooting

- **`ModuleNotFoundError: No module named 'numpy'` / `matplotlib`** — the environment is not
  active. Run `conda activate cs188` (or install the packages into the interpreter you are using).
- **`python: command not found`** — try `python3` instead of `python`.
- **Graphics window does not open** — use `python pacman.py --textGraphics` or add `-q`.
- **`error: no such layout file`** — you are in the wrong directory. `cd search/search` first.
- **Pac-Man is stuck / no path found** — your search function may not be implemented yet in
  `search.py`; that is the expected starting state for the assignment.
