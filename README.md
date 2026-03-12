This repository contains the gPROMS model code accompanying the paper:

Dynamic Optimization for Hydrogen Pipeline Network Operations
Sophia B. Shi, Brian A. Korgel, Michael Baldea
McKetta Department of Chemical Engineering, The University of Texas at Austin
Texas Materials Institute, The University of Texas at Austin
Oden Institute for Computational Engineering and Sciences, The University of Texas at Austin

Overview
This code implements a dynamic optimization framework that couples isothermal Euler gas-flow partial differential equations (PDEs) with compressor control and techno-economic analysis for pure-hydrogen pipelines.

Three operational strategies are available:

PTI — Pressure Time-Invariant: compressor discharge pressure is optimized as a single constant value over the time horizon
PDO — Pressure Dynamic Optimization: compressor discharge pressure is optimized at each time interval
FDO — Flow Dynamic Optimization: compressor flowrate is optimized at each time interval

project_root/

├── variable types/

│   ├── variable                  # lower/upper bounds, units, default values

│   └── ... ...

│

├── connection types/

│   └── Gas_Flow                  # mass flowrate and pressure

│
├── models/
│   ├── CEPCI_index               # Convert dollar values considering depreciation
│   ├── Financial_2022            # Convert all dollar values to 2022 dollar value
│   ├── node_passive              # Splitting/merging node 
│   ├── recip_compressor          # Reciprocating Compressor Model with Flowrate Settings
│   ├── pipe_passive              # Passive Pipe Segment Model with Euler's PDE
│   ├── pipe_active_setF          # Active Pipe Segment Model combining a compressor with a passive pipe segment
│   ├── cost_pipe_active          # Cost Model
│   └── scenario#                 # Scenario Model builds the topology and initial setting, and calls the demand profiles
│
├── processes/
│   ├── simulate_scenario#_setP   # Simulation with fixed discharge pressure
│   └── simulate_scenario#_setF   # Simulation with fixed flowrate
│
├── optimisation/
│   ├── PTI_scenario#             # Pressure time-invariant optimization
│   ├── PDO_scenario#             # Pressure dynamic optimization
│   └── FDO_scenario#             # Flow dynamic optimization
│
└── miscellaneous/
    └── demand_profile            # User-defined demand profile input (Before running any simulation or optimization, specify the time-varying demand for each user)
