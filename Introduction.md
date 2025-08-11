### Introduction to a 1010 Non-Overlapping Moore Sequence Detector

This project presents a **Moore sequence detector** designed to recognize the binary sequence **"1010"** within a serial data stream. The core feature of this design is its **non-overlapping** nature, meaning that once a "1010" sequence is detected and signaled, the detector does not reuse the last bits of that sequence to begin detecting a new one. It waits for the next valid starting bit.

### Design Overview
The sequence detector is implemented as a **Finite State Machine (FSM)**. A Moore machine model was chosen because its output depends solely on the current state, making the design clear and straightforward.

* **States:** The design includes states to track the detection process of the "1010" sequence. Each state represents a part of the sequence that has been successfully recognized so far.
* **Input:** A single serial data bit is fed into the system on each clock cycle.
* **Output:** The output signal is asserted (typically goes high '1') for one clock cycle when the "1010" sequence is successfully detected.

---

### Purpose and Applications
The primary goal of this project is to provide a clear and simple example of how to design a non-overlapping sequence detector using a Moore FSM. The provided VHDL or Verilog source code can be synthesized and implemented on an FPGA (Field-Programmable Gate Array) or an ASIC (Application-Specific Integrated Circuit).

Potential applications for such a sequence detector include:
* **Data Communications:** For data synchronization or packet recognition.
* **Signal Processing:** To identify a specific pattern within a data stream.
* **Control Systems:** To trigger an action when a particular sequence of events occurs.

---

### Repository Contents
This repository includes:
* **Source Code:** VHDL or Verilog files for the sequence detector design.
* **Testbench:** A testbench file written to simulate the design and verify its correctness.
* **State Diagram:** An image or description of the FSM state diagram used in the design.
* **Documentation:** A brief explanation of how the design works.
