                                                  LAB ACTIVITY 1
                                                  
**Aim:** To successfully install and configure Logisim (or an actively maintained fork like Logisim-evolution) on a local workstation to enable the design and simulation of digital logic circuits.

**Theory:** Logisim is an open-source graphical tool used to design and simulate digital logic circuits. It is widely used in Computer Organization and Architecture (COA) courses because of its intuitive interface and its ability to simulate simple gates as well as complex Central Processing Units (CPUs).Java Runtime Environment (JRE): Logisim is a Java-based application, meaning it is cross-platform (runs on Windows, macOS, and Linux) but requires a JRE to execute.Logisim-evolution: Since the original Logisim development ceased in 2011, "Logisim-evolution" is the modern standard, offering features like FPGA board support, chronograms, and VHDL/Verilog export.

**Procedure:** Follow these steps to complete the installation:
Step 1: Check for Java InstallationOpen your terminal or command prompt.Type java -version.If Java is not installed, download and install the latest JDK (Java Development Kit) from the official Oracle or OpenJDK website.
Step 2: Download the ExecutableNavigate to the official repository (e.g., GitHub for Logisim-evolution).Download the appropriate version for your OS:Windows: .msi or .exe file.macOS: .dmg file.Linux/Generic: .jar file.
Step 3: Installation/ExecutionWindows/macOS: Run the installer and follow the on-screen prompts.JAR File: If using the .jar version, right-click and "Open with Java" or use the command:java -jar logisim-evolution.jar
Step 4: VerificationOnce the application opens, locate the Canvas (center), the Component Tree (left), and the Attribute Table (bottom-left).

**Result:** The installation was successful. Upon launching the application, a blank workspace appeared. To test the functionality, a simple AND gate was placed on the canvas:Input AInput BOutput (AND)Observation000LED remains dark010LED remains dark100LED remains dark111LED glows greenThe simulation responded in real-time as the input pins were toggled using the Poke Tool (the hand icon).

**Conclusion:** The Logisim environment has been correctly configured. This tool will serve as the primary platform for building and testing combinatorial and sequential logic circuits, providing a visual understanding of how data flows through a computer's architecture.

                                                  LAB ACTIVITY 2
                                                  
**Aim:** To design, implement, and simulate Half Adder and Full Adder circuits using Logisim and verify their truth tables.

**Theory:** Adders are fundamental arithmetic circuits in a Computer’s Arithmetic Logic Unit (ALU).
1.Half Adder: A combinatorial circuit that performs the addition of two binary digits (bits).
        It produces two outputs: Sum (S) and Carry (C).
        Sum is calculated using an XOR gate: $S = A \oplus B$
        Carry is calculated using an AND gate: $C = A \cdot B$
        Limitation: It cannot handle a carry-in bit from a previous addition.
2.Full Adder: A circuit that adds three bits: two significant bits (A and B) and a carry bit (Cin) from a previous stage. 
        Sum: $S = A \oplus B \oplus Cin$
        Carry-out (Cout): $Cout = (A \cdot B) + (Cin \cdot (A \oplus B))$
        A Full Adder can be constructed using two Half Adders and an OR gate.

**Procedure:**
1.Half Adder Construction:
    Open Logisim and select the Wiring folder to place two input pins (A, B) and two output pins (Sum, Carry).
    Place an XOR gate for the Sum and an AND gate for the Carry.
    Connect the inputs to both gates and link the gate outputs to the respective output pins.
    Use the Poke Tool to toggle inputs and verify the truth table.
2.Full Adder Construction:
    Place three input pins (A, B, Cin) and two output pins (Sum, Cout).
    Method A (Gates): Use two 3-input XOR gates (or two 2-input XORs) for Sum, and a combination of AND/OR gates for Carry-out.
    Method B (Sub-circuits): Use the "Project -> Add Circuit" feature to create a Half Adder, then drag two instances of it into a new "Full Adder" circuit.
    Connect the components according to the logic expressions.
    Verify the results for all 8 possible input combinations.

