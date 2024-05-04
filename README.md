# DIGITAL VLSI SOC DESIGN AND PLANNING
# DAY-1:
## Incepation of open-source EDA, OpenLANE and Sky130 PDK
### How to talk to computers
#### ARDUINO LEONARDO
* Arduino is an open-source electronics platform based on easy-to-use hardware and software.The Arduino Leonardo is a microcontroller board based on the ATmega32u4. It has 20 digital input/output pins (of which 7 can be used as PWM outputs and 12 as analog inputs), a 16 MHz crystal oscillator, a micro USB connection, a power jack, an ICSP header and a reset button.
![Screenshot 2024-04-30 222547](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/96e22bc3-d86a-43aa-a1d9-e0ac788f4e63)

A processor (CPU) is the logic circuitry that responds to and processes the basic instructions that drive a computer. The CPU is seen as the main and most crucial integrated circuitry (IC) chip in a computer, as it is responsible for interpreting most of computers commands. The purpose of this course is that to know about the designing and planning of the chip mentioned in the above marked circle.
* Processor has interface arround it, those interafaces are:
   * Direcct I2C, direct QSPI, GPIO8-14, PWM4-5,GPIO0-7,PWD0-3
   * JTAG-UART,FTDI,QSPI1-Flash, I2C0-EEPROM
   * VCC/GND, ADC(QSP13), MUXED WITH GPIOs, SDRAM chip.
![Screenshot 2024-04-30 223609](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/42928d93-7c39-4ca8-9aa5-e534353d24df)

### Introduction to QFN-48 Package, chip, pads, core, die and IPs
1. QFN-48 Package:
     * A QFN 48 package is a 48-lead, 7x7 mm, leadless, plastic package for integrated circuits with a 0.5 mm pitch.
     * QFN stands for Quad Flat No Lead.
     * These packages are small, low profile, and have a thermal pad for good thermal performance.
![Screenshot 2024-04-30 223838](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/e48c446f-ca47-4df3-bb61-866de2f08eff)

2. Chip: It process the data to complete the required task.![Screenshot 2024-04-30 224049](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/0cd0fd6f-f81d-4c14-bcac-de6f90b54800)

3. Pads: It is the thing that can send the signal inside the chip and vice-versa.
4. Core: The area in which all digital logics are present.
5. Die is the boundary around the chip.
![Screenshot 2024-04-30 224642](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/a051ec07-1009-4789-b2bc-ac55a7b412f1)

##### Foundry IPs and Macros:
  * basically foundry is the factory of chip manufacturing, the designers are communicated with the foundry by the interface files. IPs are intellectual Properties which are DAC,ADC, PLL and SRAM in the chip.
  * Macros are pure digital logic present in the chip, which are SPI and RISCV SoC.
![Screenshot 2024-05-01 195938](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/784f4ed8-048c-468f-bc69-10110257c199)

### Introduction to RISC-V
* RISC-V Instruction Set Architecture: It is a language which we are talk to computers. Consider, C program is compiled in its Assembly language program, this is converted into Machine language program (Binary), these binary bits are executed in the layout and we will get the required output.
* the another way of interface is Hardware Discriptive Language (HDL). ISA is implemented on RTL, then RTL to layout (Standard PNR).
![Screenshot (4)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/f37e74a8-1ec2-4d59-a744-b989f634ec32)


### From Software Applications to Hardware
Application software enters into block called System software, system software converts the application program into binary language.
The major components of the sysyem software are:
  * OS: It handles the IO operations, allocates the memory and low level system functions. Major part of OS is that App is converted into Assembly language program and then it is coverted into binary language program.
  * Compiler: It converts the output of OS, that is functions of C, C++, Java etc. into the instructions depending on the type of hardware.
  * Assembler: It takes instructions and converts into respective binary numbers, this is basiucally called as machine language program.
