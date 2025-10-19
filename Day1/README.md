Of course. Here is a detailed report of your Day 1 work, structured for your documentation.

***

### Introduction

On Day 1, the primary objective was to perform **functional verification** of the Register-Transfer Level (RTL) code for a `full_adder` design. This process involved using the industry-standard Synopsys toolchain to compile the Verilog source code, run a simulation based on a testbench, and finally, analyze the resulting waveforms to ensure the design behaved according to its specification.

---

### Overview of Commands

The verification flow was executed using four key commands in the terminal.

1.  **`vcs -full64 full_adder.v -debug_access+all -lca -kdb`**
    * **Purpose**: This command begins the **two-step compilation** process. It specifically compiles the core design module, `full_adder.v`, into an intermediate object file.
    * **Flags Explained**:
        * `-full64`: Ensures a 64-bit compilation.
        * `-debug_access+all`: A crucial flag that inserts all necessary debugging "hooks" into the compiled code, allowing tools like Verdi to have full visibility into every signal and variable.
        * `-kdb`: Generates a Knowledge Database (KDB), which Verdi uses for advanced features like source code cross-probing and design hierarchy navigation.

2.  **`vcs -full64 full_adder_tb.v -debug_access+all -lca -kdb`**
    * **Purpose**: This is the second step of compilation. It compiles the testbench, `full_adder_tb.v`, and then **links** it with the previously compiled `full_adder` module to create the final simulation executable named **`simv`**.

3.  **`./simv verdi`**
    * **Purpose**: This command executes the compiled simulation. The `simv` file runs the testbench, which provides input stimuli to the `full_adder` design. The core output of this step is the generation of a waveform database file, **`novas.fsdb`**, which logs all signal activity over time.

4.  **`verdi -ssf novas.fsdb -nologo`**
    * **Purpose**: This command launches the **Synopsys Verdi** debug platform to analyze the simulation results.
    * **Flags Explained**:
        * `-ssf novas.fsdb`: The `-ssf` (Simulation Snapshot File) flag explicitly tells Verdi which waveform file to load upon startup.
        * `-nologo`: A minor convenience flag that skips the display of the Verdi startup splash screen.

---

### Results

The simulation results were loaded into Verdi's nWave viewer. The following signals from the `testbench` were added to the wave pane to visualize the design's behavior: `Clock`, `A`, `B`, `C_in`, `SUM`, and `C_out`.



---

### Waveform Analysis

The waveform confirms that the `full_adder` module is functioning correctly. By examining the relationship between the inputs (`A`, `B`, `C_in`) and the outputs (`SUM`, `C_out`) at different simulation times, we can verify the logic.

* **At 20 ns**: The inputs are `A=0`, `B=1`, `C_in=0`. The expected result is `SUM=1`, `C_out=0`. The waveform correctly shows `SUM` as `1` and `C_out` as `0`.
* **At 40 ns**: The inputs are `A=1`, `B=1`, `C_in=0`. This represents $1 + 1 + 0 = 2$, which is binary `10`. The expected result is `SUM=0`, `C_out=1`. The waveform correctly reflects this.
* **At 60 ns**: The inputs are `A=1`, `B=1`, `C_in=1`. This represents $1 + 1 + 1 = 3$, which is binary `11`. The expected result is `SUM=1`, `C_out=1`. The waveform correctly shows both outputs as `1`.

The outputs change correctly on the rising edge of the clock following the input changes, as defined by the testbench logic. All test vectors applied by the testbench produced the logically correct outputs.

---

### Conclusion

On Day 1, the **Synopsys VCS** tool was used for the compilation and simulation of the `full_adder` Verilog module, and the **Synopsys Verdi** tool was used for debugging and waveform analysis. The procedure successfully verified the functional correctness of the RTL design, confirming that its logical behavior matches the specification of a full adder. The design is now ready for the next stage of the ASIC flow.