**Result/Observation:**
Half Adder Truth Table

| Input A | Input B | Sum (S) | Carry (C) |


  0   0   0   0 

  0   1   1   0  

  1   0   1   0  

  1   1   0   1
  
  | :---: | :---: | :---: | :---: |

Full Adder Truth Table

| A | B | Cin | Sum | Cout |
| :---: | :---: | :---: | :---: | :---: |

| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

**Observation**: The simulation outputs matched the theoretical truth tables exactly. In the Full Adder, when all three inputs were high (1), both Sum and Carry-out were activated.

**Conclusion:** The Half and Full Adder circuits were successfully designed and simulated. We observed that while a Half Adder is sufficient for adding two single bits, a Full Adder is essential for multi-bit addition (cascading) as it accounts for the carry bit from lower-order positions. This experiment confirms the basic building blocks of binary arithmetic in computer architecture.

                                                  _**LAB ACTIVITY 3**_
                                                  
**Aim:** To design and simulate a 4-bit Ripple Carry Adder (RCA) by cascading four Full Adders in Logisim and to verify its binary addition capabilities.

**Theory:** A Ripple Carry Adder is a digital circuit used to add two n-bit binary numbers. It is constructed by connecting n Full Adders in a chain. 
The carry output ($C_{out}$) of each Full Adder is connected to the carry input ($C_{in}$) of the next higher-order Full Adder. The carry "ripples" through the stages from the least significant bit (LSB) to the most significant bit (MSB). For a 4-bit adder, we add two 4-bit numbers $A (A_3 A_2 A_1 A_0)$ and $B (B_3 B_2 B_1 B_0)$ along with an initial carry ($C_{in}$), producing a 4-bit sum $S (S_3 S_2 S_1 S_0)$ and a final carry bit ($C_{out}$).

**Procedure:** 
1. Create a Full Adder Sub-circuit: Open Logisim and create a functional Full Adder circuit. Save this as a sub-circuit to be reused.
2. Arrange Components: In a new main circuit, drag and drop four instances of the Full Adder sub-circuit labeled FA0, FA1, FA2, and FA3.
3. Connect Carries: Connect the carry-out of FA0 to the carry-in of FA1, the carry-out of FA1 to the carry-in of FA2, and so on.
4. Define Inputs: Use two 4-bit input pins (or eight individual 1-bit pins) for numbers A and B. Connect each bit to the corresponding Full Adder stage.
5. Define Outputs: Connect the Sum outputs of each Full Adder to a 4-bit output pin or four individual LEDs. Connect the final carry-out of FA3 to a separate output pin.
6. Simulation: Use the Poke Tool to input binary values and observe if the sum and carry match manual binary addition.

**Result:** The 4-bit Ripple Carry Adder was successfully implemented. During simulation, the following test case was observed:
| Input A | Input B | Carry In | Sum (S3-S0) | Carry Out | Decimal Equivalent |
| 0011 | 0101 | 0 | 1000 | 0 | 3 + 5 = 8 |
| 1111 | 0001 | 0 | 0000 | 1 | 15 + 1 = 16 |
| 1010 | 1100 | 1 | 0111 | 1 | 10 + 12 + 1 = 23 |
The circuit correctly performed addition, though a small propagation delay was simulated as the carry moved through each stage.

**Conclusion:** We successfully designed a 4-bit Ripple Carry Adder. The experiment demonstrated that while the RCA is simple to design by cascading Full Adders, the overall speed of the circuit is limited by the time required for the carry bit to propagate from the first stage to the last. This highlights the importance of carry-lookahead adders for high-speed computing tasks.

                                                  _**LAB ACTIVITY 4**_

**Aim:** To design, implement, and simulate an 8x3 Encoder and a 4x1 Multiplexer (MUX) in Logisim to understand the principles of data compression and data selection in digital systems.

