[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**A Demo Application**](A%20Demo%20Application.md)


# MRG32k3a_numba Package

The `mrg32k3a_numba` package provides a Python implementation of the MRG32k3a random number generator, designed to be compatible with Numba-accelerated functions. The MRG32k3a, introduced by  L’Ecuyer (1999) and L’Ecuyer et al. (2002)., is a high-quality RNG with an exceptionally long period of approximately $2^{191}$ and has been rigorously tested for statistical robustness. This implementation builds on the work of Eckman et al. (2023) and addresses the limitation of the original MRG32k3a implementation, which was not compatible with Numba, a just-in-time compiler that optimizes Python code for numerical computations by translating it into machine code.

The period of the MRG32k3a random number generator is structured hierarchically:
- **Streams**: $2^{50}$ streams, each with a length of $2^{141}$.
- **Substreams**: Each stream contains $2^{47}$ substreams, each with a length of $2^{94}$.
- **Subsubstreams**: Each substream contains $2^{47}$ subsubstreams, each with a length of $2^{47}$.

# Installation
To install the `mrg32k3a_numba` package, run the following command in your terminal or command prompt:
```bash
python -m pip install mrg32k3a_numba
```
# Initializing an Instance
To use the random number generator, create an instance of the `MRG32k3a_numba` class and seed it with a list of three positive integers [s, ss, sss], where:
- `s`: The index of the stream.
- `ss`: The index of the substream within the chosen stream.
- `sss`: The index of the subsubstream within the chosen substream.

# Example Usage
Below is an example of how to initialize an instance of the `MRG32k3a_numba` class and generate random numbers:
```python
from mrg32k3a_numba import MRG32k3a_numba
# Initialize the RNG with stream=0, substream=1, subsubstream=2
rng = MRG32k3a_numba(seed=[0, 1, 2])

# Generate a single random number (uniformly distributed in [0, 1))
random_number = rng.random()
print(f"Random number: {random_number}")
```

# Key Methods
The `MRG32k3a_numba` class provides the following key methods:



# References
- Eckman DJ, Henderson SG, Shashaani S (2023) SimOpt: A testbed for simulation-optimization experiments. INFORMS Journal on Computing 35(2):495–508.
- L’Ecuyer P (1999) Good parameters and implementations for combined multiple recursive random number generators. Operations Research 47(1):159–164.
- L’Ecuyer P, Simard R, Chen EJ, Kelton WD (2002) An object-oriented random-number package with many long streams and substreams. Operations Research 50(6):1073–1075.


<a href="Uploading Files.md">Back to the Uploading Files page</a>



