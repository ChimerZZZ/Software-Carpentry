# Lazor Solver

## 📁 Project Structure

```
lazor_solver/
├── main.py              # Solver entry point
├── board.py             # Handles board creation and random block placement
├── laser.py             # Simulates laser trajectories and physics
├── lazor_parser.py      # Parses .bff files into usable data
├── solver.py            # Solver loop + output writer
├── utils.py             # Helper functions: grid display, set comparison
├── data/
│   └── *.bff            # Sample input files
├── solution.bff         # Output solution file
└── README.md            # You're here
```

---

## 🧩 Overview

The Lazor puzzle consists of:
- A grid made of fixed and movable blocks
- One or more lazors (with initial positions and directions)
- Target points that must be intersected by lazors
- Movable blocks: Reflect, Refract, Opaque, placed on allowed cells (`o`)

### Block Types

| Symbol | Type             | Behavior                        |
|--------|------------------|---------------------------------|
| `A`    | Reflect          | Reflects lazor 90°              |
| `B`    | Opaque           | Absorbs lazor                   |
| `C`    | Refract          | Splits lazor (reflect + pass)   |
| `o`    | Movable Block    | Valid position for A/B/C        |
| `x`    | Forbidden        | No block allowed                |

---

## 🚀 Getting Started

### (1) Add Puzzle File

Place your `.bff` puzzle file inside the `data/` directory.

Example:
```
data/tiny_5.bff
```

### (2) Run the Solver

Use the command below to launch the solver:

```bash
python main.py
```

When prompted:

```
Enter the name of a .bff file to solve: tiny_5.bff
```

Just type the filename located in the `data/` folder.

---

## ⚙️ How It Works

1. **Parsing**  
   The `.bff` file is parsed to extract:
   - Grid layout  
   - Lazor origins and directions  
   - Target points  
   - Movable block counts

2. **Board Sampling**  
   A random board layout is generated by placing available blocks (`A`, `B`, `C`) on valid `o` cells.

3. **Simulation**  
   Lazor trajectories are simulated across the board mesh. The laser interacts with blocks according to their type (reflect, absorb, split).

4. **Validation**  
   After simulation, the program checks whether all targets are hit by the laser beams.

5. **Iteration**  
   If a solution is not found, the solver retries with a new random layout, up to a specified number of iterations (`maxiter`).

---

## 🤝 Contribution

**Equally Contributed**

- **Chi Zhang**  
  - Designed the overall code structure and solver algorithm  
  - Implemented parser, laser physics, and main logic loop

- **Carl Ty Mellor**  
  - Refined and debugged `board.py` for accurate block placement  
  - Solved core logic issues to enable correct solution generation

---

## 📧 Contact

**Group Members:**
- Chi Zhang — [czhan213@jh.edu](mailto:czhan213@jh.edu)
- Carl Ty Mellor — [cmellor1@jh.edu](mailto:cmellor1@jh.edu)
