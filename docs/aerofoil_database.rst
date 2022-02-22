.. _aerofoil_database:

===========================
Defining aerofoil databases
===========================

Here is an example of how to save aerofoil data into the `npz` file format
expected by :class:`bemused.AerofoilDatabase`. Of course, you can load the data
from another source rather than embedding directly in a Python script.

.. code-block:: python

   import numpy as np

   adata = {}

   # Add data for different thicknesses. For example, 100% thickness is easy...
   # The three columns are Cl, Cd and Cm

   adata[100] = """
   -180.00	0.000	0.500	0.000
   0.00	0.000	0.500	0.000
   180.00	0.000	0.500	0.000
   """

   # Add other data for other thicknesses...

   def parseData(s):
       a = np.array([tuple(map(float, row.split('\t'))) for row in s.strip().split('\n')],
                    dtype=[('alpha', float), ('CL', float), ('CD', float), ('CM', float)])
       a['alpha'] *= pi/180
       return a

   parsed_adata = {k: parseData(v) for k, v in adata.items()}

   # Save the aerofoil data
   keys = sorted(parsed_adata.keys())
   np.savez('aerofoils.npz',
            thicknesses=[float(k) / 100  for k in keys],
            datasets   =[parsed_adata[k] for k in keys])
