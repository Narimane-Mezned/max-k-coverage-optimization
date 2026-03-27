# Max-K Coverage Optimization

A specialized optimization toolkit that solves the **Maximum K-Coverage problem** using two distinct approaches: an **Exact MIP Solver (Gurobi)** for mathematical optimality and a **Fast Greedy Algorithm (KDTree)** for large-scale spatial datasets.

---

## Project Overview

This project addresses the challenge of selecting a limited number of resources ($k$) to provide the maximum possible coverage for a given population or set of points.

Instead of a single fixed method, the toolkit offers:
1. **Gurobi Integration:** A robust mathematical model for guaranteed optimal solutions.
2. **Spatial Heuristics:** A high-speed greedy implementation optimized with KDTree for millions of coordinates.
3. **Interactive GUI:** A graphical interface to manage parameters and visualize results easily.

This ensures **precision for small-to-medium problems** and **extreme scalability for Big Data**.

---

## Key Features

- Exact Integer Programming (MIP) with **Gurobi**
- High-speed greedy search using **scipy.spatial.KDTree**
- Interactive Desktop GUI (**Tkinter**)
- Seamless CSV data integration (`population.csv`, `candidates.csv`)
- Performance metrics (Execution time & Coverage score)
- Modular & clean architecture

---

## Architecture
```
max-k-coverage-optimization/
│
├── src/
│   ├── gurobi_maxkcover.py  # Gurobi MIP model & optimization logic
│   ├── greedy_fast.py       # KDTree-based greedy algorithm
│   ├── gui_gurobi.py        # Tkinter Graphical User Interface
│   │
│   ├── candidates.csv       # Dataset: Potential site coordinates
│   └── population.csv       # Dataset: Population/Points to cover
│
├── env/                     # Virtual environment
│
├── requirements.txt         # Project dependencies
└── README.md                # Documentation
```
---

## How It Works (Optimization Flow)

1. **Data Loading:** The system reads coordinates from `candidates.csv` and `population.csv`.
2. **Method Selection:**
   - **Gurobi:** Builds a binary decision matrix to find the absolute maximum coverage.
   - **Greedy:** Iteratively selects the best candidate by searching neighbors via KDTree.
3. **Constraints:** Both methods respect the $k$ limit (maximum number of sites to open).
4. **Output:** Returns selected indices, total coverage score, and solver logs.

---

## Installation

### 1️⃣ Clone the repository
```bash
git clone https://github.com/Narimane-Mezned/max-k-coverage-optimization.git
```
2️⃣ Create virtual environment
```Bash
python -m venv env
source env/bin/activate      # Linux / Mac
env\Scripts\activate         # Windows
```
3️⃣ Install dependencies
```Bash
pip install -r requirements.txt
```
▶️ Run the Application
To launch the interactive GUI:
```Bash
python src/gui_gurobi.py
```
Example Usage
Exact Solution (Gurobi)
```Bash
from src.gurobi_maxkcover import solve_max_k_coverage
# Load your data and solve
selected, coverage = solve_max_k_coverage(elements, sets, k=5)
print(f"Optimal sites: {selected}")
```
Fast Solution (Greedy + KDTree)
```Bash
from src.greedy_fast import FastGreedyCoverage
# Initialize with spatial radius
solver = FastGreedyCoverage(points, radius=0.5)
indices = solver.fit(k=5)
```

## Technologies Used
- Python 3.8+

- Gurobi Optimizer (Mathematical Solver)

- Scipy (Spatial KDTree)

- Pandas / NumPy (Data processing)

## Notes
- Gurobi License: A valid license (Academic or Commercial) is required to run the MIP solver.

- Data Format: CSV files should contain coordinate columns (lat, lon) for processing.

- Scalability: For datasets exceeding 100k points, the Greedy method is recommended.
