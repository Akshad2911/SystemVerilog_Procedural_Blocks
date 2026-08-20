# SystemVerilog_Procedural_Blocks

---

This repository demonstrates the use of SystemVerilog procedural blocks — `always_comb`, `always_ff`, and `always_latch`. The examples focus on clearly describing combinational, sequential, and latch-based hardware while following recommended SystemVerilog coding practices.

---

## Description

SystemVerilog provides specialized procedural blocks that improve RTL design clarity and help tools identify the intended hardware structure.

The three blocks covered in this repository are:

- `always_comb` — Used for combinational logic
- `always_ff` — Used for sequential logic such as flip-flops and registers
- `always_latch` — Used for intentional level-sensitive latch logic

---

## Features

- Combinational logic using `always_comb`
- Sequential logic using `always_ff`
- Level-sensitive latch using `always_latch`
- Blocking assignments (`=`) for combinational logic
- Non-blocking assignments (`<=`) for sequential and latch logic
- Automatic sensitivity handling
- Hardware-intent-based SystemVerilog coding

---

## Procedural Blocks

### 1. `always_comb`

Used to describe combinational logic.

```systemverilog
always_comb begin
    if (sel)
        y = b;
    else
        y = a;
end
````

**Typical applications:**

* Multiplexers
* Decoders
* Encoders
* ALUs
* Combinational control logic

### 2. `always_ff`

Used to describe sequential logic.

```systemverilog
always_ff @(posedge clk or posedge reset) begin
    if (reset)
        q <= 1'b0;
    else
        q <= d;
end
```

**Typical applications:**

* Flip-flops
* Registers
* Counters
* Shift registers
* Sequential state elements

### 3. `always_latch`

Used when latch behavior is intentionally required.

```systemverilog
always_latch begin
    if (enable)
        q <= d;
end
```

When `enable` is high, the latch follows the input. When `enable` is low, the previous value is retained.

**Typical applications:**

* Level-sensitive storage
* Control circuits
* Specific latch-based architectures

## Comparison

| Feature      | `always_comb`       | `always_ff`            | `always_latch`          |
| ------------ | ------------------- | ---------------------- | ----------------------- |
| Hardware     | Combinational logic | Flip-flop/Register     | Latch                   |
| Sensitivity  | Automatic           | Clock/event based      | Automatic               |
| Assignment   | Blocking `=`        | Non-blocking `<=`      | Non-blocking `<=`       |
| Storage      | No                  | Yes                    | Yes                     |
| Main Purpose | Logic calculation   | Edge-triggered storage | Level-sensitive storage |

## Coding Guidelines

### Combinational Logic

Use:

```systemverilog
always_comb
```

with blocking assignments:

```systemverilog
=
```

Ensure that outputs are assigned on every possible path to avoid unintended latch inference.

### Sequential Logic

Use:

```systemverilog
always_ff
```

with non-blocking assignments:

```systemverilog
<=
```

Use an explicit clock edge such as:

```systemverilog
@(posedge clk)
```

### Latch Logic

Use:

```systemverilog
always_latch
```

when latch behavior is intentional. Do not use incomplete assignments accidentally.

---

## Tools

The examples can be simulated using:

* EDA Playground
* QuestaSim / ModelSim
* Vivado
* Xilinx Simulator (XSim)
* Verilator
* Other SystemVerilog-compatible simulators

---

## Learning Objective

The purpose of this repository is to understand how SystemVerilog procedural blocks express different hardware structures and how they improve RTL coding compared with traditional Verilog `always` blocks.

## Applications

These coding styles are widely used in:

* RTL Design
* FPGA Design
* ASIC Design
* Digital Logic Design
* VLSI Design
* Hardware Verification
* System-on-Chip (SoC) Development

---

⭐ If you find this repository useful, consider giving it a star.
