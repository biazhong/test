# MRG32k3a_numba Package

The `mrg32k3a_numba` package provides a Python implementation of the MRG32k3a random number generator, designed to be compatible with Numba-accelerated functions. The MRG32k3a, introduced by  L’Ecuyer (1999) and L’Ecuyer et al. (2002)., is a high-quality RNG with an exceptionally long period of approximately $2^{191} and has been rigorously tested for statistical robustness. This implementation builds on the work of Eckman et al. (2023) and addresses the limitation of the original MRG32k3a implementation, which was not compatible with Numba, a just-in-time compiler that optimizes Python code for numerical computations by translating it into machine code.

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
```








