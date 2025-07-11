[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**A Demo Application**](A%20Demo%20Application.md) | [**MRG32k3a_numba**](MRG32k3a_numba.md)


# MRG32k3a_numba Package

The `mrg32k3a_numba` package provides a Python implementation of the MRG32k3a random number generator, designed to be compatible with Numba-accelerated functions. The MRG32k3a, introduced by  L’Ecuyer (1999) and L’Ecuyer et al. (2002)., is a high-quality random number generator with an exceptionally long period of approximately $2^{191}$ and has been rigorously tested for statistical robustness. This implementation builds on the work of Eckman et al. (2023) and addresses the limitation of the original MRG32k3a implementation, which was not compatible with Numba, a just-in-time compiler that optimizes Python code for numerical computations by translating it into machine code.

The period of the MRG32k3a random number generator is structured hierarchically:
- **Streams**: $2^{50}$ streams, each with a length of $2^{141}$.
- **Substreams**: Each stream contains $2^{47}$ substreams, each with a length of $2^{94}$.
- **Subsubstreams**: Each substream contains $2^{47}$ subsubstreams, each with a length of $2^{47}$.

# Installation
To install the `mrg32k3a_numba` package, run the following command in the terminal or command prompt:
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
import numpy as np
from mrg32k3a_numba import MRG32k3a_numba
# Initialize the RNG with stream=0, substream=1, subsubstream=2
rng = MRG32k3a_numba(np.array([0, 1, 2]))

# Generate a single random number (uniformly distributed in (0,1)
random_number = rng.random()
print(f"Random Number: {random_number}")
# Example Output: Random Number: 0.17526146151460337

uniform_number = rng.uniform(10.0, 20.0)
print(f"Uniform Distribution on [10, 20): {uniform_number}")
# Example Output: Uniform Distribution on [10, 20): 17.243388997536364

normal_variate = rng.normalvariate(0.0, 1.0)
print(f"Normal Distribution (mean=0.0, std_dev=1.0): {normal_variate}")
# Example Output: Normal Distribution (mean=0.0, std_dev=1.0): -0.32298573768826494

expo_variate = rng.expovariate(0.5)
print(f"Exponential Distribution (lambda=0.5): {expo_variate}")
# Example Output: Exponential Distribution (lambda=0.5): 1.3471538273911559

lognormal_variate = rng.lognormalvariate(0.0, 0.25)
print(f"Lognormal Distribution (underlying mean=0.0, underlying std_dev=0.25): {lognormal_variate}")
# Example Output: Lognormal Distribution (underlying mean=0.0, underlying std_dev=0.25): 1.2975791204572622

triangular_variate = rng.triangular(100.0, 200.0, 160.0)
print(f"Triangular Distribution (range=[100.0, 200.0], mode=160.0): {triangular_variate}")
# Example Output: Triangular Distribution (range=[100.0, 200.0], mode=160.0): 135.3251178752223

gamma_variate = rng.gammavariate(9.0, 2.0)
print(f"Gamma Distribution (shape α=9.0, scale β=2.0): {gamma_variate}")
# Example Output: Gamma Distribution (shape α=9.0, scale β=2.0): 24.983786084540256

beta_variate = rng.betavariate(5.0, 10.0)
print(f"Beta Distribution (α=5.0, β=10.0): {beta_variate}")
# Example Output: Beta Distribution (α=5.0, β=10.0): 0.4138795474882314

weibull_variate = rng.weibullvariate(1.0, 1.5)
print(f"Weibull Distribution (scale α=1.0, shape β=1.5): {weibull_variate}")
# Example Output: Weibull Distribution (scale α=1.0, shape β=1.5): 1.1890835026462618

pareto_variate = rng.paretovariate(2.5)
print(f"Pareto Distribution (shape α={2.5}): {pareto_variate}")
# Example Output: Pareto Distribution (shape α=2.5): 1.6104763097737471

poisson_variate = rng.poissonvariate(3.5)
print(f"Poisson Distribution (expected λ=3.5): {poisson_variate}")
# Example Output: Poisson Distribution (expected λ=10.0): 3

gumbel_variate = rng.gumbelvariate(0.5, 2.0)
print(f"Gumbel Distribution (location μ=0.5, scale β=2.0): {gumbel_variate}")
# Example Output: Gumbel Distribution (location μ=0.5, scale β=2.0): 3.7308608595873745

binomial_variate = rng.binomialvariate(100, 0.25)
print(f"Binomial Distribution (trials n=100, probability p=0.25): {binomial_variate}")
# Example Output: Binomial Distribution (trials n=100, probability p=0.25): 36

mean_vector = np.array([0.0, 5.0])
covariance_matrix = np.array([[1.0, 0.4], [0.4, 1.0]])
mvnormal_vector = rng.mvnormalvariate(mean_vector, covariance_matrix)
print(f"Multivariate Normal Vector (mean={mean_vector}, covariance=\n{covariance_matrix}): \n{mvnormal_vector}")
# Example Output:
# Multivariate Normal Vector (mean=[0. 5.], covariance=
# [[1.  0.8]
#  [0.8 1. ]]):
# [0.28548717 5.8516565]

rng = MRG32k3a_numba(np.array([0, 1, 2]))
simplex_vec_exact = rng.continuous_random_vector_from_simplex(4, 100.0, True)
print(f"Random Vector from Simplex (elements=4, exact sum=100.0):")
print(simplex_vec_exact)
print(f"Actual sum: {np.sum(simplex_vec_exact)}")
# Example Output:
# Random Vector from Simplex (elements=4, exact sum=100.0):
# [ 7.3792011  37.47239331 43.14995325 11.99845234]
# Actual sum: 100.0
```

# Key Methods
The `MRG32k3a_numba` class provides the following key methods:



# References
- Eckman DJ, Henderson SG, Shashaani S (2023) SimOpt: A testbed for simulation-optimization experiments. INFORMS Journal on Computing 35(2):495–508.
- L’Ecuyer P (1999) Good parameters and implementations for combined multiple recursive random number generators. Operations Research 47(1):159–164.
- L’Ecuyer P, Simard R, Chen EJ, Kelton WD (2002) An object-oriented random-number package with many long streams and substreams. Operations Research 50(6):1073–1075.


<a href="Uploading Files.md">Back to the Uploading Files page</a>



