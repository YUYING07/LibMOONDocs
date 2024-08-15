============================================
What is Multi-Objective Optimization?
============================================
Multi-Objective Optimization (MOO) involves minimizing multiple objective functions :math:`(f_1(x), \ldots, f_m(x))`
simultaneously over a decision variable :math:`x`. Typically, no single solution optimizes all objectives;
instead, a set of Pareto optimal solutions exists, representing trade-offs where improving one objective worsens another.
As shown in :numref:`fig-main` , these solutions under function :math:`f` forms the Pareto front (PF).

.. _fig-main:
.. figure:: ../img/moo.png
    :figwidth: 250px
    :align: left
    :figclass: Fig1

    A Pareto front example for a bi-objective optimization problem.


Traditionally, MOO is combined with evolutionary algorithms, known as Multi-Objective Evolutionary Algorithms (MOEAs), which have over 30 years of research [#f1]_ [#f8]_.
Notable algorithms include NSGAs [#f2]_, and MOEA/D [#f3]_. Popular MOEA libraries include PlatEMO [#f4]_, Pymoo [#f5]_, EvoX [#f6]_, and Pagmo [#f7]_.
However, MOEAs are typically limited to problems with small decision variable dimensions, making them challenging to scale for large-scale machine learning tasks.


``LibMOON`` is a gradient-based multi-objective optimization library built on PyTorch. It provides access to gradients of objective functions, :math:`(\nabla f_1(x), \ldots, \nabla f_m(x))`, or estimates them using zero-order methods.
By leveraging gradient information, ``LibMOON`` effectively supports large-scale machine learning tasks.

References
==========
.. [#f1] Zhou et al. Multiobjective evolutionary algorithms: A survey of the state of the art. Swarm and evolutionary computation. 2011.
.. [#f2] Deb et al. A fast and elitist multiobjective genetic algorithm: NSGA-II. TEVC. 2002.
.. [#f3] Zhang et al. MOEA/D: A Multiobjective Evolutionary Algorithm Based on Decomposition. TEVC. 2007.
.. [#f4] Tian et al. PlatEMO: A MATLAB Platform for Evolutionary Multi-Objective Optimization. IEEE Computational Intelligence Magazine. 2017.
.. [#f5] J. Blank and K. Deb, pymoo: Multi-Objective Optimization in Python. IEEE Access. 2020.
.. [#f6] EvoX: A Distributed GPU-accelerated Framework for Scalable Evolutionary Computation. TEVC 2024.
.. [#f7] Biscani et al. A parallel global multiobjective framework for optimization: pagmo. The Journal of Open Source Software. 2020.
.. [#f8] Li et al. A Survey of Decomposition-Based Evolutionary Multi-Objective Optimization. IEEE Access. 2020.