=================
Overall Framework
=================

:numref:`fig-framework` demonstrates the framework of the proposed ``LibMOON`` library. ``LibMOON`` supports three categories of solvers: MOO solvers aiming to find a finite set of Pareto solutions satisfying certain requirements, PSL solvers aiming to learn whole PS with a single mode, and MOBO solvers aiming to solve expensive problems.

Each solver category is designed highly modulized and new solvers are easy to plugin ``LibMOON`` by rewriting only a small portion of code, e.g.,
the way of gradient manipulation. MOO and PSL solvers support all synthetic, MTL, and realworld (RE) problems,
while MOBO solvers support synthetic and RE problems.


.. _fig-framework:
.. figure:: ../img/LibMOON.png
    :figwidth: 600px
    :align: center
    :figclass: Figure1

    The Framework of ``LibMOON``: ``LibMOON`` addresses synthetic, real-world and MTL problems with three categories of solvers: MOO, PSL, and MOBO solvers.


The overall framework consists of three modules as introduced below.

- The :ref:`problem-ref` includes all supported problems.
- The :ref:`metric-ref` supports the following metrics: (1) hypervolume (HV), (2) inverted general distance (IGD), (3) fill distance (FD), (4) minimal distance (lmin), (5) smooth minimal distance (slmin), (6) Spacing, (7) Span, (8) penalty-based intersection (PBI), (9) inner product (IP), and (10) cross angle (ϑ).
- The :ref:`solver-ref` includes all supported solvers.