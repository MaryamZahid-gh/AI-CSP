# Sudoku CSP Solver

A Constraint Satisfaction Problem (CSP)-based Sudoku solver implementing **Backtracking Search**, **Forward Checking**, and **AC-3 (Arc Consistency)** algorithms.

---

## Features

- Reads Sudoku boards from plain text files
- Solves puzzles of varying difficulty (easy → expert)
- Uses three core AI/CSP techniques:
  - **AC-3** – propagates arc consistency before and during search
  - **Forward Checking** – prunes domains after each assignment
  - **Backtracking Search** – explores the search space efficiently

---

## Input Format

Boards are read from `.txt` files with the following rules:

- Exactly **9 lines**, each containing exactly **9 digits**
- Digits `1–9` represent filled cells
- `0` represents an **empty cell**


---

## Algorithm Overview

### 1. CSP Formulation
| Component   | Definition                                                   |
|-------------|--------------------------------------------------------------|
| Variables   | Each of the 81 cells                                         |
| Domain      | Digits 1–9 (pre-filled cells have a fixed singleton domain) |
| Constraints | All-different in every row, column, and 3×3 box              |

### 2. AC-3 (Arc Consistency Algorithm 3)
Enforces arc consistency across all variable pairs before search begins. Reduces domains early, shrinking the search space significantly.

### 3. Forward Checking
After assigning a value to a variable, removes that value from the domains of all unassigned neighbors. If any domain becomes empty, triggers backtracking immediately.

### 4. Backtracking Search
Explores assignments depth-first. Uses:
- **MRV (Minimum Remaining Values)** heuristic to pick the next variable
- **Backtracking** when a dead end is detected

---

## File Structure

```
.
├── sudoku_csp.py       # Main solver implementation
├── easy.txt            # Easy puzzle
├── medium.txt          # Medium puzzle
├── hard.txt            # Hard puzzle
├── expert.txt          # Expert puzzle
└── README.md           # This file
```

---

## Output

The program prints the solved board to the console in a 9×9 grid format. If no solution exists, it outputs `No solution found.`

**Example Output:**
```
7 4 8 | 5 3 9 | 2 1 6
...
```

---

## Requirements

- Python 3.7+
- No external libraries required (standard library only)

---

## Course Info

**Assignment:** Question 3 – Sudoku Boards as CSPs  
**Institution:** National University of Computer & Emerging Sciences  
**Campus:** Chiniot-Faisalabad Campus
