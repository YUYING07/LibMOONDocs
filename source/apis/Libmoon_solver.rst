================
libmoon.solver
================


.. py:class:: GradBaseSolver

    Base: object

    All gradient solvers should implement the methods in the base class ``GradBaseSolver``

    .. py:method:: __init__(self, step_size, n_iter, tol)

        :param int step_size: The step size for updating directions.
        :param int n_iter: Maximal iterations.
        :param float tol: Stop when the norm of gradients is less than the value of tol.

    .. py:method:: solve(self, x, prefs)

        :param ndarray (K, n) x: The initial solution.
        :param ndarray (K, m) prefs: The preference matrix.
