# PyPRS: Parallel Ranking and Selection in Python

**PyPRS** is a Python software package specifically developed to solve large-scale ranking and selection (R&S) problems in parallel computing environments. The underlying parallel computing framework is **Ray**. PyPRS incorporates four well-known parallel procedures: 

- **The Good Selection Procedure (GSP)**
- **The Knockout-Tournament (KT) Procedure**
- **The Parallel Adaptive Survivor Selection (PASS) Procedure**
- **The Fixed-Budget Knockout-Tournament (FBKT) Procedure**

Users can also upload custom procedures to test and compare performance against these built-in procedures.

## 📋 Prerequisites
Ensure Python is installed. We recommend **Python 3.10** for optimal compatibility.

## 1. 📦 Obtaining PyPRS
Users can acquire PyPRS via one of two methods:

### 1.1 Direct Download from Repository
1. Download the `PyPRS` folder from the repository, which includes the complete source code.
2. Deploy the source code in a Python environment.
#### ⚠️ Notes
Additional Python packages are required for PyPRS. Install them using:
```bash
python -m pip install ray==2.44.1 numpy scipy matplotlib mrg32k3a_numba
```
Required packages:
- `ray` (version 2.44.1)
- `numpy`
- `scipy`
- `matplotlib`
- `mrg32k3a_numba`
### 1.2 Installation via PyPI
Install PyPRS and its dependencies directly from the **Python Package Index (PyPI)**:
```bash
python -m pip install PyPRS
```
## 2. 🚀 How to Use PyPRS
This section provides instructions for running PyPRS on a **single computer** or a **cluster**.

### 2.1 Running PyPRS on a Single Computer
1. Navigate to the `UserInterface` package.
2. Execute the `GUI.py` file:
```bash
python GUI.py
```
Once the file is executed, the **Graphical User Interface (GUI)** will launch, allowing users to:
- Select a procedure
- Configure input parameters
- Upload required files
- Run the procedure

Below is a screenshot of the GUI:

  <img width="474.4" height="496" alt="image" src="https://github.com/user-attachments/assets/11314524-ebef-4662-b1dc-4b184b50c0db" />

#### 2.1.1 Setting Up a Built-in Procedure
To use a built-in procedure (e.g., GSP, KT, PASS, or FBKT), follow these steps:

##### 1) Configuring Input Parameters
Each procedure requires specific input parameters.  For detailed input parameters and their explanations for each procedure, see the details listed below:
- <a href="aaa">Input Parameters for GSP</a>
- <a href="aaa"> Input Parameters for the KT Procedure </a>
- <a href="aaa"> Input Parameters for the PASS Procedure</a>
- <a href="aaa"> Input Parameters for the FBKT Procedure</a>

##### 📋 Input Parameters for GSP

| Parameter                  | Explanation                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `n0`                       | Sample size for Stage 0.                                                   |
| `n1`                       | Sample size for Stage 1.                                                   |
| `r_bar`                    | Maximum number of rounds in Stage 2.                                       |
| `beta`                     | Average number of simulation samples per alternative in Stage 2.           |
| `alpha1, alpha2`           | Splits of the tolerable PICS alpha (i.e., `alpha = alpha1 + alpha2`).      |
| `delta`                    | Indifference-zone (IZ) parameter.                                          |
| `Number of Processors`     | Number of processors used to run the procedure.                            |
| `Repeat`                   | Number of times the problem is repeatedly solved.                          |
| `Reference Seed (Optional)` | Seed used to initialize random number generators.                          |


##### 📋 Input Parameters for KT Procedure

| Parameter                  | Explanation                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `delta`                    | Indifference-zone (IZ) parameter.                                          |
| `alpha`                    | Tolerable Probability of Incorrect Selection (PICS).                       |
| `g`                        | Number of alternatives in a group.                                         |
| `n0`                       | First-stage sample size for the KN procedure.                              |
| `Number of Processors`     | Number of processors used to run the procedure.                            |
| `Repeat`                   | Number of times the problem is repeatedly solved.                          |
| `Reference Seed (Optional)` | Seed used to initialize random number generators.                          |

##### 📋 Input Parameters for PASS Procedure

