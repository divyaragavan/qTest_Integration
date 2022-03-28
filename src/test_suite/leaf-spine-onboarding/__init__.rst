.. highlight:: robotframework

Leaf Spine Test Suite
=====================

Overview
========
Automation of SVCT Test cases - Onboarding of Devices on Large Node

.. code:: robotframework

    *** Settings ***
    Resource        keywords/leaf_spine_onboarding.robot
    Suite setup     leaf_spine_onboarding.Setup Leaf Spine Onboarding Suite

Test Topology
=============

This is an OpenReach Large Leaf-Spine test setup as depicted in the figure below:

.. image:: _static/open_reach_large.png
    :align:  center

Tests
=====

.. toctree::
   :caption: Contents:
   :maxdepth: 1

   leaf_spine_onboarding.rst
