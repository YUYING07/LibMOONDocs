===========
Quick Start
===========

In this notebook, we will guide you through the basic steps of using ``LibMOON``.


.. code-block:: python

    # install LibMOO, skip it if you have already installed evox
    try:
        import libmoon
    except ImportError:
        import libmoon==0.1.11

Here we use the a synthetic problem as an example to show how to use ``LibMOON``.

For more detailed list,  please refer to our API documentation :doc:`Supported Benchmark Datasets <Introduction>`.

Create an algorithm and a problem
=================================

.. note::

    Example1: Finding a size-K (K=5) Pareto solutions with four lines of code.

.. code-block:: python

    # import necessary modules
    from libmoon.util.synthetic import synthetic_init
    from libmoon.util.prefs import uniform_pref
    from libmoon.util.problems import get_problem
    from libmoon.solver.gradient.methods import EPOSolver

    problem = get_problem(problem_name='ZDT1')
    prefs = get_uniform_pref(n_prob=5, n_obj=problem.n_obj, clip_eps=1e-2)
    solver = EPOSolver(step_size=1e-2, n_iter=1000, tol=1e-2, problem=problem, prefs=prefs)
    res = solver.solve(x=synthetic_init(problem, prefs))
