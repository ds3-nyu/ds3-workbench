=================================
DS3 Workbench - Data Access Layer
=================================

.. image:: https://img.shields.io/badge/License-GPL--3.0--or--later-blue.svg
   :target: https://github.com/ds3-nyu/ds3-workbench/blob/master/LICENSE



About
=====

This repository contains references to different components for the DS3 Workbench.


More Information
================

The **DS3 Workbench** forms the umbrella for inward-facing projects that build infrastructure for Data Science & Software Services (DS3) operations. The main goal is to support intake and management of faculty research projects that are supported by DS3. In particular, the workbench will provide to following functionality:

- an interface that allows researchers to submit project proposals and resource requests,
- send notifications to researchers about potential grant opportunities for their projects,
- an interface that allows students to submit their CV and express their interest to work for DS3 in the future,
- assist DS3 administrators with resource and project planning, and with the hiring process.


An illustration of the overall architecture is shown below.

.. figure:: https://github.com/ds3-nyu/ds3-workbench/blob/master/docs/images/DS3-Workbench-Overview.png
   :scale: 50 %
   :alt: DS3 Workbench Overview

   **Overview of the DS3 Workbench architecture.**


Researchers can enter their project proposals and resource requests via a customer user interface. Among other information they need to specify the kind of work they expect from DS3 as part of their project (e.g., required skills and nice to have skills). If a researcher proposes a project for which they currently do not have grant funding the workbench can notify them about suitable grant opportunities.


Matchmaking & Resource Planning
-------------------------------

The matchmaking tool assists with various tasks:
identify (a set of) employees to work on a submitted project,
highlight shortage of skills to satisfy project requirements,
identify potential candidates for hiring.


Grant Recommendation
--------------------

The grant recommendation engine uses `GrantForward <https://www.grantforward.com/>`_ (a service that the University can subscribe to) for continuous queries (e.g., once a day) to identify grant opportunities for projects that do not yet have funding.
