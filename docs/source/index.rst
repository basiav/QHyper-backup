.. documentation master file, created by
   sphinx-quickstart on Thu Oct 27 13:27:51 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. meta::
    :google-site-verification: -BAN3UWgNz2CPUt5v5AcQpDH8GJc0kX0VdKh2Kfj89I


Welcome to QHyper's documentation!
==================================

.. image:: https://user-images.githubusercontent.com/38388283/226841016-711112a8-09d1-4a83-8aab-6e305cb24edb.png
    :width: 40

QHyper - a software framework for hybrid quantum-classical optimization.

Introduction
=================

QHyper is a python library which main goal is to make easier conducting experiments.
Focuses on quantum algorithms, allows also to use classical solvers.

.. code-block:: python

    >>> problem = KnapsackProblem(max_weight=2, items=[(1, 2), (1, 2), (1, 1)])

    >>> params_config = {
            'angels': [[0.5]*5, [1]*5],
            'hyper_args': [1, 2.5, 2.5],
        }

    >>> config = {
            'solver': {
                'type': 'vqa',
                'args': {
                    'optimizer': {
                        'type': 'scipy',
                        'maxfun': 200,
                    },
                    'pqc': {
                        'type': 'hqaoa',
                        'layers': 5,
                    },
                }
            },
            'hyper_optimizer': {
                'type': 'random',
                'processes': 5,
                'number_of_samples': 100,
                'bounds': [[1, 10], [1, 10], [1, 10]]
            }
        }

    >>> vqa = Solver.from_config(problem, config=config)

    >>> vqa.solve(params_cofing)
    {
        'angles': array([0.20700558, 0.85908389, 0.58705246, 0.52192666, 0.7343595 ,
                         0.98882406, 1.00509525, 1.0062573 , 0.9811152 , 1.12500301]),
        'hyper_args': array([1.02005268, 2.10821942, 1.94148846, 2.14637279, 1.88565744])
    }



Architecture
================

QHyper consists with three main components:
    * :ref:`README Problems` - classes describing different types of problems e.g. Knapsack problem or Travelling Salesman Problem
    * :ref:`README Solvers` - classes definng differnt types of solvers e.g. quantum solvers like QAOA or CQM, but also classical algorithms like Gurobi
    * :ref:`README Optimizers` - classes implementing different types of optimizer

Each abstract class allows adding new implementatons which will be compatible with the rest of the system.

.. _README Problems:

Problems
----------

.. graphviz:: _static/classes_problems.dot

More detailed information can be found on :ref:`generated/qhyper.problems.base.problem:qhyper.problems.base.problem`.


.. _README Solvers:

Solvers
----------

.. graphviz:: _static/classes_solvers.dot


More detailed information can be found on :ref:`generated/qhyper.solvers.base.solver:qhyper.solvers.base.solver`.

.. _README Optimizers:

Optimizers
----------

.. graphviz:: _static/classes_optimizers.dot


More detailed information can be found on :ref:`generated/qhyper.optimizers.base.optimizer:qhyper.optimizers.base.optimizer`.



Contents
--------
.. toctree::

   Home <self>
   usage
   api


