
Cold Thermal Multi-Energy System Py (MES-Py)
========================

    ##### DESCRIPTION ##### 
The tool main objective is to provide an open-source alternative to the problem of sizing and dispatch of energy in multi-energy systems, integrating a cold thermal energy demand and electrical demand in rural application,
the model integrates reneawble sources with a backup system made of batteries and diesel generators to produce electricity and ice to be stored and dispatched.
It’s written in python(pyomo) and use excel and text files as input and output data handling and visualization. It is an expansion of the existing Micro-Grids Py library, developed by S.Balderrama and S.Quoilin.

Main features:

    Optimal sizing of: a) Lion-Ion batteries, diesel generators and renerable sources; 
                       b) Refrigerative cycle's compressor and thermal energy storage sizing to supply a single-node electricity demand and a cold thermal demand with the lowest cost possible.
    Optimal dispatch from different energy sources.
    Calculation of the net present cost of the system for the project lifetime.
    Determination of the LCOE for the optimal system.


    ##### FOLDERS ##### :

"Inputs"	           : inputs for resource availability, demand curve, technology characterization.
"Results"	           : results of the model in .XLSX form.
"Demand_archetypes"        : list of demand archetypes for different rural users.

     ##### SCRIPTS #####

"Micro-Grids"              : model MAIN script, it contains the run instructions. May be used to change the optimization goal (minimize NPC/ minimize Operation Cost),
                             to force minimum renewable penetration, minimum number of days to run with only batteries or days to run without ice producrion, to select brownfield and two-objective optimization
"Constraints_XXfield"         : contains the definition of all the governing equations of the model
"Initialize"                  : contains the import of model parameters and the initialization of specific variables
"Model_Creation"              : contains the creation of the Pyomo variables 
"Model_Resolution_Greenfield" : contains the creation of the Pyomo instance, to be elaborated by the external solver (GUROBI, CPLEX, GLPK)
"Results"                     : script for results extraction, elaboration and export to Excel; also contains the functions needed for the results plot
"Demand"	              : script for the calculation of the total load profile from demand archetypes.
"Re_input_data"               : script for extraction of input for renewables production script
"RE_calculation"              : contains the general calculations for input renewable energy production time-series
"Solar_PV_calculation"        : contains calculations for solar PV production
"Wind_calculation"            : contains calculations for wind turbine production
"Typical_year"                : contains Typical Meteorological Year calculations
"Windrose"                    : script to construct the windrose plot
"Grid_Availability"           : contains the calculations for the national grid availability matrix 
"Plots"                       : script for visual representation of results.

    ##### RESULTS FILES #####

Results_Summary.xlsx : spreadsheet containing
			- sheet 'Size': Installed capacity of each component, including the TES size.
			- sheet 'Cost': Economic breakdown of the system. All the costs are ACTUALIZED to the year at which they occur.
			- sheet 'Yearly cash flows': Breakdown of yearly NON-ACTUALISED costs (fixed O&M, fuel cost, battery replacement, lost load), grouped by component type (battery, generators, renewable technologies)
			- sheet 'Yearly energy parameters': 
						* Generators share: total energy provided by generators divided by total electric demand
                                                * Renewables penetration: total energy provided by renewables divided by the sum of total energy provided by both renewables and generators
                                                * Curtailment share: total energy curtailed divided by the sum of total energy provided by both renewables and generators  
                                                * Battery usage: total energy discharged by the batteries divided by total electric demand
						* Grid usage: total energy withdrawn from the national grid divided by total electric demand
			- sheet 'Yearly energy parameters SC': 
						* Generators share: total energy provided by generators divided by total electric demand for each scenario.
                                                * Renewables penetration: total energy provided by renewables divided by the sum of total energy provided by both renewables and generators for each scenario.
                                                * Curtailment share: total energy curtailed divided by the sum of total energy provided by both renewables and generators for each scenario.
                                                * Battery usage: total energy discharged by the batteries divided by total electric demand for each scenario.
						* Grid usage: total energy withdrawn from the national grid divided by total electric demand for each scenario.

Time_Series.xlsx : spreadsheet containing
		  - hourly energy balance of the system (technologies energy production, battery energy flows, electrical and thermal demand(under the form of compressor electrical consumption),
                    lost load, curtailment) + state of charge of the batteries and of the thermal storage, ice priduction and its dispatch, COP calculated for each time step and fuel consumed by the generators
		  - each year of the time horizon is reported on a different sheet

Plots: 
DispatchPlot : image print-out of system energy dispatch and load demand for the selected date(s)
IcePlot      : image print-out of system thermal energy dispatch under the form of mass of ice and load demand for the selected date(s)