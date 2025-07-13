| [**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**Output**](Output.md) | [**A Demo Application**](A%20Demo%20Application.md) |
# The Throughput Maximization Problem

## 1 📝 Problem Description
The throughput maximization problem considers a flow line system with three stations, labeled as Stations 1, 2, and 3. There are infinitely many jobs waiting in front of Station 1, and each job moves sequentially through all three stations. The service times at Stations 1, 2, and 3 are independently drawn from exponential distributions with service rates $s_1$, $s_2$, and $s_3$ respectively. At Stations 2 and 3, there is finite buffer storage, denoted as $b_2$ and $b_3$ respectively. When the buffer at Station $i$, where $i = 2, 3$, is fully occupied, Station $i - 1$ is blocked and must hold the completed job until the job at Station $i$ is finished and released. The objective of this problem is to determine the optimal allocation of the service rate and the buffer to maximize the expected steady-state throughput of the flow line subject to constraints $s_1 + s_2 + s_3 = \mathcal{L}_1$,  $b_2 + b_3 = \mathcal{L}_2$, and $x=(s_1,s_2,s_3,b_2,b_3)\in Z$. Here, $\mathcal{L}_1$ and $\mathcal{L}_2$ represent problem-specific parameters that define the feasible solution set. The mathematical formulation of this problem is as follows:

<p align="center">$\max_{x} \mathbb{E}[f(x; \xi)]$</p>
<p align="center">$\text{s.t.} \quad s_1 + s_2 + s_3 = \mathcal{L}_1$</p>
<p align="center">$\quad\quad b_2 + b_3 = \mathcal{L}_2 $</p>
<p align="center">$\quad\quad\quad  x=(s_1,s_2,s_3,b_2,b_3)\in Z$,</p>

where $f(x; \xi)$ is the random throughput of the flow line. For every feasible solution, we obtain observations of $f(x; \xi)$ by running simulation experiments. For each simulation experiment, we warm up the system with 2,000 jobs. After 2,000 jobs are processed, we observe the throughput of the subsequent 50 jobs. In this demonstration, we let $\mathcal{L}_1=50$ and $\mathcal{L}_2=50$ resulting in 57,624 alternatives available in the problem. 

## 2 🔧 Using PyPRS to Solve the Problem

In this demo application, all the built-in procedures and a custom procedure, namely the equal allocation procedure, are applied to solve the throughput maximization problem.  To use PyPRS, users need the **alternatives information file** and **simulation function file**. Download these files directly by clicking the following link:

<a href="https://raw.githubusercontent.com/biazhong/test/refs/heads/main/files/Uploading%20Files.zip">Download Uploading Files</a>

### GSP
### The KT Procedure
### The PASS Procedure
### The FBKT Procedure
### The Custom Procedure
