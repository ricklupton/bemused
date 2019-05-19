=======
bemused
=======

This is the documentation of **BEMused**, a Python implementation of the `Blade
Element Momentum (BEM)`_ method of modelling the flow around and loads on a wind
turbine rotor (or other kind of rotor).

This code was originally written for `Rick Lupton's PhD thesis`_ and used in `a
related paper`_.

To use it you need to create a :class:`bemused.Blade` object defining your blade
parameters (chord, twist and thickness) and an :class:`bemused.AerofoilDatabase`
containing lift and drag coefficients. You can then use
:class:`bemused.BEMModel` to do the calculations.

Contents
========

.. toctree::
   :maxdepth: 2

   License <license>
   Authors <authors>
   Changelog <changelog>
   Module Reference <api>


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`


.. _Blade Element Momentum (BEM): https://en.wikipedia.org/wiki/Blade_element_momentum_theory
.. _Rick Lupton's PhD thesis: https://doi.org/10.17863/CAM.14119
.. _a related paper: https://doi.org/10.1016/j.renene.2018.11.067
