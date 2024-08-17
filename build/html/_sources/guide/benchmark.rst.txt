===============
Run a Benchmark
===============

Pareto-Set Learning
===================


It is a learning-based approach that aims to learn the Pareto set of a given problem.

In this notebook, we will guide you through the basic steps of using ``LibMOON``.


.. note::

   PSL in a problem with three lines of solving problem and two lines of evaluating the results.

.. code-block:: python

    from libmoon.solver.psl.core_psl import AggPSLSolver

    problem = get_problem(problem_name='ZDT1')
    # agg list [ ’ls ’, ’tche ’, ’mtche ’, ’pbi ’, ... ]
    prefs = uniform_pref(n_prob=100, n_obj=problem.n_obj, clip_eps=1e-2)
    solver = AggPSLSolver(problem, agg='ls')
    model = solver.solve()
    eval_y = problem.evaluate(model(Tensor(prefs).cuda()))
