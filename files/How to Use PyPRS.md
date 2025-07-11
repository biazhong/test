[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**A Demo Application**](A%20Demo%20Application.md)
# ⚙️ How to Use PyPRS
This section provides instructions for running PyPRS on a **single computer** and a **cluster**.

## 1. 🖥️ Running PyPRS on a Single Computer
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
Each procedure requires specific input parameters.  For detailed explanations of the input parameters for each procedure, please visit the <a href="./Input Parameters.md">Input Parameters</a> page.

#### 2) Uploading Required Files
In addition to configuring parameters, users must upload two files: one is the alternatives infromation file (a `.txt` file) and the other one is the simulation function file (a `.py`file). For detailed discussions about these two files, please visit the <a href="./Uploading Files.md">Uploading Files</a> page.



### 1.2 Setting Up a Custom Procedure

## 2. 🌐 Running PyPRS on a Cluster
