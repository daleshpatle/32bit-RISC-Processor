# 32-bit RISC Processor Verification using UVM

## Overview

This project implements a 32-bit pipelined RISC processor in Verilog and verifies its functionality using the Universal Verification Methodology (UVM). The processor supports a simplified instruction set and a five-stage pipeline, while the UVM environment provides reusable, scalable, and modular verification components.

---

## Features

### Processor
- 32-bit RISC architecture
- Five-stage pipeline
  - Instruction Fetch (IF)
  - Instruction Decode (ID)
  - Execute (EX)
  - Memory Access (MEM)
  - Write Back (WB)
- Two-phase clock architecture
- 32 General Purpose Registers
- 1024 × 32-bit Data/Instruction Memory
- Arithmetic and Logical Operations
- Load/Store Instructions
- Branch Instructions
- Halt Instruction

### Supported Instructions

| Instruction | Description |
|------------|-------------|
| ADD | Addition |
| SUB | Subtraction |
| AND | Bitwise AND |
| OR | Bitwise OR |
| SLT | Set Less Than |
| MUL | Multiplication |
| ADDI | Add Immediate |
| SUBI | Subtract Immediate |
| SLTI | Set Less Than Immediate |
| LW | Load Word |
| SW | Store Word |
| BEQZ | Branch if Equal to Zero |
| BNEQZ | Branch if Not Equal to Zero |
| HLT | Halt Processor |

---

## UVM Verification Environment

The verification environment consists of:

- Interface
- Sequence Item
- Sequence
- Sequencer
- Driver
- Monitor
- Scoreboard
- Agent
- Environment
- Test
- Top Testbench

The driver loads instructions into the processor memory, while the monitor observes processor activity. The scoreboard compares the expected processor behavior with the actual results.

---

## Directory Structure

```
project/
│
├── rtl/
│   ├── processor.sv
│   └── processor_wrapper.sv
│
├── interface/
│   └── proc_if.sv
│
├── uvm/
│   ├── transaction.sv
│   ├── sequence.sv
│   ├── sequencer.sv
│   ├── driver.sv
│   ├── monitor.sv
│   ├── scoreboard.sv
│   ├── agent.sv
│   ├── env.sv
│   ├── test.sv
│
├── tb/
│   └── top.sv
│
└── README.md
```

---

## Verification Flow

```
Sequence
    │
    ▼
Sequencer
    │
    ▼
Driver
    │
    ▼
Processor DUT
    │
    ▼
Monitor
    │
    ▼
Scoreboard
```

---

## Simulation

Compile the RTL and UVM files using your preferred simulator.

Example (QuestaSim):

```
vlog rtl/*.sv
vlog interface/*.sv
vlog uvm/*.sv
vlog tb/top.sv

vsim top
run -all
```

Example (Cadence Xcelium):

```
xrun -uvm rtl/*.sv interface/*.sv uvm/*.sv tb/top.sv
```

---

## Expected Result

Example Program:

```
ADDI R1, R0, 10
ADDI R2, R0, 20
ADD  R4, R1, R2
HLT
```

Expected Register Values

| Register | Value |
|----------|------:|
| R1 | 10 |
| R2 | 20 |
| R4 | 30 |

The scoreboard reports **PASS** if the processor produces the expected output.

---

## Future Enhancements

- Hazard Detection Unit
- Data Forwarding
- Pipeline Stall Logic
- Functional Coverage
- Constrained Random Instruction Generation
- Reference Model
- Assertion-Based Verification (SVA)
- Branch Prediction
- Code Coverage
- Regression Automation

---

## Tools Used

- Verilog
- SystemVerilog
- UVM
- QuestaSim / Xcelium
- Git
- GitHub

---

## Author

**Dalesh Patle**

- Front-End VLSI Verification Engineer
- M.Tech (Microelectronics, Photonics and RF)
- IIT Guwahati

---

## License

This project is developed for educational and learning purposes.
