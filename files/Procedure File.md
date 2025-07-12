[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**Output**](Output.md) | [**A Demo Application**](A%20Demo%20Application.md) | [**MRG32k3a_numba**](MRG32k3a_numba.md)

## The Procedure (`.py`) File

Defines a function named `custom_procedure`, which implements the computational steps for one run of the custom procedure. The function takes specific input arguments and returns a dictionary with required output keys. 

**Prerequisites**

Before creating the `custom_procedure` function, ensure the following:
- The **alternatives information file** (**`.txt`** file) is created.
- The **simulation function file** (**`.py`** file) is created.
- **Input parameters** are specified in the GUI, including their names and values.

**Arguments**
- **`alternatives`**: A list of `SampleGenerate` class instances.
  - Each instance corresponds to an alternative specified in the **alternatives information file** (**`.txt`** file).
  - The `SampleGenerate` class provides methods to manage simulations and alternative details, including:
    - `alternatives[i].get_args()`: Retrieves the alternative's parameter information.
    - `alternatives[i].set_seed(seed)`: Sets the random number seed for the alternative's next simulation run.
    - `alternatives[i].get_seed()`: Retrieves the random number seed for the alternative's next simulation run.
    - `alternatives[i].run_simulation()`: Executes the `simulation_function`, passing the values of `alternatives[i].get_args()` to `argsSim` and `alternatives[i].get_seed()` to `seedSim`， and returns the simulation output as a float.
- **`configs`**: A dictionary containing input parameters.
  - Keys are parameter names, and values are the corresponding values specified in the GUI.
- **`replication`**: An integer that records the number of times the procedure has been applied to solve the problem.
  - Useful for managing random number seeds or implementing Common Random Numbers.
 
**Selection Process**

Based on the information provided in the arguments, users must implement a custom selection process, which includes defining how the procedure leverages Ray for parallelization. For guidance on programming and using Ray, refer to the <a href="https://docs.ray.io/en/latest/index.html">official Ray website</a>.



**Return**

The function must return a dictionary with the following five keys:
- **best alternative args**: Parameter information for the selected best alternative (format depends on the problem).
- **simulation time**: Total simulation time used (in appropriate units, e.g., seconds).
- **wall-clock time**: Real-world time elapsed during the procedure (in seconds).
- **total budget**: Total number of samples generated during the procedure.
- **utilization**: A measure of processor efficiency in parallel computing, calculated as:  utilization = total simulation time / (number of processors * wall-clock time).

**Function Template**
```python
def custom_procedure(alternatives, configs, replication):
    # Extract input parameter information from configs
    param1 = configs.get('Repeat')
    param2 = configs.get('Number of Processors')
    # Extract more as needed...

    # Custom designed selection process
    
    return {
        'best alternative args': ...,
        'simulation time': ...,
        'wall-clock time': ...,
        'total budget': ...,
        'utilization': ...
    }
```




<a href="How to Use PyPRS.md">Back to How to Use PyPRS</a>
