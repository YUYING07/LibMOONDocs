================
libmoon.solver
================

GradBaseSolver
==============

.. py:class:: GradBaseSolver

    Base: ``object``

    All gradient solvers should implement the methods in the base class ``GradBaseSolver``

    .. py:method:: __init__(self, step_size, n_iter, tol)

        :param int step_size: The step size for updating directions.
        :param int n_iter: Maximal iterations.
        :param float tol: Stop when the norm of gradients is less than the value of tol.

    .. py:method:: solve(self, x, prefs)

        :param ndarray (K, n) x: The initial solution.
        :param ndarray (K, m) prefs: The preference matrix.

.. py:class:: GradAggSolver

    Base: ``GradBaseSolver``

    .. py:method:: __init__(self, problem, step_size, n_iter, tol, agg_fun)

        :param str problem: Existing problems or the given n_obj.
        :param str agg_fun: agg_fun from ls, mtche, tche, pbi, cosmos, invagg, softtche, softmtche

    .. py:method:: solve(self, x, prefs)


.. py:class::  EPOSolver

    Base: ``GradBaseSolver``

    EPOSolver, published in:

    1. `"Multi-Task Learning with User Preferences: Gradient Descent with Controlled Ascent in Pareto Optimization" <https://proceedings.mlr.press/v119/mahapatra20a.html>`_
    2. `"Controllable Pareto Multi-Task Learning" <https://arxiv.org/abs/2010.06313>`_

    .. py:method:: solve(self, x, prefs)


.. py:class::  MOO-SVGDSolver

    Base: ``GradBaseSolver``

    MOO-SVGDSolver, published in:
    `"Profiling Pareto Front With Multi-Objective Stein Variational Gradient Descent" <https://openreview.net/pdf?id=S2-j0ZegyrE>`_

    .. py:method:: solve(self, x, prefs, problem, n_prob, n_obj)

        :param int n_obj: The number of objectives.
        :param float n_prob: The number of problems.


.. py:class::  MGDAUBSolver

    Base: ``GradBaseSolver``

    MGDAUBSolver, published in:

    1. `"Multiple-gradient descent algorithm (MGDA) for multiobjective optimizationAlgorithme de descente à gradients multiples pour lʼoptimisation multiobjectif" <https://www.sciencedirect.com/science/article/pii/S1631073X12000738>`_
    2. `"Multi-task learning as multimnist-objective optimization." <https://arxiv.org/abs/1810.04650>`_

    .. py:method:: solve(self, x, prefs, problem, n_prob, n_obj)


.. py:class::  PMGDASolver

    Base: ``GradBaseSolver``

    PMGDASolver, published in:

    `"PMGDA: A Preference-based Multiple Gradient Descent Algorithm." <https://arxiv.org/abs/2402.09492>`_

    .. py:method:: solve(self, x, prefs)

.. py:class::  PMTLSolver

    Base: ``GradBaseSolver``

    .. py:method:: solve(self, x, prefs, problem, n_prob, n_obj)

.. py:class::  HVGradSolver

    Base: ``GradBaseSolver``

    .. py:method:: solve(self, x, prefs, problem, n_prob, n_obj)


SimplePSLSolver
===============

.. py:class:: SimplePSLSolver

    Base: ``object``

    All pareto set learning solvers should implement the methods in the base class ``SimplePSLSolver``

    .. py:method:: __init__(self, n_obj, n_var, lr=1e-3)

        :param int n_obj: Number of objectives.
        :param int n_var: Number of variables.
        :param float lr: Learning rate. Default is ``1e-3``.

    .. py:method:: forward(self, prefs)

        :param ndarray (n_prob, n_obj) prefs: The preference matrix.
        :return: The ``solution`` matrix of shape ``(n_prob, n_var)``.

    .. py:method:: optimize(self, problem, epoch)

        :param ProblemClass problem: The problem class instance to optimize.
        :param int epoch: Number of epochs for optimization.

    .. py:method:: evaluate(self, prefs)

            :param ndarray (n_prob, n_obj) prefs: The preference matrix.
            :return: The ``decision_variables`` matrix of shape ``(n_prob, n_var)``.

.. py:class:: SimplePSLLoRAModel

        Base: ``SimplePSLModel``