These binary language is fed to the hardware and it understands the execution and output as respect to the input.
![Screenshot (5)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/e929eb4a-e40c-4794-9dc0-25e8d59ed2b2)

Instructions acts as the Abstract interface between the C language and hardware, it is also called as Instruction Set Architecture or Architecture of the computer. This represents the architecture of Hardware.
Another interface between instructions and hardware is called HDL. The instructions are implemented in in RTL and it is synthesized in Netlist and finally implementing the Netlist as Physical Design or Hardware.
![Screenshot (6)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/07776bad-95fb-49ab-af48-b7d864edc36f)

### SoC design and OpenLANE
#### Introduction to all components of open-source digital ASIC design
![Screenshot (7)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/faf1055b-b71c-4365-8a21-a303f1642168)
* Register Transfer Level (RTL): It is a vital part of circuit design, and its verification ensures that a design meets all system requirements and specifications. RTL design flow can be used to assemble the top-level design, instantiate IP, or create modules.
* PDK DATA: A PDK is a "Process Design Kit" - it's a set of libraries and associated data (model files, physical verification rule files, control files for various tools) to allow you to design in a particular technology. A flow is far more generic than that it could mean many things.
* Electronic Design Automation (EDA) tools are used in ASIC design for tasks such as design, verification, and manufacturing.
  * QFlow,OpenRoad, OpenLANE, Spice Simulator, SIC, Magic etc. these are some ASIC design tools.

![Screenshot (8)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/e6c2671b-04af-43a7-a140-e2ba4260cc98)

#### Simplified RTL2GDS flow
![Screenshot (9)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/5f8866f7-9fd9-4654-9e04-442deedef135)
 * Synthesis
 * Floor and Power planning
 * Placement
 * Clock tree synthesis
 * Routing
 * Sign off
#### Introduction to OpenLANE and Strive chipsets
##### OpenLANE ASIC flow 
   * Main goal:
     * Produce clean GDSII with no-human in the loop
   * Clean means:
     * No LVS voilations
     * No DRC violations

Strive chipsets:

![Screenshot (10)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/aca1dcbd-6a78-4b95-9761-dcd8a29758a0)

#### Introduction to OpenLANE detailed ASIC design flow
![Screenshot (11)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/cffb124a-e373-498f-8109-caea7d874fe8)
The above block diagram shows the detailed design flow of ASIC.
### Preparation and Synthesis results:
![preparation successfully](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/ea75981c-6c51-4f5f-8dbf-531d8f69bdf6)
![Sythesis successful](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/0adb755f-2cc1-4b18-9bb7-8289ea9e6b9c)

# DAY-2:
### Good floorplan vs bad floorplan and introduction to library cells: 
  * Chip floorplanning considerations:
    * define Width and Height of the core and die
      
       * Utilizaton factor=(Area occupied by netlist)/(total area of the core)
      
       * Aspect ratio=Height/width
      
    * define locations of preplaced cells
    * Surround pre-placed cells with decoupling capacitors
    * Power planning
    * Pin placement
    * Logical cell placement blockage
    * Floor plan
    * Floorplan Layout in magic

![layout](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/e69d8319-198f-4067-a782-9099fa14c2cc)
  
  * Library Bindings and Placements:
    * Bind netlist with physical cells (In Libarary)
    * Placement
    * Optimize placement
      * This is the stage we estimate wire length and capacitance and based on that, insert repeaters.
    * Library characterization and modelling
  
  Placement:

![Placement](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/1e44f30e-3331-4d88-a689-d311bd40f1b8)

  * Cell design and charaterization flows:
     * Cell design flow:
    
    ![Screenshot 2024-05-04 161027](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/354be99d-2ebb-4e5b-8327-7c0bbb672664)
    
     * Characterization flow:
       
    ![Screenshot (12)](https://github.com/kirankumarmn21/nasscom-vsd-workshop/assets/168124790/d3088b8e-cc47-4959-8e85-ef1a24b19c6f)
