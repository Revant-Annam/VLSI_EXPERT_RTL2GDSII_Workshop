# 3-Day RTL-to-GDSII Workshop using Synopsys Tools

This repository documents the learnings and project files from a comprehensive 3-day workshop on the complete RTL-to-GDSII flow using industry-standard Synopsys EDA tools. The workshop covered the entire VLSI design flow from initial Verilog simulation to final GDSII generation and signoff.

**Design File:** `fulladder.v`

---

## Workshop Summary

### Day 1: VLSI Flow & RTL Simulation

* **Focus:** Understanding the complete VLSI design flow and performing functional verification of the RTL code.
* **Tools Used:** **Synopsys Verdi**
* **Key Activities:**
    * Learned the theory behind the various stages of the ASIC design cycle.
    * Simulated the `fulladder.v` design along with its testbench (`tb_fulladder.v`).
    * Performed detailed waveform analysis and debugging using the Verdi tool to verify the design's correctness.

---

### Day 2: Logic Synthesis & Physical Design Initiation

* **Focus:** Converting the RTL code into a gate-level netlist and beginning the physical implementation.
* **Tools Used:** **Synopsys Design Compiler (DC)**, **Synopsys ICC2**
* **Key Activities:**
    * Studied the fundamentals of logic synthesis, including constraints, optimization, and technology mapping.
    * Used the DC tool to perform logic synthesis on the full adder design, generating a gate-level netlist.
    * Initiated the physical design stage by importing the netlist into the ICC2 tool.

---

### Day 3: Physical Design & Signoff Verification

* **Focus:** Completing the physical layout of the chip and performing final timing verification.
* **Tools Used:** **Synopsys ICC2**, **Synopsys PrimeTime (PT)**
* **Key Activities:**
    * Learned the theory and practical aspects of key Physical Design stages.
    * Completed **Floorplan**, **Placement**, **Clock Tree Synthesis (CTS)**, and **Routing** within ICC2.
    * Generated the final `GDSII` file.
    * Used the PT tool for static timing analysis (STA) on the final layout to confirm that all timing constraints were met and that there were no violations.

---

## Tools Used

* **Synopsys Verdi:** For simulation and waveform debugging.
* **Synopsys Design Compiler (DC):** For logic synthesis.
* **Synopsys ICC2:** For physical design (floorplanning, placement, CTS, routing).
* **Synopsys PrimeTime (PT):** For static timing analysis (STA) and signoff.
