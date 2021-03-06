.. include:: links.inc

.. _astropy-modeling:

***************************************
Models and Fitting (`astropy.modeling`)
***************************************

Introduction
============

`astropy.modeling` provides a framework for representing models and performing
model evaluation and fitting.  A number of predefined 1-D and 2-D models are
provided and the capability for custom, user defined models is supported.
Different fitting algorithms can be used with any model.  For those fitters
with the capabilities fitting can be done using uncertainties, parameters with
bounds, and priors.

.. _modeling-getting-started:

Getting started
===============

Using a model is a matter of defining the model (instantiating) and then
calling it with the input values for calculation.  This is illustrated with
the code and plot below for a 1-dimensional Gaussian.

.. plot::
    :include-source:

    import numpy as np
    import matplotlib.pyplot as plt
    from astropy.modeling import models

    # define and evaluate the model
    g = models.Gaussian1D(amplitude=1.2, mean=0.9, stddev=0.5)
    x = np.linspace(-5., 5.0, 200)
    y = g(x)

    # plot the model
    plt.figure()
    plt.plot(x, y, 'ko')
    plt.xlabel('x')
    plt.ylabel('y')

.. note::

    A number of significant changes have been made to the internals that have been
    documented in more detail in :doc:`changes_for_4`. This summarizes the two
    biggest changes:

    - Expressions of model classes no longer is supported. (Expressions of model
      instances are still very much supported!)

    - Parameter values now are contained in the parameter instance. Previously they
      were contained in the model referencing the parameter. The previous behavior
      resulted in compound models parameters not sharing the same value as the
      constituent models, if one of them changed, the other didn't. Now they
      see exactly the same value.

.. _modeling-using:

Concepts
========

.. toctree::
   :maxdepth: 1

   Basic Concepts <basics.rst>
   Advanced Concepts <models.rst>
   Model Parameters <parameters.rst>
   Units with Models <units.rst>
   basic-fitting
   Advanced Fitting <fitting.rst>
   Custom Models <new-model.rst>
   Combining Models (Compound Models) <basic-compound-models.rst>
   compound-models
   bounding-boxes
   model-sets
   performance
   changes_for_4

.. TODO list
    Fitting with constraints
    Fitting with units
    Fitting with different or custom statistics functions
    Estimation of fitting errors
    Adding a new fitter
    Using models with Bayesian tools
    Model bounds

Examples
========

.. toctree::
   :maxdepth: 1

   example-fitting-constraints
   example-fitting-uncertainties
   example-fitting-sigma-clipping
   example-fitting-model-sets

.. TODO list
    fitting with masks
    fitting with priors
    fitting with units
    defining 1d model
    defining 2d model
    fitting 2d model
    defining and using a WCS/gWCS model
    defining and using a Tabular1D model
    statistics functions and how to make your own
    compound models
    model sets w/ fitting

Reference/API
=============

.. toctree::
   :maxdepth: 1

   reference_api
