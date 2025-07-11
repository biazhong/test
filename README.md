# PyPRS: A Python Software Package for Parallel Ranking and Selection Procedures



**PyPRS** is a Python software package specifically developed to solve large-scale ranking and selection (R&S) problems in parallel computing environments. The underlying parallel computing framework is **Ray**. PyPRS incorporates four well-known parallel procedures: 

- **The Good Selection Procedure (GSP)**
- **The Knockout-Tournament (KT) Procedure**
- **The Parallel Adaptive Survivor Selection (PASS) Procedure**
- **The Fixed-Budget Knockout-Tournament (FBKT) Procedure**

Users can also upload custom procedures to test and compare performance against these built-in procedures.

---
## 📋 Prerequisites
- Python **3.10** is recommended for optimal compatibility.
- Required packages:  `ray==2.44.1`, `numpy`, `scipy`, `matplotlib`, `mrg32k3a_numba`. Install them using:
```bash
python -m pip install ray==2.44.1 numpy scipy matplotlib mrg32k3a_numba
```

## 📦 Installation
#### Option 1: Download from Repository
1. Download the PyPRS folder from the source repository.
2. Open it in a Python environment.
#### Option 2: Install from PyPI
```bash
python -m pip install ray==2.44.1 numpy scipy matplotlib mrg32k3a_numba
```

To use PyPRS, please visit the <a href="How to Use PyPRS.md"> How to Use PyPRS</a> page.
