=========================
Customize an Architecture
=========================


This guide will show you how to add a new method to find a set of Pareto solutions.

As we have mentioned in the main paper, specific multiobjective optimization can be written in the form of:

.. math::
        \begin{equation}
        \tilde{g}(L(\theta)) = \sum_{i=1}^m \tilde{\alpha}_i \cdot L_i(\theta).
        \end{equation}

Here, the difference for different methods is how to calculate the coefficients :math:`\tilde{\alpha}_i`.

We firstly provide an example of using random weights ( by set the ``get_weight_func()`` function ), and use initial params ``n_obj=2, n_prob=10, n_var=10``.

.. code-block:: python

    def get_weight_func():
        return Tensor(np.random.rand(n_prob, n_obj))

    class RandomSolver(GradBaseSolver):
        def __init__(self, step_size, n_iter, tol):
            self.step_size = step_size
            self.n_iter = n_iter
            self.tol = tol

        def solve(self, problem, x, prefs):
        # The base solver uses get_weight_func() to specify weights
        return super().solve(problem, x, prefs, get_weight_func)
