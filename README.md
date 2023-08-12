MicroGridsPy - Version 2.0
========================

### Description

The tool main objective is to provide an open-source alternative to the problem of sizing and dispatch of energy in multi-energy systems, integrating a cold thermal energy demand and electrical demand in rural application,
the model integrates reneawble sources with a backup system made of batteries and diesel generators to produce electricity and ice to be stored and dispatched.
It’s written in python(pyomo) and use excel and text files as input and output data handling and visualization. It is an expansion of the existing Micro-Grids Py library, developed by S.Balderrama and S.Quoilin.


Main features:

    Optimal sizing of PV panels, wind turbines, other renewable technologies, back-up genset and electrochemical storage system for least cost electricity supply in rural isolated areas.
    Optimal dispatch from the identified supply systems.
    Possibility to optimize on NPC or operation costs.
    LCOE evaluation for the identified system.
    

### Required libraries

In the current repository under the Environments branch MAC OS and Windows environment made available.
Works with Gurobi, CPLEX, cbc, glpk.

### Licence
This is a free software licensed under the “European Union Public Licence" EUPL v1.1. It 
can be redistributed and/or modified under the terms of this license.

### Getting started

Run from the main file "Micro-Grids.py". In the folder "Inputs" all the required inputs can be provided.

