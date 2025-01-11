# Unintended Latch in VHDL

This repository demonstrates a common but subtle error in VHDL code: an unintended latch. The `buggy_code.vhd` file contains code with this error, leading to unpredictable behavior under certain conditions.  The `buggy_code_solution.vhd` file shows the corrected code. 

**Problem:** The original code lacks a complete assignment to the `internal_data` signal in the clock process's `else` branch when `rst` is '0'.  This results in an implicit latch, where `internal_data` retains its previous value instead of being explicitly updated.  This latent condition may be challenging to debug, as it only surfaces under specific input sequences and clock conditions.

**Solution:** The corrected code ensures that `internal_data` is assigned in all branches of the `if` statement within the clock process, eliminating the unintended latch. This results in predictable behavior regardless of the `clk` and `rst` signal activity.

This example highlights the importance of carefully managing signal assignments within VHDL processes to prevent unintended latches and ensure predictable and reliable hardware behavior.