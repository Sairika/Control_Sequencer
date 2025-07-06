# Modified SAP Architecture Implementation in Logisim

## Overview

This project implements a Modified Simple-As-Possible (SAP) processor architecture using Logisim-2. The design demonstrates fundamental computer architecture concepts including instruction fetch-decode-execute cycles, memory operations, and arithmetic logic unit (ALU) functionality.

## Project Details

- **Course**: ETE 404 - VLSI Technology Sessional
- **Institution**: Chittagong University of Engineering and Technology (CUET)
- **Department**: Electronics and Telecommunication Engineering
- **Implementation Tool**: Logisim-2
- **Date**: September 17, 2024

## Architecture Features

### Instruction Set Architecture (ISA)

The Modified SAP processor supports 7 fundamental instructions:

| Instruction | Opcode | Description |
|-------------|--------|-------------|
| LDA | 0001 | Load data from RAM into the Accumulator register |
| LDB | 0110 | Load data from RAM into register B |
| STR | 0101 | Store ALU output into RAM |
| ADD | 0010 | Add registers A and B |
| SUB | 0011 | Subtract register B from register A |
| AC OUT | 0100 | Load value of register A into the output register |
| HLT | 1111 | Halt the program |

### Key Components

- **Program Counter (PC)**: Manages instruction sequencing
- **Memory Address Register (MAR)**: Holds memory addresses
- **Instruction Register (IR)**: Stores current instruction
- **Accumulator (A Register)**: Primary data register
- **B Register**: Secondary data register for ALU operations
- **Arithmetic Logic Unit (ALU)**: Performs arithmetic and logic operations
- **Output Register**: Stores results for output
- **SRAM**: Program and data memory
- **Control Sequencer**: Manages timing and control signals

## Implementation Details

### Fetch-Execute Cycle

The processor follows a standard three-phase cycle:

1. **Fetch Phase**:
   - T1: Program counter outputs address to MAR
   - T2: RAM outputs instruction to Instruction Register
   - T3: Program counter increments

2. **Decode Phase**:
   - Combinational logic decodes instruction opcode
   - Control signals are generated accordingly

3. **Execute Phase**:
   - Instruction-specific operations are performed
   - Timing varies by instruction type (T4-T6)

### Memory Operations

- **LDA/LDB**: Load operations from memory to registers
- **STR**: Store ALU results to memory
- All memory operations use the MAR for address specification

### Arithmetic Operations

- **ADD**: Performs addition of registers A and B
- **SUB**: Performs subtraction (A - B)
- Results are available at ALU output

## File Structure

```
├── Modified_SAP_Architecture.circ    # Main Logisim circuit file
├── README.md                         # This file
├── docs/
│   └── project_report.pdf           # Detailed project documentation
└── examples/
    └── sample_programs/              # Example programs for testing
```

## Getting Started

### Prerequisites

- Logisim-2 (or compatible version)
- Basic understanding of digital logic and computer architecture

### Running the Simulation

1. Open the `.circ` file in Logisim
2. Load instructions and data into memory using the debug interface
3. Set the program counter to 0000
4. Use the clock input to step through instruction execution
5. Monitor register contents and memory states through the interface

### Example Program

```assembly
Address 0000: LDA 2    ; Load value from address 2 into register A
Address 0001: LDB 1    ; Load value from address 1 into register B
Address 0002: ADD      ; Add A and B
Address 0003: AC OUT   ; Output result
Address 0004: HLT      ; Halt execution

Data:
Address 0001: 0000 0010 (decimal 2)
Address 0002: 0000 0011 (decimal 3)
```

## Control Signals

The processor uses various control signals for component coordination:

- **MI**: MAR Input Enable
- **CO**: Program Counter Output Enable
- **RO**: RAM Output Enable
- **II**: Instruction Register Input Enable
- **CE**: Program Counter Enable (increment)
- **AI**: Accumulator Input Enable
- **BI**: B Register Input Enable
- **EO**: ALU Output Enable
- **SU**: Subtraction Enable
- **OI**: Output Register Input Enable
- **AO**: Accumulator Output Enable
- **RI**: RAM Input Enable (Write)

## Testing and Verification

The implementation has been tested with various instruction sequences to verify:

- Correct instruction fetch and decode
- Proper memory read/write operations
- Accurate arithmetic operations
- Sequential program execution
- Halt functionality

## Learning Outcomes

This project demonstrates:

- Computer architecture fundamentals
- Instruction set design principles
- Digital logic implementation
- Sequential circuit design
- Memory organization concepts
- Control unit design

## Future Enhancements

Potential improvements could include:

- Extended instruction set (multiplication, division, branching)
- Larger memory capacity
- Multiple addressing modes
- Interrupt handling capabilities
- Pipeline implementation

## Author

**Sabrina Sultana**  
Student ID: 1908034  
Department of Electronics and Telecommunication Engineering  
Chittagong University of Engineering and Technology

## Acknowledgments

Special thanks to **Arif Istiaque Rupom**, Lecturer, Department of ETE, CUET, for guidance and supervision throughout this project.

## License

This project is created for educational purposes as part of the VLSI Technology Sessional course at CUET.

---

*For detailed implementation procedures and timing diagrams, please refer to the project documentation.*
