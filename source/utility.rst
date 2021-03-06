=================
Utility
=================

[github] https://github.com/Tomoki-YAMASHITA/CrySPY/tree/master/utility

.. contents:: Contents


.. index::
   single: cryspy_analyzer_RS.ipynb

cryspy_analyzer_RS.ipynb
==========================

[github] https://github.com/Tomoki-YAMASHITA/CrySPY/blob/master/utility/cryspy_analyzer_RS.ipynb

Jupyter Notebook to visualize results for Random Search.


.. index::
   single: cryspy_analyzer_BO.ipynb

cryspy_analyzer_BO.ipynb
==========================

[github] https://github.com/Tomoki-YAMASHITA/CrySPY/blob/master/utility/cryspy_analyzer_BO.ipynb

Jupyter Notebook to visualize results for Bayesian Optimization.


.. index::
   single: cryspy_analyzer_LAQA.ipynb

cryspy_analyzer_LAQA.ipynb
==========================

[github] https://github.com/Tomoki-YAMASHITA/CrySPY/blob/master/utility/cryspy_analyzer_LAQA.ipynb

Jupyter Notebook to visualize results for LAQA.


.. index::
   single: pkl_data.ipynb

pkl_data.ipynb
================

[github] https://github.com/Tomoki-YAMASHITA/CrySPY/blob/master/utility/pkl_data.ipynb

Jupyter Notebook to analyze pickled data in CrySPY.



.. index::
   single: kpt_check.py

kpt_check.py
===============
kpt_check.py can check a k-point mesh with a given ``kppvol``. In this script, ``POSCAR``, ``CONTCAR``, and ``init_struc_data.pkl`` are readable.

For example, check a k-point mesh with kppvol = 100 for a POSCAR file.

.. code-block:: bash

   $ python kpt_check.py POSCAR 100
   a = 10.689217
   b = 10.689217
   c = 10.730846
       Lattice vector
   10.689217 0.000000 0.000000
   0.000000 10.689217 0.000000
   0.000000 0.000000 10.730846

   kppvol:  100
   k-points:  [2, 2, 2]

You can write a ``KPOINTS`` file with ``-w`` or ``--write`` option for VASP.

.. code-block:: bash

   $ python kpt_check.py -w POSCAR 100
   $ cat KPOINTS
   pymatgen 4.7.6+ generated KPOINTS with grid density = 607 / atom
   0
   Monkhorst
   2 2 2

In checking k-point meshes for init_struc_data.pkl, first five structures in init_struc_data.pkl are automatically checked in the default setting. You can change the number of structures using ``-n`` or ``--nstruc`` option.

.. code-block:: bash

   $ python kpt_check.py -n 3 init_struc_data.pkl 100


   # ---------- 0th structure
   a = 8.0343076893
   b = 8.03430768936
   c = 9.1723323373
       Lattice vector
   8.034308 0.000000 0.000000
   -4.017154 6.957915 0.000000
   0.000000 0.000000 9.172332

   kppvol:  100
   k-points:  [3, 3, 3]


   # ---------- 1th structure
   a = 9.8451944096
   b = 9.84519440959
   c = 6.8764313585
       Lattice vector
   9.845194 0.000000 0.000000
   -4.922597 8.526188 0.000000
   0.000000 0.000000 6.876431

   kppvol:  100
   k-points:  [3, 3, 4]


   # ---------- 2th structure
   a = 7.5760383679
   b = 7.57603836797
   c = 6.6507478296
       Lattice vector
   7.576038 0.000000 0.000000
   -3.788019 6.561042 0.000000
   0.000000 0.000000 6.650748

   kppvol:  100
   k-points:  [4, 4, 4]


.. index::
   single: struc2cif.py

struc2cif.py
===================
struc2cif.py can covert a structure file to a cif file using pymatgen. You can specify various formats. A (input file name + '.cif') file is generated.

.. seealso::
   `pymatgen <http://pymatgen.org/>`_

.. code-block:: bash

   $ python struc2cif.py POSCAR

You can change a tolerance value for checking the space group with ``-t`` or ``--tolerance`` option (default value is 0.1).

.. code-block:: bash

   $ python struc2cif.py -t 0.001 POSCAR
