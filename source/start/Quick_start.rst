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


.. code-block:: python

    # import necessary modules
    from libmoon.util_global.initialization import synthetic_init
    from libmoon.util_global.weight_factor import uniform_pref
    from libmoon.util_global import get_problem


Create an algorithm and a problem
=================================

.. note::

    Example1: Finding a size-K (K=5) Pareto solutions with four lines of code.

.. code-block:: python

    from libmoon.solver.gradient.methods import EPOSolver
    from libmoon.util_global.initialization import synthetic_init

    problem = get_problem(problem_name='ZDT1')
    prefs = uniform_pref(n_prob=5, n_obj=problem.n_obj, clip_eps=1e-2)
    solver = EPOSolver(problem, step_size=1e-2, n_iter=1000, tol=1e-2)
    res = solver.solve(x=synthetic_init(problem, prefs), prefs=prefs)

