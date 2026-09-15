# 8-Bit General-Purpose Processor

This project involved the design and implementation of a simple 8-bit general-purpose processor using digital logic and FPGA hardware.

The processor combines two 8-bit storage registers, a finite state machine (FSM), a 4-to-16 decoder, and an Arithmetic Logic Unit (ALU). The control system generates a 16-bit microcode signal that determines which arithmetic or logical operation is performed by the ALU.

The final system processes two 8-bit inputs and produces an 8-bit output that is displayed in hexadecimal using seven-segment displays.

---

## System Architecture

The processor is composed of four main components:

- **Two 8-bit Registers** – store input values A and B on the rising edge of the clock.
- **Finite State Machine (FSM)** – cycles through nine states and controls the processor's operation sequence.
- **4-to-16 Decoder** – converts the FSM state into a 16-bit microcode signal.
- **Arithmetic Logic Unit (ALU)** – performs arithmetic and Boolean operations based on the selected microcode.

The FSM sends its current state to the decoder, which generates the appropriate control signal for the ALU. The ALU then performs the selected operation on the two stored 8-bit inputs.

### Processor Block Diagram

<img width="1557" height="587" alt="image" src="https://github.com/user-attachments/assets/69333309-66ad-4353-8ea1-2ee32d17c07b" />

---

## Arithmetic Logic Unit

The ALU accepts two 8-bit inputs and a 16-bit microcode control signal.

The initial ALU implementation supports nine arithmetic and logical operations, including addition, subtraction, XOR, and other Boolean operations.

The resulting 8-bit output is split into two 4-bit values so it can be displayed as a two-digit hexadecimal value on the FPGA's seven-segment displays.

---

## Control Unit

The processor uses a finite state machine and decoder to control the ALU.

The FSM cycles through nine states using the clock signal. Each state is passed to the 4-to-16 decoder, which activates the corresponding microcode signal.

This allows the processor to automatically cycle through different ALU operations as the FSM changes state.

### FSM and Decoder Components

<img width="219" height="110" alt="image" src="https://github.com/user-attachments/assets/fb2026a0-e87f-4d5b-8c08-c2a4cad0073b" />
<img width="277" height="109" alt="image" src="https://github.com/user-attachments/assets/c0079b32-a7ca-440a-a40e-1530421e9ab9" />

---

## Modified ALU

The processor was also extended with a modified ALU that supports additional operations such as:

- Incrementing an input
- Logical right shifts
- Bit rotations
- Minimum-value comparison
- XOR operations
- Bit-order reversal
- Modified addition operations

This demonstrated how the ALU functionality could be expanded while continuing to use the same FSM and microcode-based control structure.

The modified ALU still produces an 8-bit result that is displayed in hexadecimal on the FPGA.

---

## FPGA Implementation

The complete processor was implemented and tested on FPGA hardware.

The final system displayed:

- FSM state information
- Processor output
- Hexadecimal ALU results
- Control-related values using seven-segment displays

### FPGA Demonstration

<img width="572" height="669" alt="image" src="https://github.com/user-attachments/assets/ad4f79b7-8d78-4931-94a3-38d2d50d8c7c" />

---

## Testing and Verification

The design was verified using component truth tables, block schematics, expected outputs, and FPGA testing.

During hardware testing, a one-clock-cycle delay was observed between the control-unit update and the ALU output. This occurs because the control unit updates first, and the resulting control signal reaches the ALU on the following rising clock edge.

This demonstrated the importance of timing and synchronization when designing sequential digital systems.


## FSM-Controlled Comparison

A third version of the design used the FSM output directly as part of the processor's comparison logic.

Instead of performing only traditional arithmetic operations, this implementation compared values against the FSM-generated output and produced either a `y` or `n` result.

The result was then converted for display on a seven-segment display.

This showed how the processor's control logic could be modified to perform state-dependent operations.

---

## What I Learned

Through this project, I gained hands-on experience with:

- Digital system design
- Arithmetic Logic Units
- Finite State Machines
- Registers and sequential logic
- Decoders and microcode
- FPGA implementation
- Clock-driven digital systems
- Binary and hexadecimal representation
- Hardware testing and debugging
- Timing and synchronization
- Modular processor design

---


## Technologies

**Digital Design:** ALU, FSM, Registers, Decoders, Microcode  
**Hardware:** FPGA, Seven-Segment Displays  
**Concepts:** Sequential Logic, Combinational Logic, Binary Arithmetic, Boolean Logic