**Theory:** This activity covers two essential combinatorial circuits used in data handling:
1. 8x3 Encoder: An encoder is a circuit that converts an active input signal into a coded binary output. In an 8x3 encoder (Octal-to-Binary), there are eight input lines and three output lines. It identifies which input is "high" and represents that index in 3-bit binary form.
2. 4x1 Multiplexer (MUX): A multiplexer is a data selector that chooses one of several input signals and forwards it to a single output. A 4x1 MUX uses two selection lines ($S_1, S_0$) to determine which of the four data inputs ($D_0, D_1, D_2, D_3$) is connected to the output (Y).

**Procedure:**
1. For the 8x3 Encoder:
   - Create eight input pins (Y0-Y7) and three output pins (A2, A1, A0).
   - Use OR gates to map the inputs to outputs according to the Boolean logic:
     - A2 = Y4 + Y5 + Y6 + Y7
     - A1 = Y2 + Y3 + Y6 + Y7
     - A0 = Y1 + Y3 + Y5 + Y7
   - Verify that activating a single input pin produces the corresponding binary code at the output.

2. For the 4x1 Multiplexer:
   - Create four data input pins (D0-D3), two selection pins (S1, S0), and one output pin (Y).
   - Use NOT gates to invert the selection lines.
   - Use four AND gates to pair each data input with its unique combination of selection bits (e.g., AND1 = D0 · NOT S1 · NOT S0).
   - Use a final OR gate to combine the outputs of the four AND gates into the single output Y.
   - Test the circuit by changing the selection bits and observing which data input is "passed through" to the output.

**Result:** Both circuits were successfully implemented and verified against their respective truth tables.
8x3 Encoder Observation:
| Active Input | Output (A2 A1 A0) |
| Y1 | 001 |
| Y4 | 100 |
| Y7 | 111 |
4x1 Multiplexer Observation:
| S1 | S0 | Output Y |
| 0 | 0 | D0 |
| 0 | 1 | D1 |
| 1 | 0 | D2 |
| 1 | 1 | D3 |
The simulation confirmed that the Encoder effectively coded the input position, while the Multiplexer successfully routed the selected input to the output based on the control signals.

**Conclusion:** Through this activity, we demonstrated how encoders and multiplexers function as the primary building blocks for data routing in a CPU. We concluded that while encoders are used to categorize and prioritize signals, multiplexers are critical for directing data flow between different registers and the ALU.

                                                  _**LAB ACTIVITY 5**_

**Aim:** To observe and verify different microprocessor addressing modes by inspecting CPU registers and memory locations using the GNU Debugger (GDB).

**Theory:** Addressing modes are the methods by which the location of an operand is specified in an instruction. Understanding these modes is critical for optimizing assembly code and debugging low-level software. The primary modes explored in this activity include:
1. Immediate Addressing: The operand is a constant value contained within the instruction itself (e.g., MOV EAX, 10).
2. Register Addressing: The operand is stored in a specific CPU register (e.g., MOV EAX, EBX).
3. Direct/Absolute Addressing: The instruction contains the exact memory address of the operand.
4. Indirect/Register Indirect Addressing: The instruction specifies a register that contains the memory address of the operand (e.g., MOV EAX, [EBX]).
5. Displacement/Indexed Addressing: The address is calculated by adding an offset to a base register.
GDB (GNU Debugger) allows us to pause program execution and use commands like `info registers` and `x` (examine memory) to see how these modes work in real-time.

