[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**Output**](Output.md) | [**A Demo Application**](A%20Demo%20Application.md) | [**MRG32k3a_numba**](MRG32k3a_numba.md)
# ⚙️ How to Use PyPRS
This section provides instructions for running PyPRS on a **single computer** and a **cluster**.

## 1 🖥️ Running PyPRS on a Single Computer
To run PyPRS on a single computer, users just need to execute the `GUI.py` file located in the `UserInterface` package in a Python environment:
```bash
python GUI.py
```
Once the file is executed, the **Graphical User Interface (GUI)** will launch. In the GUI, users can:
- **select a procedure**
- **configure input parameters**
- **upload required files**
- **run the procedure**

Below is a screenshot of the GUI:

  <img width="379.52" height="396.8" alt="image" src="https://github.com/user-attachments/assets/11314524-ebef-4662-b1dc-4b184b50c0db" />

### 1.1 Setting Up a Built-in Procedure
To use a built-in procedure (e.g., GSP, KT, PASS, or FBKT), follow these steps:

#### 1) Configuring Input Parameters
Each procedure requires specific input parameters.  For detailed explanations of the input parameters for each procedure, please go to <a href="./Input Parameters.md">Input Parameters</a>.

#### 2) Uploading Required Files
In addition to configuring parameters, users must upload two files: one is the **alternatives infromation file** (a **`.txt`** file) and the other one is the **simulation function file** (a **`.py`** file). For detailed discussions about these two files, please go to <a href="./Uploading Files.md">Uploading Files</a>.



### 1.2 Setting Up a Custom Procedure
To use a custom procedure, follow these steps:

#### 1) Configuring Input Parameters
Below is a screenshot of the GUI for the custom procedure:

  <img width="379.52" height="396.8" alt="image" src="https://github.com/user-attachments/assets/2a3ab001-4d6a-4873-bb6a-90c63e7696a4" />


When configuring a custom procedure, there are two default input parameters that need to be set:

- **`Number of Processors`**: Number of processors used to run the procedure.
- **`Repeat`**: Number of times the problem is repeatedly solved.

In addition to these two default input parameters, users can define other custom input parameters based on their procedure's requirements.

#### 2) Uploading Required Files

When using a custom procedure, users also need to upload the **alternatives infromation file** and the **simulation function file**. Besides these two files, users must upload the **procedure file** (a **`.py`** file). For detailed discussions about the file, please go to <a href="./Procedure File.md">Procedure File</a>.
## 2 🌐 Running PyPRS on a Cluster
