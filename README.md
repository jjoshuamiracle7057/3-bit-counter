# 3-bit-counter
A 3-bit synchronous counter is a sequential circuit using three T flip-flops to cycle through 8 binary states (000 to 111). It increments on every clock pulse and resets to 000 after reaching 7. Ideal for frequency division and digital clocks, it ensures all bits transition simultaneously to prevent lag and ripple errors.

A 3-bit synchronous binary up-counter is a sequential digital circuit designed to count through a fixed sequence of eight binary states, from 000 (0 in decimal) to 111 (7 in decimal). Unlike asynchronous or "ripple" counters, where the clock signal ripples through each flip-flop one after another, a synchronous counter applies a global clock signal to all three flip-flops simultaneously.

This parallel clocking mechanism ensures that all output bits change state at the exact same moment, effectively eliminating the propagation delays and timing "glitches" that often plague high-speed digital systems. The counter typically utilizes three T (Toggle) Flip-Flops or JK Flip-Flops, where the toggling of each bit is controlled by the logical state of the bits preceding it. 

For instance, the least significant bit (LSB) toggles on every clock pulse, while the second bit only toggles when the LSB is high, and the most significant bit (MSB) only toggles when both lower bits are high (11).Beyond simple counting, the 3-bit counter serves as an efficient frequency divider, where the output of the final flip-flop oscillates at exactly one-eighth the frequency of the input clock.

This characteristic makes it indispensable in timing applications, such as digital clocks, baud rate generators in communication interfaces, and state machine controllers in embedded systems. In a practical hardware environment, such as an FPGA, the counter is often paired with an asynchronous reset signal to ensure the system can be cleared to a known zero state regardless of the clock's current phase. Once the counter reaches its terminal count of 111, the next active clock edge triggers a "roll-over," returning the sequence back to 000 to begin the cycle again. This continuous modulo-8 operation provides a reliable, high-speed rhythmic backbone for complex digital logic operations.

📌 Project Overview
This repository contains the design and implementation of a 3-Bit Synchronous Binary Up-Counter. Unlike asynchronous (ripple) counters, this design uses a common clock signal for all flip-flops, ensuring that all output bits transition simultaneously. This eliminates "glitches" and propagation delays, making it ideal for high-speed digital systems. The counter cycles through 8 states (0 to 7) and resets automatically.

⚙️ Theory and Design
A 3-bit counter consists of three T Flip-Flops (Q0, Q1, Q2). The logic is governed by the state of the preceding bits.

1. Logic Equations
To achieve a synchronous count, the Toggle (T) inputs for each stage are defined as:
T0 (LSB): Always 1 (Toggles on every clock pulse).
T1:Toggles only when Q0 = 1 
T2 (MSB): Toggles only when both Q0 = 1 AND Q1 = 1.

2. State Transition Table

Clock Pulse  Q2​(MSB)   Q1​   Q0​(LSB)
0              0       0      0
1              0       0      1
2              0       1      0
3              0       1      1
4              1       0      0
5              1       0      1
6              1       1      0
7              1       1      1
8              0       0      0(Reset)

🛠 Hardware Features
* Modulus:Mod-8 Counter.
* Clocking: Synchronous (Parallel Clocking).
* Reset: Asynchronous Active-Low Reset included for safety.
* Frequency Division: The MSB output frequency is fin / 8


