# Tiltrotor Mission Planner and Rotor Performance Model

## Overview

This project is a Python-based preliminary design and performance tool for a twin-rotor VTOL/tiltrotor aircraft.

The code brings together rotor aerodynamic analysis, aircraft sizing, forward-flight performance, mission simulation, fuel burn and design studies in one workflow. It is intended for preliminary aircraft design and parametric studies rather than detailed certification-level analysis.

The main aerodynamic method used for the rotor is Blade Element Momentum Theory (BEMT). The aircraft-level model then uses the rotor results to estimate power requirements and complete a defined mission.

## What the code does

The program covers the following main areas:

- ISA atmosphere calculations
- Airfoil lift and drag modelling
- BEMT rotor analysis
- Rotor thrust, torque and power calculation
- Rotor performance and stall checks
- BEMT validation against reference data
- Blade number, solidity, taper and twist studies
- Airfoil comparison and rotor selection
- Preliminary aircraft sizing
- Hover performance
- Forward-flight performance
- Aircraft drag and power calculations
- Mission segment simulation
- Aircraft mass and fuel updates
- Power required and power available checks
- Range and endurance studies
- Performance sensitivity plots
- Mission result tables and warnings

## Model structure

The code is organised so that the analysis progresses from the basic aerodynamic inputs to the aircraft-level mission model.

text
Atmosphere
    ↓
Airfoil model
    ↓
BEMT rotor model
    ↓
Rotor validation and design studies
    ↓
Rotor / airfoil selection
    ↓
Aircraft sizing
    ↓
Hover and forward-flight performance
    ↓
Mission definition
    ↓
Mission simulation
    ↓
Fuel and mass update
    ↓
Performance results and plots


## Main sections

| Section | Purpose |
|---|---|
| Atmosphere model | Calculates atmospheric properties for the selected altitude. |
| Airfoil model | Provides lift and drag characteristics used by the rotor model. |
| BEMT solver | Calculates rotor thrust, torque, power and blade loading. |
| BEMT validation | Checks the rotor model against reference experimental data. |
| Rotor design studies | Examines the effect of blade number, solidity, taper and twist. |
| Airfoil comparison | Compares candidate airfoil behaviour for the rotor application. |
| Rotor selection | Defines the final rotor geometry used by the aircraft model. |
| Aircraft sizing | Estimates the main aircraft and rotor sizing parameters. |
| Forward-flight analysis | Evaluates rotor behaviour and aircraft performance in cruise. |
| Mission model | Defines and runs the different aircraft mission segments. |
| Fuel and mass model | Updates aircraft mass as fuel is consumed. |
| Performance studies | Calculates range, endurance, speed and other performance quantities. |
| Results and plots | Produces tables, graphs and mission warnings. |

## Requirements

The code is written for Python 3.

The main Python packages used by the model are:

- NumPy
- Pandas
- Matplotlib
- SciPy

A typical installation is:

bash
pip install numpy pandas matplotlib scipy


Using a virtual environment is recommended:

bash
python -m venv venv


Activate it on Windows:

bash
venv\Scripts\activate


Then install the required packages:

bash
pip install numpy pandas matplotlib scipy


## How to run

Place the Python file and any required input/reference files in the same working directory.

Run:

bash
python total_code_cleaned.py


The program will execute the analysis in its defined order and generate the corresponding printed results and plots.

If running from an IDE such as VS Code, PyCharm or Spyder, open `total_code_cleaned.py` and run the complete script.

## Reproducing the analysis

The main inputs are defined within the Python file. To reproduce a particular design case:

1. Open `total_code_cleaned.py`.
2. Locate the aircraft, rotor and mission input sections.
3. Set the desired aircraft mass, rotor configuration and operating conditions.
4. Set the mission segments and their durations/distances.
5. Keep the analysis settings unchanged if an existing case needs to be reproduced.
6. Run the complete script.
7. Compare the generated tables and plots with the original case.

