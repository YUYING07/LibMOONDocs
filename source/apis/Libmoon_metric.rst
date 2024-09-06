.. _metric-ref:
================
libmoon.metric
================

Functions
=========

Metrics can be divided into two parts, the first part measures the quality of a set of solutions :math:`\mathbb{S} = \{ y^{(1)}, \ldots, y^{(N)} \}`.

.. py:function:: compute_hv(solutions)

    The hypervolume indicator measures the dominated volume by at least one objective belongs to the set :math:`\mathbb{Y}` with a reference point :math:`\mathcal{r}`.

    .. math::

        \begin{align*}
        \mathrm{HV}_\mathcal{r} = \mathrm{Vol}( \{\mathcal{y} | \exists \mathcal{y'} \in \mathbb{Y}, \mathcal{y'} \preceq \mathcal{y} \preceq \mathcal{r} \} ).
        \end{align*}

    :param list solutions:

.. py:function:: compute_lmin(solutions)

    Minimal distance indicator :math:`(l_{\min})`, which measures the minimal pairwise distances among all objectives.

    .. math::

        \begin{align*}
        \mathrm{l}_{\min} = \min_{1 < i < j < N} \rho(y^{(i)}, y^{(j)}),
        \end{align*}

    where :math:`\rho` denotes the Euclidean distance.
    :param list solutions:

.. py:function:: compute_slmin(solutions)

    Soft minimal distance indicator }, which serves as the “soft-min” version of the minimal distance function

    .. math::

        \begin{equation}
        \mathrm{sl}_{\min} = -\frac{1}{hN(N-1)} \log \left( \sum_{1 < i < j < N} \exp\left(-h \rho\left(y^{(i)}, y^{(j)}\right)\right) \right).
        \end{equation}

    :param list solutions:

.. py:function:: compute_spacing(solutions)

    Spacing indicator is supposed to be small, which indicates that objectives vectors are uniformly distributed. Spacing indicator is defined as follows

    .. math::
        \begin{equation}
        \mathrm{spacing} = \frac{1}{N} \sum_{i=1}^N (d_i - \bar{d})^2, \qquad \bar{d} = \frac{1}{N} \sum_{i=1}^N d_i, \qquad d_i = \min_{i \neq j} \rho(y^{(i)}, y^{(j)}).
        \end{equation}

    :param list solutions:


.. note::

    For IGD and FD, these two indicators rely that the true Pareto front :math:`Z` is known.
    And for the second part of indicators, these indicators measure the quality of a single solution :math:`y` with a given preference vector :math:`\lambda`.

.. py:function:: compute_igd(solutions, Z)

    Inverted(GD) indicator indicator, measuring the average distance

    .. math::

        \begin{align*}
        \operatorname{IGD}(\mathbb{S})= \frac{1}{|\mathbb{Z}|}\left( \sum_{i=1}^{|\mathbb{Z}|} \min_{y' \in \mathbb{Z}} \rho(y^{(i)}, y') ^{2} \right)^{1/2},
        \end{align*}

    where :math:`\mathbb{Z}` is a reference set

    :param list solutions:
    :param list Z:


.. py:function:: compute_fd(solutions, Z)

    Fill Distance(FD) is the covering radius of a set of solutions:math:`\mathbb{S}`

    .. math::

        \begin{equation}
        \mathrm{FD}(\mathbb{A}) = \max_{y' \in \mathbb{Z}} \min_{y \in \mathbb{A}} \rho(y, y').
        \end{equation}

    :param list solutions:
    :param list Z:


.. note::

   In the following part, we introduce indicators related to preference vectors :math:`\lambda`:


.. py:function:: compute_pbi(y, \lambda)

    The Penalty-based Intersection (PBI) indicator, which represents a weighted sum of distance functions :math:`d_1`$` and $d_2$. It is given by :math:`\mathrm{PBI} = d_1 + \mu d_2`, where

    .. math::

        \begin{equation}
        d_1 = \frac{\langle y - z, \lambda \rangle}{\lVert \lambda \rVert}, \qquad d_2 = \lVert y - (d_1\lambda + z) \rVert.
        \end{equation}

    :param list y:
    :param list \lambda:

.. py:function:: compute_inner_product(y, \lambda)
    The inner product indicator,

    .. math::
        \begin{equation}
        \mathrm{Ip} = \langle y, \lambda \rangle,
        \end{equation}

    measures the alignment of objective :math:`y` with preference vector :math:`\lambda`.

    :param list y:
    :param list \lambda:

.. py:function:: compute_cross_angle(y, \lambda)
    TFor bi-objective problems, the cross angle indicator,

    .. math::
        \begin{equation}
        \vartheta = \lVert \arctan(y_2 / y_1) - \arctan(\lambda_2 / \lambda_1) \rVert
        \end{equation}

    measures the alignment of objective :math:`y` with preference vector :math:`\lambda`.

    :param list y:
    :param list \lambda:


