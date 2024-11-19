Custom OR 6-bit Branch Predictor - gem5 Simulation
===
This project implements a custom 6-bit OR Branch Predictor within the gem5 simulator to evaluate branch prediction accuracy in processor architectures. 
The predictor uses a 6-bit saturation counter mechanism to track the history of branch decisions, ultimately helping reduce mispredictions and improve simulation accuracy for branch-intensive workloads.

Project Overview
---
Branch predictors are critical components in modern processors that aim to anticipate the outcome of conditional branch instructions, reducing stalls in the pipeline and improving overall execution efficiency. 
This project features a custom OR-based branch prediction model that:

Utilizes a 6-bit saturation counter to maintain branch history.

Combines bits using an OR operation to form predictions.

Aims to enhance accuracy by minimizing mispredictions in the simulation environment.

The branch predictor was integrated and tested using the gem5 simulator, which is widely used for modeling and simulating processor architectures.

Architecture
---
6-bit Saturation Counter: The predictor maintains a 6-bit counter for each branch, where each bit represents the likelihood of a branch being taken or not.

OR Logic: The OR-based approach combines the 6 bits into a final decision output, which predicts the branch behavior based on cumulative past outcomes.

Predictor Table: A predictor table stores entries for different branches, with each entry initialized and updated dynamically.

Features
---
Customizable Counter Initialization: Counters can be initialized to different values to simulate diverse prediction scenarios.

Bitwise OR Operation for Prediction: This allows the model to predict branch outcomes by evaluating multiple past outcomes collectively.

Misprediction Analysis: Tracks and outputs misprediction rates to help analyze the predictor's performance under various branch conditions.

Getting Started
---
Prerequisites

gem5 Simulator: Ensure that gem5 is installed and configured on your system. gem5 Installation Guide

C++ Compiler: A C++ compiler compatible with gem5.

Installation
---
Clone this repository or download the source files.
Navigate to your gem5 source directory:

Copy code

cd /path/to/gem5/src/cpu/pred

Copy the custom predictor files custom.cc & custom.hh

Rebuild the gem5 executable to include the custom predictor:

scons build/<ARCH>/gem5.opt

Replace <ARCH> with the appropriate architecture (e.g., X86, ARM).

Usage
---
Run gem5 with your desired simulation configuration, specifying the Custom OR 6-bit branch predictor in the configuration script.

Sample command to initiate a test run:

./build/<ARCH>/gem5.opt configs/example/se.py --cmd=<program> --cpu-type=O3CPU --bp-type=CustomOR6BitPredictor

Modify <program> and other options based on your simulation requirements.

Parameters
---
Initial Counter Value: Configure the initial saturation counter value to fine-tune prediction behavior.

Debug Output: Enable verbose output for step-by-step tracking of predictions and mispredictions.

Results
---
The branch predictor outputs a summary of its performance, including:


Total Predictions: Total number of branches predicted.

Misprediction Rate: Percentage of incorrect predictions.

Prediction Accuracy: Overall accuracy of the branch predictor.

Experimenting with different branch-intensive benchmarks helps in evaluating the predictor's effectiveness under diverse workloads.


Files Included
custom.cc - Core implementation of the branch predictor.

custom.hh - Header file defining the predictor class and methods.

README.md - Documentation for the project.

References
---
This project utilizes the gem5 simulator as a framework for simulating branch prediction logic. For additional resources on gem5, refer to:

gem5 Documentation
Branch Prediction Overview





This is the gem5 simulator.

The main website can be found at http://www.gem5.org

A good starting point is http://www.gem5.org/about, and for
more information about building the simulator and getting started
please see http://www.gem5.org/documentation and
http://www.gem5.org/documentation/learning_gem5/introduction.

To build gem5, you will need the following software: g++ or clang,
Python (gem5 links in the Python interpreter), SCons, SWIG, zlib, m4,
and lastly protobuf if you want trace capture and playback
support. Please see http://www.gem5.org/documentation/general_docs/building
for more details concerning the minimum versions of the aforementioned tools.

Once you have all dependencies resolved, type 'scons
build/<ARCH>/gem5.opt' where ARCH is one of ARM, NULL, MIPS, POWER, SPARC,
or X86. This will build an optimized version of the gem5 binary (gem5.opt)
for the the specified architecture. See
http://www.gem5.org/documentation/general_docs/building for more details and
options.

The basic source release includes these subdirectories:
   - configs: example simulation configuration scripts
   - ext: less-common external packages needed to build gem5
   - src: source code of the gem5 simulator
   - system: source for some optional system software for simulated systems
   - tests: regression tests
   - util: useful utility programs and files

To run full-system simulations, you will need compiled system firmware
(console and PALcode for Alpha), kernel binaries and one or more disk
images.

If you have questions, please send mail to gem5-users@gem5.org

Enjoy using gem5 and please share your modifications and extensions.
