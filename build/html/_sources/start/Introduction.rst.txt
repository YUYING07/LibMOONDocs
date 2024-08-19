============
Introduction
============

``LibMOON`` is a multiobjective optimization framework that spans from single-objective optimization to multiobjective
optimization. It aims to enhance the understanding of optimization problems and facilitate fair comparisons between MOO
algorithms.


Supported Benchmark Datasets
============================

+------------------------------------------------------------------------------------------------------------------------------------+--------------------+---------------------------------------------------------+
| Datasets                                                                                                                           | Problems           | Project/Code                                            |
+====================================================================================================================================+====================+=========================================================+
| `ZDT <https://ieeexplore.ieee.org/document/996017>`_                                                                               | Synthetic          | `Project <https://pymoo.org/problems/multi/zdt.html>`_  |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `DTLZ <https://ieeexplore.ieee.org/document/996017>`_                                                                              |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `MAF <https://link.springer.com/article/10.1007/s40747-017-0039-7>`_                                                               |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+                    +---------------------------------------------------------+
| `WFG <https://ieeexplore.ieee.org/document/996017>`_                                                                               |                    | `Code <https://github.com/ryojitanabe/reproblems>`_     |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `Fi's <https://ieeexplore.ieee.org/document/996017>`_                                                                              |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `RE <https://arxiv.org/abs/2009.12867>`_                                                                                           |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+--------------------+---------------------------------------------------------+
| `MO-MNISTs <https://proceedings.neurips.cc/paper_files/paper/2019/file/685bfde03eb646c27ed565881917c71c-Paper.pdf>`_               | Multitask Learning | `COSMOS <https://github.com/ruchtem/cosmos>`_           |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `Fairness Classification <https://arxiv.org/pdf/2103.13392>`_                                                                      |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+                    |                                                         |
| `Federated Learning <https://proceedings.neurips.cc/paper_files/paper/2023/file/7cb2c2a8d35576c00078b6591ec26a7d-Paper.pdf>`_      |                    |                                                         |
+------------------------------------------------------------------------------------------------------------------------------------+                    +---------------------------------------------------------+
| `Synthetic (DST, FTS...) <https://proceedings.neurips.cc/paper_files/paper/2019/file/4a46fbfca3f1465a27b210f4bdfe6ab3-Paper.pdf>`_ |                    |`Project <https://github.com/sample-repo/envelop-code>`_ |
+------------------------------------------------------------------------------------------------------------------------------------+                    +---------------------------------------------------------+
| `Robotics (MO-MuJoCo...) <https://proceedings.mlr.press/v119/xu20h/xu20h.pdf>`_                                                    |                    |  `Code <https://github.com/mit-gfx/PGMORL>`_            |
+------------------------------------------------------------------------------------------------------------------------------------+--------------------+---------------------------------------------------------+

Supported Algorithms
====================

``LibMOON`` supports the following algorithms:

+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
| Method                                                                                                          | Property                                                               | #Obj                |Support     |Venues       |Complexity           |Arguments          |
+=================================================================================================================+========================================================================+=====================+============+=============+=====================+===================+
+ Aggregation fun. based, e.g. Tche,mTche,LS,PBI,...                                                              | Pareto solution with aggregations.                                     | Any                 |Yes         |Any          |                     |``GradAggSolver``  |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`COSMOS <https://arxiv.org/pdf/2103.13392>`_                                                                     | Approximated exact solution.                                           | Any                 |Yes         |ICDM 2021    |:math:`O(m n K )`    |                   |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`EPO <https://proceedings.mlr.press/v119/mahapatra20a/mahapatra20a.pdf>`_                                        | Exact solution.                                                        | Any                 |Yes         |ICML 2020    |:math:`O(m^2 n K)`   |``EPOSolver``      |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`MO-SVGD <https://openreview.net/pdf?id=S2-j0ZegyrE>`_                                                           | A set of diverse Pareto solution.                                      | Any                 |Yes         |NeurIPS 2021 |:math:`O(m^2 n K^2)` |``MOO-SVGDSolver`` |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`MGDAUB <https://proceedings.neurips.cc/paper/2018/file/432aca3a1e345e339f35a30c8f65edce-Paper.pdf>`_            | Arbitray Pareto solutions. Location affected highly by initialization. | Any                 |Yes         |NeurIPS 2018 |:math:`O(m^2 n K)`   |``MGDAUBSolver``   |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`PMGDA <https://arxiv.org/abs/2402.09492>`_                                                                      | Pareto solutions satisfying any preference.                            | Any                 |Yes         |TETCI        |:math:`O(m^2 n K)`   |``PMGDASolver``    |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`PMTL <https://proceedings.neurips.cc/paper_files/paper/2019/file/685bfde03eb646c27ed565881917c71c-Paper.pdf>`_  | Pareto solutions in sectors.                                           | 2. 3 is difficult.  |Yes         |NeurIPS 2019 |:math:`O(m^2 n K^2)` |``PMTLSolver``     |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+
|`HVGrad <https://arxiv.org/abs/2102.04523>`_                                                                     | It is a gradient-based HV method.                                      | 2/3                 |Yes         |CEC2023      |:math:`O(m^2 n K^2)` |``HVGradSolver``   |
+-----------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+---------------------+------------+-------------+---------------------+-------------------+