| Parameter                  | Explanation                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `n0`                       | Initial sample size.                                                       |
| `Delta`                    | Number of simulation samples taken per alternative each time.              |
| `c`                        | Constant that determines the boundary function.                            |
| `Termination Sample Size`  | Forces the procedure to stop when sample size exceeds this value.           |
| `Worker Elimination`       | Whether workers are used to eliminate alternatives.                        |
| `Number of Processors`     | Number of processors used to run the procedure.                            |
| `Repeat`                   | Number of times the problem is repeatedly solved.                          |

##### 📋 Input Parameters for FBKT Procedure

| Parameter                  | Explanation                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `N`                        | Total sampling budget.                                                     |
| `n0`                       | Sample size needed at the initial stage for seeding.                       |
| `phi`                      | Positive integer that determines budget allocation.                        |
| `Number of Processors`     | Number of processors used to run the procedure.                            |
| `Repeat`                   | Number of times the problem is repeatedly solved.                          |
| `Reference Seed (Optional)` | Seed used to initialize random number generators.                          |

##### 2) Uploading Required Files
In addition to configuring parameters, users must upload two files:

##### 📄 1. The `.txt` File
This file contains the parameter information for each alternative.

- **Structure**:

  - Each line represents one alternative.
  - The first entry is the index of the alternative (starting from 1, incrementing by 1).
  - The following entries are the parameter values (e.g., `x1`, `x2`, `x3`).
- **Example Format**:
```markdown
1 0.5 0.8 1.2
2 1.3 0.6 0.9
3 0.7 1.1 1.0
```
In this example:
- Alternative 1: `x1 = 0.5`, `x2 = 0.8`, `x3 = 1.2`
- Alternative 2: `x1 = 1.3`, `x2 = 0.6`, `x3 = 0.9`
- Alternative 3: `x1 = 0.7`, `x2 = 1.1`, `x3 = 1.0`

*Notes*: All values must be numerical. Non-numeric values will cause errors.

##### 🐍 2. The `.py` File
This file defines a Python function named `simulation_function`, which generates **simulation samples** from a given alternative using specific random number sequences.

***Function Signature***
```python
def simulation_function(argsSim, seedSim):
```
***Arguments***
- **`argsSim`** (List of Floats):
  - Contains the parameter information of the alternative.
  - Format matches the `.txt` file:
    - `argsSim[0]`: Index of the alternative.
    - `argsSim[1]`, `argsSim[1]`, etc: Parameter values (e.g., `x1`, `x2`, `x3`).
- **`seedSim`**  (List of Integers):
  - A list of three positive integers used to seed the random number generators.

***Random Number Generation***

PyPRS uses the MRG32k3a_numba package for random number generation. If your simulation requires multiple sources of randomness (e.g., interarrival times and service times in a queueing model), you can initialize multiple instances of MRG32k3a_numba.

What is a "Source of Randomness"?
A source of randomness refers to distinct needs for random numbers in a simulation model. For example, a single-server queueing model might use:

One RNG for interarrival times.
Another RNG for service times.
Initializing Two Instances of MRG32k3a_numba
To handle multiple sources of randomness, you can initialize two instances of MRG32k3a_numba as follows:

python
运行
from MRG32k3a_numba import MRG32k3a_numba

def simulation_function(argsSim, seedSim):
    # Initialize RNG for interarrival times
    rng1 = MRG32k3a_numba(seedSim[0], seedSim[1] + 1, seedSim[2])
    # Initialize RNG for service times
    rng2 = MRG32k3a_numba(seedSim[0], seedSim[1] + 2, seedSim[2])
    
    # Simulation logic using rng1, rng2, and argsSim
    ...
This ensures that each source of randomness uses a unique seed sequence, maintaining reproducibility and independence in the simulation.

🛠️ Summary
To use PyPRS effectively:

Install PyPRS via direct download or PyPI.
Run the GUI to configure and execute procedures.
Set input parameters for your chosen procedure (GSP, KT, PASS, or FBKT).
Upload required files:
A .txt file with alternative parameters.
A .py file defining the simulation_function with proper random number generation.
This setup enables you to solve large-scale R&S problems efficiently using PyPRS.