**Procedure:**
1. Prepare a Source File: Write a simple Assembly program (e.g., in NASM or C) that utilizes various addressing modes.
2. Compile with Debug Symbols: Compile the code using the `-g` flag (e.g., `gcc -g program.c -o program` or `nasm -g -f elf64`) to ensure GDB can read the source lines.
3. Launch GDB: Load the executable into GDB using the command `gdb ./program`.
4. Set Breakpoints: Use the `break main` command to stop execution at the start of the program.
5. Step through Instructions: Use `stepi` or `nexti` to execute one machine instruction at a time.
6. Inspect Operands: 
   - Use `print $rax` or `info registers` to verify Register and Immediate addressing.
   - Use `x/wx &variable` to examine memory for Direct addressing.
   - Use `x/wx $rbp - 8` to verify Displacement/Indexed addressing relative to the base pointer.

**Result:** The behavior of various addressing modes was observed in the GDB environment. The following observations were recorded during the debug session:
| Addressing Mode | Example Instruction | GDB Observation |
| Immediate | mov $0x5, %eax | Register EAX changed to 0x5 immediately. |
| Register | mov %eax, %ebx | Value 0x5 was copied from EAX to EBX. |
| Direct | mov 0x4010, %eax | EAX was loaded with the value stored at memory 0x4010. |
| Indirect | mov (%rbx), %eax | EAX was loaded with value at the address held in RBX. |
| Displacement | mov 4(%rbp), %eax | EAX loaded with value at address (RBP + 4 bytes). |
The values in the registers updated exactly as predicted by the architectural logic of each mode.

**Conclusion:** Through this lab, we successfully utilized GDB to visualize how the CPU fetches operands. We concluded that different addressing modes provide a balance between instruction length and the flexibility of accessing complex data structures like arrays and pointers in memory.

                                                  _**LAB ACTIVITY 6**_

**Aim:** To design and implement a 4-bit Common Bus System using multiplexers and tri-state buffers in Logisim to understand how data is transferred between multiple registers.

**Theory:** A Common Bus System is a communication pathway used to transfer data between various registers, the ALU, and memory within a computer. Instead of having separate wires connecting every register to every other register, a single "bus" is shared.
To prevent data collisions, the system uses two primary methods:
1. Multiplexers (MUX): A MUX selects one register's output at a time based on selection lines and places that data onto the bus.
2. Tri-state Buffers: These act as electronic switches. When a specific register's "Enable" signal is active, it connects to the bus; otherwise, it remains in a high-impedance state (disconnected).
In this lab, we focus on a bus connecting four registers (Register A, B, C, and D), where selection lines determine which register currently controls the bus lines.

**Procedure:**
1. Create Registers: Place four 4-bit registers in the Logisim workspace and label them Reg A, Reg B, Reg C, and Reg D.
2. Setup the Multiplexer: Place a 4x1 Multiplexer (with a data bit width of 4). Connect the output of each register to one of the four inputs of the MUX.
3. Configure Selection Lines: Add a 2-bit input pin to the selection lines of the MUX. This will act as the "Bus Selector."
4. Connect the Bus: The output of the MUX represents the Common Bus. Connect this output to a 4-bit Hex Digit Display or a set of LEDs to visualize the data on the bus.
5. Verification: Load different binary values into each register (e.g., Reg A = 0001, Reg B = 0010, etc.). Toggle the selection lines and observe how the data on the Common Bus changes to match the selected register.
6. Data Loading: Connect the bus back to the inputs of the registers through a "Load" enable gate to demonstrate how data can be transferred from the bus into a different register.

**Result:** The Common Bus System was successfully simulated. The following observations were made regarding data transfer:
| Selection Lines (S1, S0) | Selected Register | Data on Bus |
| 00 | Register A | Data from Reg A |
| 01 | Register B | Data from Reg B |
| 10 | Register C | Data from Reg C |
| 11 | Register D | Data from Reg D |
The simulation confirmed that only the data from the selected register appeared on the bus, and no data interference occurred between the registers.

**Conclusion:** We successfully designed a 4-bit Common Bus System. This experiment demonstrates the efficiency of using a shared bus architecture to reduce the number of physical wires required in a CPU, while highlighting the necessity of selection logic to manage data flow between components.
