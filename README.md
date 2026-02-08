---

# SudokuSMT

SudokuSMT is a Sudoku solver implemented in Python using **SMT (Satisfiability Modulo Theories)** with the Z3 solver.
Instead of using backtracking or brute force, the puzzle is modeled as a set of logical constraints and solved through formal reasoning.

This project demonstrates how real world rules can be translated into declarative constraints and solved by an SMT solver.

---

## Features

* Solves standard 9×9 Sudoku puzzles
* Uses SMT and constraint modeling instead of procedural algorithms
* Accepts input as plain text with 9 rows of characters
* Separates input parsing, constraint modeling, and solving
* Determines whether a puzzle is solvable or unsatisfiable

---

## Requirements

* Python 3.8 or newer
* Z3 SMT solver via Python bindings

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/USERNAME/SudokuSMT.git
cd SudokuSMT
```

### 2. Create and activate a virtual environment

**Windows (PowerShell):**

```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

**Linux or macOS:**

```bash
python3 -m venv env
source env/bin/activate
```

### 3. Install dependencies

```bash
pip install z3-solver
pip freeze > requirements.txt
```

---

## Input Format

The solver expects **9 lines**, each containing **9 characters**.

* Digits `1–9` represent fixed values
* `0` or `.` represent empty cells

Example:

```
900508007
080302905
054000080
070680032
100004008
500219060
000906001
726001040
001470056
```

---

## Usage

Run the solver:

```bash
python main.py
```

<img width="1067" height="690" alt="image" src="https://github.com/user-attachments/assets/4cf48580-bf70-4118-acff-ccd83af16ca9" />

Enter the Sudoku puzzle when prompted.
If the puzzle is solvable, the completed grid is printed.
If not, the solver reports that no solution exists.

---

## How It Works

* Each Sudoku cell is modeled as an integer variable constrained to values from 1 to 9
* Fixed cells are enforced using equality constraints
* Sudoku rules are expressed declaratively:

  * Rows contain distinct values
  * Columns contain distinct values
  * Each 3×3 subgrid contains distinct values
* The SMT solver checks satisfiability and extracts a model if one exists

No guessing, no recursion, and no backtracking logic. The solver relies entirely on constraint reasoning.

---

## Project Structure

```
SudokuSMT/
├── main.py
├── .gitignore
├── requirements.txt
└── README.md
```

---

## Future Improvements

* Detect invalid puzzles before solving
* Check for multiple solutions
* Add a verification-only mode
* Improve output formatting
* Extend to other grid sizes

---

