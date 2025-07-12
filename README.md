[**Main Page**](README.md) | [**How to Use PyPRS**](./files/How%20to%20Use%20PyPRS.md) | [**Output**](./files/Output.md) | [**A Demo Application**](./files/A%20Demo%20Application.md) | [**MRG32k3a_numba**](./files/MRG32k3a_numba.md)


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
python -m pip install PyPRS.
```

<a href="./files/How to Use PyPRS.md"> Proceed to How to Use PyPRS</a>