Here, :math:`m` is the number of objectives, :math:`K` is the number of samples, and :math:`n` is the number of decision variables.
For neural network based methods, :math:`n` is the number of parameters; hence :math:`n` is very large (>10000), :math:`K` is also large (
e.g., 20-50), while :math:`m` is small (2.g., 2-4).
As a result, :math:`m^2` is not a big problem. :math:`n^2` is a big problem. :math:`K^2` is a big problem.

Time complexity of gradient based methods are as follows,

1. Tier 1. ``GradAggSolver``.
2. Tier 2. ``MGDASolver``, ``EPOSolver``, ``PMTLSolver``.
3. Tier 3. ``GradHVSolver``
4. Tier 4. ``MOOSVGDSolver``

Important things to notice:
The original code ``MOO-SVGD`` does not offer a MTL implement. Our code is the first open source code for MTL ``MOO-SVGD``.


+----------------------------------------------+----------------------------------------------+---------------------------+
|Method                                        |Problems	                              |Arguments                  |
+==============================================+==============================================+===========================+
|                                              |Pareto set learning Solvers                   |``EPO-based PSL``          |
+----------------------------------------------+                                              +---------------------------+
|                                              |                                              |``Agg-based PSL``          |
+----------------------------------------------+                                              +---------------------------+
|                                              |                                              |``PMGDA-based PSL``        |
+----------------------------------------------+                                              +---------------------------+
|                                              |                                              |``Evolutionary-based PSL`` |
+----------------------------------------------+----------------------------------------------+---------------------------+
|                                              |MultiObjective Bayesian Optimization  Solvers |``PSL-MONO``               |
+----------------------------------------------+                                              +---------------------------+
|                                              |                                              |``PSL-DirHV-EI``           |
+----------------------------------------------+                                              +---------------------------+
|                                              |                                              |``DirHV-EGO``              |
+----------------------------------------------+----------------------------------------------+---------------------------+
| `HV Net <https://arxiv.org/abs/2203.02185>`_ |Machine Learning Pretrained                   |                           |
+----------------------------------------------+----------------------------------------------+---------------------------+


Citation
========

If you find ``LibMOON`` useful for your research or development, please cite the following:


.. code-block:: python

    @software{libmoon_2024,
        author = {Zhang, Xiaoyuan and Zhao, Liang and Yu, Yingying and Lin, Xi and Chen, Yifan and Zhao, Han and Zhang, Qingfu},
        title = {{LibMOON: A Gradient-based MultiObjective OptimizatioN Library in PyTorch}},
        url = {https://github.com/xzhang2523/libmoon},
        version = {2.0.4},
        year = {2024}
    }


Contributors
============
``LibMOON`` is developed by the following contributors:

- `Xiaoyuan Zhang <https://scholar.google.com/citations?user=KQj18L8AAAAJ&hl=zh-TW>`_  (Maintainer of Pareto set learning, gradient-based solver)
- `Liang Zhao <https://liazhao5.github.io/>`_  (Maintainer of MOBO)
- `Yingying Yu <https://scholar.google.com/citations?user=nw6-_5wAAAAJ&hl=en>`_  (Software design)
- `Xi Lin <https://xi-l.github.io/>`_  (Software design)

Contact Us
==========

- If you have any question or suggestion, please feel free to contact us by raising an issue or sending an email
  to ``xzhang2523-c@my.cityu.edu.hk``.



Advisory Board
==============

- Prof. `Qingfu Zhang <https://www.cs.cityu.edu.hk/~qzhan7/index.html>`_ (FIEEE, City University of Hong Kong, **Corresponding**)
- Prof. `Han Zhao <https://hanzhaoml.github.io/>`_ (University of Illinois at Urbana-Champaign)
- Prof. `Yifan Chen <https://ychen-stat-ml.github.io/>`_ (Hong Kong Baptist University)
- Prof. `Ke Shang <https://scholar.google.com.hk/citations?user=jFUXL1AAAAAJ&hl=zh-CN>`_ (Shenzhen University)
- Prof. `Genghui Li <https://scholar.google.com/citations?user=3WixDRMAAAAJ&hl=zh-CN>`_ (Shenzhen University)
- Prof. `Zhenkun Wang <https://faculty.sustech.edu.cn/?tagid=wangzk3&iscss=1&snapid=1&orderby=date&go=1&lang=en>`_ (Southern University of Science and Technology)
- Prof. `Tao Qin <https://scholar.google.com/citations?user=Bl4SRU0AAAAJ&hl=zh-CN>`_ (Microsoft Research)



