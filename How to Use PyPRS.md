<a href="./README.md">Back to the main page</>
# ⚙️ How to Use PyPRS
This section provides instructions for running PyPRS on a **single computer** and a **cluster**.

## 1. 🖥️ Running PyPRS on a Single Computer
To run PyPRS on a single computer, users just need to execute the `GUI.py` file located in the `UserInterface` package in a Python environment:
```bash
python GUI.py
```
Once the file is executed, the **Graphical User Interface (GUI)** will launch. In the GUI, users can **select a procedure**, **configure input parameters**, **upload required files**, and **run the procedure**.

<!--- Below is a screenshot of the GUI:

  <img width="379.52" height="396.8" alt="image" src="https://github.com/user-attachments/assets/11314524-ebef-4662-b1dc-4b184b50c0db" />--->

### 1.1 Setting Up a Built-in Procedure
To use a built-in procedure (e.g., GSP, KT, PASS, or FBKT), follow these steps:

#### 1) Configuring Input Parameters
Each procedure requires specific input parameters.  For detailed explanations of the input parameters for each procedure, please visit the <a href="./Input Parameters.md">Input Parameters.md</a> file.

#### 2) Uploading Required Files
In addition to configuring parameters, users must upload two files:

#### 📄 i. The `.txt` File
Defines parameter information for each alternative.
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

#### 🐍 ii. The `.py` File
Defines a Python function named `simulation_function`, which is responsible for generating a **simulation sample** from a given alternative using specific random number sequences.

*Arguments*
- **`argsSim`** (List of Floats):
  - Contains the parameter information of the alternative.
  - Format matches the `.txt` file:
    - `argsSim[0]`: Index of the alternative.
    - `argsSim[1]`, `argsSim[1]`, etc: Parameter values (e.g., `x1`, `x2`, `x3`).
- **`seedSim`**  (List of Integers):
  - A list of three positive integers used to seed the random number generators.

*Random Number Generation*

PyPRS uses the `MRG32k3a_numba` package for random number generation. (For more details about the `MRG32k3a_numba` package, please visit the <a href="./MRG32k3a_numba.md">MRG32k3a_numba</a> page.) If the simulation process requires multiple sources of randomness (e.g., interarrival times and service times in a queueing model), users can initialize multiple instances of `MRG32k3a_numba`. A source of randomness refers to distinct needs for random numbers in a simulation model. For example, a simple single-server queueing model might designate two such sources of randomness: one for interarrival times and one for service times.

In the simulation_function, whenever instances of `MRG32k3a_numba` are initialized, proper seeding is required. For example, when two independent sources of randomness are needed within the `simulation_function`, the seedSim parameter can be used to seed the instances as follows:

 - The first instance is seeded using `[seedSim[0], seedSim[1]+1, seedSim[2]]`.
 - The second instance is seeded using `[seedSim[0], seedSim[1]+2, seedSim[2]]`.

*Numba Optimization*

PyPRS allows users to apply the `numba` decorator to optimize the `simulation_function` for faster execution. For more details about this technique, please visit the official <a href="https://numba.pydata.org/">Numba site</a>

*Return*

The output of the function should be a float that records the output for one run of the simulation model.

*Function Template*
```python
from mrg32k3a_numba import MRG32k3a_numba
import numba

# Apply the @numba.njit decorator for better performance
@numba.njit
def simulation_function(argsSim, seedSim) -> float:
    # Extract alternative's parameter information from argsSim
    idx= argsSim[0]  # Index
    x1 = argsSim[1]  # Parameter 1
    x2 = argsSim[2]  # Parameter 2
    x3 = argsSim[3]  # Parameter 3
    # Extract more as needed...

    # Initialize random number generators based on seedSim
    rng1 = MRG32k3a_numba(seedSim[0], seedSim[1] + 1, seedSim[2]) # First random number generator
    rng2 = MRG32k3a_numba(seedSim[0], seedSim[1] + 2, seedSim[2]) # Second random number generator
    # Add more random number generators as needed...

    # Users can replace the following lines with their own custom simulation logic
    random_val_1 = rng1.random() # Get a random value from rng1
    random_val_2 = rng2.random() # Get a random value from rng2
    result = (x1 * random_val_1 + x2 * random_val_2) / x3 # Example calculation

    # Return the result as a float
    return float(result)
```

### 1.2 Setting Up a Custom Procedure

## 2. 🌐 Running PyPRS on a Cluster
