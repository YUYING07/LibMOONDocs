# Introduction

`LibMOON` is a multiobjective optimization framework that spans from single-objective optimization to multiobjective
optimization. It aims to enhance the understanding of optimization problems and facilitate fair comparisons between MOO
algorithms. A submission to NeurIPS 2024 DB track.

## Supported Benchmark Datasets

| Datasets                                                                                                                         | Problems           | Project/Code                                           |
|----------------------------------------------------------------------------------------------------------------------------------|--------------------|--------------------------------------------------------|
| [ZDT](https://ieeexplore.ieee.org/document/996017)                                                                               | Synthetic          | [Project](https://pymoo.org/problems/multi/zdt.html)   |
| [DTLZ](https://ieeexplore.ieee.org/document/996017)                                                                              | Synthetic          | [Project](https://pymoo.org/problems/multi/zdt.html)   |
| [MAF](https://link.springer.com/article/10.1007/s40747-017-0039-7)                                                               | Synthetic          | [Project](https://pymoo.org/problems/multi/zdt.html)   |
| [WFG](https://ieeexplore.ieee.org/document/996017)                                                                               | Synthetic          | [Code](https://github.com/ryojitanabe/reproblems)      |
| [Fi's](https://ieeexplore.ieee.org/document/996017)                                                                              | Synthetic          | [Code](https://github.com/ryojitanabe/reproblems)      |
| [RE](https://arxiv.org/abs/2009.12867)                                                                                           | Synthetic          | [Code](https://github.com/ryojitanabe/reproblems)      |
| [MO-MNISTs](https://proceedings.neurips.cc/paper_files/paper/2019/file/685bfde03eb646c27ed565881917c71c-Paper.pdf)               | Multitask Learning | [COSMOS](https://github.com/ruchtem/cosmos)            |
| [Fairness Classification	](https://arxiv.org/pdf/2103.13392)                                                                     | Multitask Learning | [COSMOS](https://github.com/ruchtem/cosmos)            |
| [Federated Learning](https://proceedings.neurips.cc/paper_files/paper/2023/file/7cb2c2a8d35576c00078b6591ec26a7d-Paper.pdf)      | Multitask Learning | [COSMOS](https://github.com/ruchtem/cosmos)            |
| [Synthetic (DST, FTS...)](https://proceedings.neurips.cc/paper_files/paper/2019/file/4a46fbfca3f1465a27b210f4bdfe6ab3-Paper.pdf) | Multitask Learning | [Project](https://github.com/sample-repo/envelop-code) |
| [Robotics (MO-MuJoCo...)](https://proceedings.mlr.press/v119/xu20h/xu20h.pdf)                                                    | Multitask Learning | [Code](https://github.com/mit-gfx/PGMORL)              |

## Supported Algorithms

`LibMOON` supports the following algorithms:

| Method	                                                                                                       | Property                                                               | 	#Obj              | 	Support	 | Venues       | 	Complexity     | Arguments            |
|---------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|--------------------|-----------|--------------|-----------------|----------------------|
| Aggregation fun. based, e.g. Tche,mTche,LS,PBI,...                                                            | Pareto solution with aggregations.                                     | Any                | Yes       |              |                 | `GradAggSolver`      |
| [COSMOS](https://arxiv.org/pdf/2103.13392)	                                                                   | Approximated exact solution.	                                          | Any                | Yes       | ICDM 2021    | $O(m n K )$     |                      |
| [EPO](https://proceedings.mlr.press/v119/mahapatra20a/mahapatra20a.pdf)                                       | Exact solution.                                                        | Any                | Yes       | ICML 2020    | $O(m^2 n K )$   | `EPOSolver`          |
| [MOO-SVGD](https://openreview.net/pdf?id=S2-j0ZegyrE)                                                         | A set of diverse Pareto solution.                                      | Any                | Yes       | NeurIPS 2021 | $O(m^2 n K^2 )$ | `MOO-SVGDSolver (*)` |
| [MGDA](https://proceedings.neurips.cc/paper/2018/file/432aca3a1e345e339f35a30c8f65edce-Paper.pdf)             | Arbitray Pareto solutions. Location affected highly by initialization. | Any                | Yes       | NeurIPS 2018 | $O(m^2 n K )$   | `MGDASolver `        |
| [PMGDA](https://arxiv.org/abs/2402.09492)                                                                     | Pareto solutions satisfying any preference.                            | Any                | Yes       | TETCI        | $O(m^2 n K )$   | `PMGDASolver`        |
| [PMTL](https://proceedings.neurips.cc/paper_files/paper/2019/file/685bfde03eb646c27ed565881917c71c-Paper.pdf) | Pareto solutions in sectors.                                           | 2. 3 is difficult. | Yes       | NeurIPS 2019 | $O(m^2 n K^2 )$ | `PMTLSolver`         |
| [HVGrad ](https://arxiv.org/abs/2102.04523)                                                                   | It is a gradient-based HV method.                                      | 2/3                | Yes       | CEC2023      | $O(m^2 n K^2 )$ | `HVGradSolver`       |

Here, $m$ is the number of objectives, $K$ is the number of samples, and $n$ is the number of decision variables.
For neural network based methods, $n$ is the number of parameters; hence $n$ is very large (>10000), $K$ is also large (
e.g., 20-50), while $m$ is small (2.g., 2-4).
As a result, $m^2$ is not a big problem. $n^2$ is a big problem. $K^2$ is a big problem.

Time complexity of gradient based methods are as follows,

1. Tier 1. GradAggSolver.
2. Tier 2. MGDASolver, EPOSolver, PMTLSolver.
3. Tier 3. GradHVSolver
4. Tier 4. MOOSVGDSolver

Important things to notice:
The original code MOO-SVGD does not offer a MTL implement. Our code is the first open source code for MTL MOO-SVGD.

|                                            | 	Problems	                                    | Arguments                |
|--------------------------------------------|-----------------------------------------------|--------------------------|
|                                            | Pareto set learning Solvers                   | `EPO-based PSL`          |
|                                            | Pareto set learning Solvers                   | `Agg-based PSL`          |
|                                            | Pareto set learning Solvers                   | `PMGDA-based PSL`        |
|                                            | Pareto set learning Solvers                   | `Evolutionary-based PSL` |
|                                            | MultiObjective Bayesian Optimization  Solvers | `PSL-MONO`               |
|                                            | MultiObjective Bayesian Optimization  Solvers | `PSL-DirHV-EI`           |
|                                            | MultiObjective Bayesian Optimization  Solvers | `DirHV-EGO`              |
| [HV Net](https://arxiv.org/abs/2203.02185) | Machine Learning Pretrained                   |                          |

## Contributors

`LibMOON` is developed by the following contributors:

- [Xiaoyuan Zhang](https://scholar.google.com/citations?user=KQj18L8AAAAJ&hl=zh-TW) (Maintainer of Pareto set learning,
  gradient-based solver)
- [Liang Zhao](https://liazhao5.github.io/) (Maintainer of MOBO)
- [Xi Lin](https://xi-l.github.io/)
- [Yingying Yu](https://scholar.google.com/citations?user=nw6-_5wAAAAJ&hl=en)

## Contact Us

- If you have any question or suggestion, please feel free to contact us by raising an issue or sending an email
  to `xzhang2523-c@my.cityu.edu.hk`.
- QQ Group:

<img src="/assets/img/qq.jpg" width="20%">

## Advisory Board

- Prof. [Yifan Chen](https://ychen-stat-ml.github.io/) (Hong Kong Baptist University)
- Prof. [Zhichao Lu](https://www.cs.cityu.edu.hk/~zhichalu/) (City University of Hong Kong)
- Prof. [Han Zhao](https://hanzhaoml.github.io/) (University of Illinois at Urbana-Champaign)
- Prof. [Ke Shang](https://scholar.google.com.hk/citations?user=jFUXL1AAAAAJ&hl=zh-CN) (Shenzhen University)
- Prof. [Tao Qin](https://scholar.google.com/citations?user=Bl4SRU0AAAAJ&hl=zh-CN) (Microsoft Research)

## Correspondence

For any inquiries, please contact [Qingfu Zhang](https://www.cs.cityu.edu.hk/~qzhan7/index.html) (FIEEE, City
University of Hong Kong) at the corresponding address.
