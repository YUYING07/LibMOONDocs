================
libmoon.problem
================

BaseMOP
=======

.. py:class:: BaseMOP

    Base: object

    This base class has the following functions.

    .. py:method:: __init__(self, n_var, n_obj, lbound, ubound, n_cons=0)

        Initialize the problem.

        :param int n_var: Number of variables.
        :param int n_obj: Number of objectives.
        :param ndarray lbound: The lower bound array.
        :param ndarray ubound: The upper bound array.
        :param int n_cons: Number of constraint functions.

    .. py:method:: get_number_variable(self)

        :return: n_var.
        :rtype: int

    .. py:method:: get_number_objective(self)

        :return: n_obj.
        :rtype: int

    .. py:method:: get_number_constraint(self)

        :return: n_cons.
        :rtype: int

    .. py:method:: get_lbound(self)

        :return: lbound.
        :rtype: ndarray

    .. py:method:: get_ubound(self)

        :return: ubound.
        :rtype: ndarray

DTLZ
=====

.. py:class:: DTLZ1

    Base: ``BaseMOP``

    Synthetic DTLZ dataset from `"Scalable test problems for evolutionary multiobjectiveoptimization, Evolutionary multiobjective Optimization." <https://link.springer.com/chapter/10.1007/1-84628-137-7_6>`_

    .. py:method:: __init__(self, n_var=30, n_obj=3, lbound=np.zeros(30), ubound=np.ones(30))

        Initialize the DTLZ1 problem.

    .. py:method:: _evaluate_torch(self, x)
        :param torch.Tensor x: The decision variable array.
        :return: The objective array.
        :rtype: torch.Tensor

    .. py:method:: _evaluate_numpy(self, x)
        :param ndarray x: The decision variable array.
        :return: The objective array.
        :rtype: ndarray

.. py:class:: DTLZ2

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=30, n_obj=3,lbound=np.zeros(30), ubound=np.ones(30))

        Initialize the DTLZ2 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)

.. py:class:: DTLZ3

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=30, n_obj=3,lbound=np.zeros(30), ubound=np.ones(30))

        Initialize the DTLZ3 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)

.. py:class:: DTLZ4

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=30, n_obj=3, lbound=np.zeros(30), ubound=np.ones(30))

        Initialize the DTLZ4 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


MAF1
=====

.. py:class:: MAF1

    Base: ``BaseMOP``

    Synthetic MAF1 dataset from `"A benchmark test suite for evolutionary many-objective optimization." <https://colab.ws/articles/10.1007%2Fs40747-017-0039-7>`_

    .. py:method:: __init__(self, n_var=30, n_obj=3, lbound=np.zeros(30), ubound=np.ones(30))

        Initialize the MAF1 problem.


    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


RE
==

.. py:class:: RE21

    Base: ``BaseMOP``

    Synthetic RE dataset from `"An easy-to-use real-world multi-objective optimization problem suite." <https://www.sciencedirect.com/science/article/pii/S1568494620300181>`_

    .. py:method:: __init__(self, n_var=4, n_obj=2, lbound=np.zeros(4), ubound=np.ones(4))

        Initialize the RE21 problem.


    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE22

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=3, n_obj=2, lbound=np.zeros(3), ubound=np.ones(3))

        Initialize the RE22 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE23

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=4, n_obj=2, lbound=np.zeros(4), ubound=np.ones(4))

        Initialize the RE23 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE24

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=2, n_obj=2, lbound=np.zeros(2), ubound=np.ones(2))

        Initialize the RE24 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE25

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=3, n_obj=2, lbound=np.zeros(3), ubound=np.ones(3))

        Initialize the RE25 problem.



    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE31

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=3, n_obj=3, lbound=np.zeros(3), ubound=np.ones(3))

        Initialize the RE31 problem.



    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE37

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=3, n_obj=3, lbound=np.zeros(4), ubound=np.ones(3))

        Initialize the RE37 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE41

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=4, n_obj=7, lbound=np.zeros(4), ubound=np.ones(3))

        Initialize the RE41 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: RE42

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=4, n_obj=6, lbound=np.zeros(4), ubound=np.ones(3))

        Initialize the RE41 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


VLMOP
=====

.. py:class:: VLMOP1

    Base: ``BaseMOP``

    Synthetic VLMOP dataset from `"Distributed Multiobjective Optimization Problems and Methods for their Solution." <https://link.springer.com/chapter/10.1007/978-3-642-59132-7_26>`_

    .. py:method:: __init__(self, n_var=10, n_obj=2, lbound=np.zeros(10), ubound=np.ones(10)

        Initialize the VLMOP1 problem.

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)


.. py:class:: VLMOP2

    Base: ``BaseMOP``

    .. py:method:: __init__(self, n_var=10, n_obj=2, lbound=np.zeros(10), ubound=np.ones(10)

       Volkovich et al. Distributed Multiobjective Optimization Problems and Methods for their Solution.1997

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)

ZDT
====

.. py:class:: ZDT1

    Base: ``BaseMOP``

    Synthetic ZDT dataset from `"An easy-to-use real-world multi-objective optimization problem suite" <https://www.sciencedirect.com/science/article/pii/S1568494620300181>`_

    .. py:method:: __init__(self, n_var=30, n_obj=2, lbound=np.zeros(30), ubound=np.ones(30)

    .. py:method:: _evaluate_torch(self, x)

    .. py:method:: _evaluate_numpy(self, x)

    .. py:method::_get_pf(self, n_points=100)
            :param int n_points: Number of points.
            :return: The Pareto front.
            :rtype: ndarray


.. py:class:: ZDT2

        Base: ``BaseMOP``

        .. py:method:: __init__(self, n_var=30, n_obj=2, lbound=np.zeros(30), ubound=np.ones(30)

        .. py:method:: _evaluate_torch(self, x)

        .. py:method:: _evaluate_numpy(self, x)

        .. py:method::_get_pf(self, n_points=100)


.. py:class:: ZDT3

        Base: ``BaseMOP``

        .. py:method:: __init__(self, n_var=30, n_obj=2, lbound=np.zeros(30), ubound=np.ones(30)

        .. py:method:: _evaluate_torch(self, x)

        .. py:method:: _evaluate_numpy(self, x)

        .. py:method::_get_pf(self, n_points=100)


.. py:class:: ZDT4

            Base: ``BaseMOP``

            .. py:method:: __init__(self, n_var=10, n_obj=2, lbound=np.zeros(10), ubound=np.ones(10)

            .. py:method:: _evaluate_torch(self, x)

            .. py:method:: _evaluate_numpy(self, x)

            .. py:method::_get_pf(self, n_points=100)


.. py:class:: ZDT6

            Base: ``BaseMOP``

            .. py:method:: __init__(self, n_var=30, n_obj=2, lbound=np.zeros(30), ubound=np.ones(30)

            .. py:method:: _evaluate_torch(self, x)

            .. py:method:: _evaluate_numpy(self, x)

            .. py:method::_get_pf(self, n_points=100)


