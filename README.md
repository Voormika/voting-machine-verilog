# voting-machine-verilog
This project implements a digital voting machine in Verilog HDL, designed for simulation on platforms like EDA Playground and targeting hardware like the           ZedBoard (Zynq-7000 SoC). It demonstrates a mode-based voting system using push buttons and LEDs for input and output. The design emphasizes button debouncing, vote logging, and result display.

**Purpose**:
    To design and simulate a simple, debounced, mode-controlled voting machine capable of:
    ->Recording votes for four candidates
    ->Displaying vote counts using LEDs
    ->Ensuring only intentional button presses are registered as valid votes

**Modules**:
    **Button Control**: Uses a 31-bit counter to detect a long-enough button press. Prevents multiple votes from being registered during a single press
    **Vote Logger**: Registers one vote per valid button press per candidate. Keeps a tally of votes for each of the four candidates. Resets all tallies when reset       is active
    **Mode Control**: Two Modes:-
      Mode 0 (Voting): Accepts votes and flashes LEDs
      Mode 1 (Result/Telling): Displays the vote count for a selected candidate
    **LED indicators**:
      In Mode 0: All LEDs flash when a vote is cast
      In Mode 1: LED output displays vote count in binary
    **Voting Machine** (Top Module): Integrates all submodules- buttonControl, voteLogger, and modeControl. Handles clock, reset, mode selection, and candidate           button inputs

**Development Environment**
      Hardware Target: ZedBoard (Zynq-7000 SoC)
      Simulation Platform: EDA Playground
      Languages Used: Verilog

**The testbench**: 
      Provides input stimulus for clock, reset, mode, and candidate buttons.Tests both voting and result display functionalities. Monitors LED outputs to verify 
      correct behavior

**Timing Considerations**:
      A vote is registered only when a button is pressed continuously long enough (determined by counter reaching value 10). This debouncing mechanism ensures     
      accidental or noisy inputs are ignored

A vote has been cast (Mode 0)
Vote counts (Mode 1)
LEDs display binary values due to lack of 7-segment or alphanumeric display

**Results**:
      Successfully simulated and verified:
      Correct vote logging
      Debounced input handling
      Binary vote count display
      Ensured smooth mode switching and accurate vote tracking
