[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**Output**](Output.md) | [**A Demo Application**](A%20Demo%20Application.md) | [**MRG32k3a_numba**](MRG32k3a_numba.md)

## The Procedure (`.py`) File

Define a function named `custom_procedure`, which implements the computational steps for one run of the custom procedure. The function takes specific input arguments and returns a dictionary with required output keys.

**Prerequisites**
Before creating the `custom_procedure` function, ensure the following:
- The **alternatives information file** (**`.txt`** file) is created.
- The **simulation function file** (**`.py`** file) is created.
- **Input parameters** are specified in the GUI, including their names and values.

**Arguments**
- **`alternatives`**: A list of SampleGen class instances.
  - Each instance corresponds to an alternative listed in the **alternatives information file** (**`.txt`** file).
  - The ``SampleGenerate`` class provides methods to:
    - Generate simulation samples for the alternative.
    - Access and modify details associated with the alternative.
    - For more details about this class, please go to <a href="SampleGenerate Class.md">SampleGenerate Class</a>.
- **`configs`**: A dictionary containing input parameters.
  - Keys are parameter names, and values are the corresponding values specified in the GUI.
- **`replication`**: An integer that records the number of times the procedure has been applied to solve the problem.
  - Useful for managing random number seeds or implementing Common Random Numbers.

**Return**
The function must return a dictionary with the following five keys:
- **best alternative args**: Parameter information for the selected best alternative (format depends on the problem).
- **simulation time**: Total simulation time used (in appropriate units, e.g., seconds).
- **wall-clock time**: Real-world time elapsed during the procedure (in seconds).
- **total budget**: Total number of samples generated during the procedure.
- **utilization**: A measure of processor efficiency in parallel computing, calculated as:  $\text{utilization}=\text{total simulation time}/(\text{number of processors
}\times \text{wall-clock time})$.






<a href="How to Use PyPRS.md">Back to How to Use PyPRS</a>
