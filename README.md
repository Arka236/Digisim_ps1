# Digisim_ps1
Digital hardware design that reads up to 7 coordinate points from ROM, stores them in registers, selects point pairs using counters and multiplexers, computes distance and a custom metric, and continuously updates the minimum value using comparator-controlled registers.
Coordinate Metric Evaluation Using Digital Logic
Overview

This project implements a hardware-based coordinate processing system using discrete digital logic components. The design reads up to seven coordinate points (xi, yi) from ROM, stores them in registers, and systematically evaluates all valid pairs of points. For each pair, the circuit computes mathematical expressions such as Euclidean distance squared and a custom metric function, while continuously tracking the minimum result using comparator-based logic.

The goal of this project is to demonstrate how algorithmic computation typically performed in software can be implemented using pure hardware datapath and control logic.

System Architecture

The system consists of several functional blocks working together:

ROM
 ↓
Decoder
 ↓
Register Bank (Store X and Y coordinates)
 ↓
Multiplexer Network
 ↓
Arithmetic Processing Unit
 ↓
Comparator
 ↓
Minimum Value Register

Each block performs a specific task in the coordinate processing pipeline.

Key Features

Supports up to 7 coordinate points

Stores coordinate data using dedicated X and Y registers

Uses hardware counters to generate valid point pairs

Implements multiplexer-based point selection

Computes:

Euclidean distance squared

Custom metric function

Tracks the minimum value automatically

Fully clock-synchronized digital system

Hardware Components Used

The design uses commonly available digital ICs such as:

ROM – Stores coordinate values

74LS139 – Address decoder for register selection

74179 Registers – Coordinate storage

74151 Multiplexers – Select coordinates

74161 Counters – Generate point indices

74283 Adders – Arithmetic operations

4585 Comparator – Minimum value detection

These components collectively implement the system's datapath and control logic.

Working Principle
1. Coordinate Storage

Coordinate values are stored in ROM. A decoder enables specific registers to load the data, allowing the system to store multiple coordinate pairs simultaneously.

2. Point Selection

Two hardware counters generate indices i and j, representing the selected points. These indices drive multiplexers that choose the corresponding xi, yi, xj, yj values from the register bank.

3. Pair Evaluation

The counters operate similarly to a nested loop structure, ensuring that all valid pairs of points are processed without redundancy.

4. Arithmetic Computation

For each selected pair, the system computes:

Distance:

𝐷
2
=
(
𝑥
𝑖
−
𝑥
𝑗
)
2
+
(
𝑦
𝑖
−
𝑦
𝑗
)
2
D
2
=(x
i
	​

−x
j
	​

)
2
+(y
i
	​

−y
j
	​

)
2

Metric:

𝑀
𝑒
𝑡
𝑟
𝑖
𝑐
=
(
𝑥
𝑖
𝑦
𝑖
+
𝑥
𝑗
𝑦
𝑗
)
 
m
o
d
 
(
𝑖
×
𝑗
)
Metric=(x
i
	​

y
i
	​

+x
j
	​

y
j
	​

)mod(i×j)

These calculations are implemented using adders, subtractors, and multipliers.

5. Minimum Value Tracking

Each computed result is compared with the current minimum value stored in a register. If the new value is smaller, a comparator triggers the load signal to update the minimum register.

Clock and Synchronization

All registers, counters, and control logic operate using a single system clock. This ensures synchronized updates and prevents timing mismatches between arithmetic computations and register updates.

Applications

Although implemented as a learning project, the architecture demonstrates concepts used in:

Hardware accelerators

Signal processing circuits

Embedded datapath design

FPGA and ASIC digital systems

Algorithm implementation in hardware

Learning Outcomes

Through this project, the following digital design concepts are explored:

Datapath and control architecture

Hardware implementation of nested loops

Multiplexer-based data selection

Register-based storage systems

Comparator-driven decision logic

Clock-synchronized digital systems

Possible Improvements

Future improvements could include:

Implementing the design on an FPGA

Increasing the number of supported points

Adding a hardware square-root unit for actual Euclidean distance

Optimizing the metric computation unit

Introducing a finite state machine (FSM) for better control logic

Author

Arka Kar
Electronics Engineering
IIT (BHU)



Repository Folder Structure

Those make the README look 10× more professional.
