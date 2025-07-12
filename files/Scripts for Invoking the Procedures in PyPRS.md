[**Main Page**](../README.md) | [**How to Use PyPRS**](How%20to%20Use%20PyPRS.md) | [**Output**](Output.md) | [**A Demo Application**](A%20Demo%20Application.md) | [**MRG32k3a_numba**](MRG32k3a_numba.md)
## 📋 Scripts for Invoking GSP
```python
  from PyPRS.procedure import Procedure
	
  gsp_procedure = Procedure("GSP")
  gsp_procedure.set_CRNs() #Disable CRNs by commenting out this line

  gsp_config = {
	  "n0": <value>, # (int)
	  "n1": <value>, # (int)
	  "r_bar": <value>, # (int)
	  "beta": <value>, # (int)
	  "alpha1": <value>, # (float)
	  "alpha2": <value>, # (float)
	  "delta": <value>, # (float)
	  "Number of Processors": <value>, # (int)
	  "Repeat": <value>, # (int)
	  "Reference Seed": <value>, # (list[int, int, int])
	  "Alternatives Information File": "<path/to/file.txt>", # (str)
	  "Simulation Function File": "<path/to/file.py>" # (str)
  }	
  gsp_result = gsp_procedure.run_procedure(gsp_config) 
  # A list of dictionaries that record the final results.
```


<a href="How to Use PyPRS.md">Back to How to Use PyPRS</a>