For a new design study, change only the relevant design variable while keeping the other inputs fixed. This makes the resulting performance change easier to interpret.

## Mission simulation

The mission model treats the flight as a sequence of segments. Depending on the defined mission, these can include phases such as:

- Takeoff / hover
- Climb
- Transition
- Cruise
- Descent
- Landing / hover

During the simulation, the aircraft state is updated as the mission progresses. The model tracks quantities such as:

- Time
- Distance
- Aircraft mass
- Fuel remaining
- Rotor tilt
- RPM
- Power required
- Power available
- Advance ratio
- Rotor thrust coefficient
- Tip Mach number

Mission warnings are used to identify conditions such as insufficient available power or inadequate fuel.

## Rotor model

The rotor calculations are based on Blade Element Momentum Theory.

The blade is divided into radial elements. For each element, the model evaluates the local flow and blade loading and then integrates the results over the rotor.

The rotor model provides quantities including:

- Thrust
- Torque
- Power
- Power loading
- Rotor coefficients
- Local angle of attack
- Tip Mach number
- Stall-related limits

These results are then used by the aircraft and mission models.

## Design studies

The code includes parametric studies for important rotor design variables.

### Blade number

The effect of changing the number of blades on rotor loading and performance can be studied while keeping the other rotor parameters fixed.

### Solidity

Rotor solidity can be varied to examine its effect on thrust, power and efficiency.

### Taper

Blade taper is studied to see how the radial chord distribution affects rotor performance.

### Twist

Blade twist can be varied to improve the distribution of aerodynamic loading along the blade.

### Airfoil selection

Candidate airfoils can be compared before selecting the airfoil used for the final rotor model.

## Validation

The BEMT model includes a validation step against reference rotor performance data.

The validation compares calculated and reference quantities and provides error measures such as RMSE and MAPE.

This is intended as a check on the rotor model before using it for the aircraft-level studies.

## Outputs

Depending on the selected analysis, the program produces:

- Rotor performance values
- Validation results
- Design-study tables
- Performance curves
- Aircraft sizing results
- Mission segment tables
- Fuel and mass histories
- Range and endurance results
- Power required / available comparisons
- Mission warnings
- Sensitivity plots

## Important input groups

When modifying the model, the most important groups of inputs are:

### Rotor inputs

- Rotor radius
- Number of blades
- RPM
- Blade chord
- Blade twist
- Blade taper
- Rotor tilt
- Airfoil data

### Aircraft inputs

- Takeoff mass
- Empty mass
- Payload
- Fuel mass
- Number of rotors
- Aircraft drag parameters
- Propulsion power

### Mission inputs

- Segment type
- Segment duration
- Segment distance
- Altitude
- Flight speed
- Rotor tilt
- Wind condition
- Fuel reserve requirement

## Recommended workflow

For a new aircraft configuration, the following order is recommended:

text
1. Set atmosphere and operating conditions
2. Define airfoil data
3. Define rotor geometry
4. Run BEMT rotor analysis
5. Check rotor validation
6. Perform rotor design studies
7. Select rotor geometry
8. Define aircraft-level parameters
9. Run hover and forward-flight analysis
10. Define the mission
11. Run the mission simulation
12. Check fuel and power margins
13. Generate the final plots and tables


## Notes

This is a preliminary design and analysis tool. The results depend strongly on the assumptions used for the aerodynamic model, propulsion system, aircraft drag, fuel model and mission inputs.

The code should therefore be used mainly for design comparison, sensitivity studies and preliminary performance estimation. Higher-fidelity CFD, experimental testing or validated propulsion models should be used when detailed design accuracy is required.

## File

The main program is:

Team7_compiled.py

The cleaned version retains the original calculation flow and functionality while removing redundant preliminary parameters, repeated imports, dead/commented-out code and unnecessarily long comments.

## Author / Project

Tiltrotor preliminary design, rotor performance and mission analysis project.

