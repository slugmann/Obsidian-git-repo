---
date: 2019-09-19
tags:
  - MTRN/3026
status: Complete
Relevant Docs:
  - "[Basic_Ladder_Programming](Attachments/Basic_Ladder_Programming.pdf)"
  - "[PLC](Attachments/PLC.ppt)"
Relevant Questions:
  - "[Tut-7 1](Attachments/Tut-7%201.pdf)"
Relevant Notes:
  - "[PLC (Programmable Logic Contoller)s](../../../Distilled%20Notes/PLC%20(Programmable%20Logic%20Contoller)s.md)"
Practical Docs: "[Week 7 (Induction Motor)](Attachments/Week%207%20(Induction%20Motor).pdf)"
Relevant Links: https://instrumentationblog.com/logic-gates-in-plc-ladder-logic/
---
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
# Maths and Distilled Info
---



# Conceptual Info
---

# What is a PLC (Programmable Logic Controller)
PLC's are special purpose computer (Usually a microprocessor or microcontroller) aimed at implementing control solutions. Typically they are designed with the intent that their software never or rarely needs updating, ideally design in a way that is low maintenance.
**Overview:**
- For use where large computer systems would be ineffective, inefficient, or difficult
- Robust, suitable for use in industrial systems (From keypads to motor control)
- Many different forms with many different Features (e.g. Teensy 4.0, ATMega328P)

## Relative Power of PLCs
#todo Check how up to date this data is

| Size   | IO                      | Memory                                    | Description                                                                                            |     |
| ------ | ----------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------ | --- |
| Small  | Up to 128 I/O Channels  | Up to 2Kb                                 | Capable of providing simple to advanced levels of machine control                                      |     |
| Medium | Up to 2048 I/O Channels | Up to 32Kb                                | A larger version of the Small PLCs, likely similar performance                                         |     |
| Large  | up to 8192 I/O Channels | Up to 740Kb (Keep in mind its just a PLC) | Can control individual production processes (or an entire plant? If its a plant for fucken ants maybe) |     |

# Control Hierarchy of PLCs
![Pasted image 20230919223736](Attachments/Pasted%20image%2020230919223736.png)

PLC Systems typically communicate with a higher level of control. This can be another computer, or a human.

# Major Components
![Pasted image 20230919223847](Attachments/Pasted%20image%2020230919223847.png)

| Component          | Description                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Power Supply       | Provides voltage needed to run primary PLC Components                                                                              |
| I/O Modules        | Provide Signal Conversion and isolation between the internal logic-level signals inside the PLC and the device's high level signal. |
| Processor          | Brain. Processes data, gives and executes commands to govern the activity of the PLC                                               |
| Programming Device | Used to program the PLC to give it instructions. **Can be a handheld unit with an LED/LCD Display, or compatible computer**.       |

# I/O Circuits
- *Main Purpose:* Condition the various signals received from or sent to the external input and output devices.
- Connects to **external field devices**.
- *Inputs* **convert signals from analog to digital** so the PLC can interpret.
- *Outputs* **convert logic signal to suitable output levels** either **analog (DAC)** or **digital (Logic High and Low)**

**Different Type of I/O Circuits**
1. *Pilot Duty Outputs*
	- Typically used to **dribe high current electromagnetic loads,** such as solenoids, relays, valves and motor starters
	- Loads are **highly inductive** and exhibit a large inrush current
	- *Pilot Duty* output should be capable of withstanding an inrush current **ten times the rated load** for a short period of time **without failure**.
2. *General Purpose*
	- Usually **low voltage low current** 
	- used to drive indicating lights and other **non inductive loads**
	- Noise suppression may or may not be included
3. *Discrete Input*
	- Used to sense the **status of limit switches, push buttons and other discrete sensors**
	- Noise suppression **VERY IMPORTANT** to prevent false positives.
4. *Analog I/O*
	- Sense **OR** Drive analog signals
	- Standard analog input signals range from **4-20mA; 0-10V**
	- Can be used to drive devices like voltmeters through the use of **transducers**
	- Standard analog output signals range from **4-20mA; 0-5V; and potentially 0-10V for a larger PLC.**
5. *Special Purpose I/O*
	- Used to interface PLCs to **specific types of circuits** (servomotors, stepper motors, PID loops
	- Consider **motor drivers**

# Processors
Processor Module contains the PLC's **microprocessor**, supporting circuitry, and its **memory system**.
*Its main function is to analyze data coming from inputs, make decisions based on the user defined control program, and return signals through outputs.*

## Memory Map Organization
**Memory** has two parts, **system** memory and **application** memory.
![Pasted image 20230920001056](Attachments/Pasted%20image%2020230920001056.png)

## Memory Designs

| Memory Type  | Read/Write?                       | Examples                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------ | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Volatile     | Read/Write                        | **RAM** (Random Access Memory, Read/Write)  Random Access means any location in the memory can be accessed or used. RAM is used for both user memory and storage memory.                                                                                                                                                                                                                  |
| Non-Volatile | Read Only                         | **ROM** (Read Only Memory) Cannot be changed, placed there by the manufacturer for internal use and operation of the PLC.                                                                                                                                                                                                                                                                 |
| Non-Volatile | Read Only, initial write possible | **PROM** (Programmable Read Only Memory)  Can be written into only once after being received from the manufacturer, achieved by pulses of currents. *The current melts the fusible links in the device preventing reprogramming*.                                                                                                                                                         |
| Non-Volatile | Read Only, can be erased          | **EPROM** (Erasable Programmable Read Only Memory) Ideally suited to semi-permanent storage or when added security is needed to prevent unauthorized change. *A quartz window over a silicon material that contains the electronic ICs. This window is normally covered by an opaque material but when the material is removed and the circuitry exposed to UV the memory can be erased.* |
| Non-Volatile | Read and Reprogram?                | **EEPROM** (Electrically Erasable Programmable Read Only Memory) (E$^2$PROM) Can be programmed using a standard programming device and can be erased with a signal to the erase pin. Usually used as a non-volatile backup so that if power is lost a copy can be downloaded from the EEPROM into the RAM.                                                                                                       |


# PLC Operation
![Pasted image 20230920003704](Attachments/Pasted%20image%2020230920003704.png)
While the PLC is running, the scanning process includes these four phases, which are repeated continuously for each cycle of operation (do they mean clock cycles? #todo )

The time taken to do all this is called  SCAN TIME. Heavily dependent on the control program and how long it takes to solve it, the amount of memory taken up by the control program and the type of instructions. 

**Time can vary between 1ms to 100ms**.




## DC VS AC Inputs/Outputs

### For DC Input
![Pasted image 20230919225219](Attachments/Pasted%20image%2020230919225219.png)

### For AC Input
![Pasted image 20230919225508](Attachments/Pasted%20image%2020230919225508.png)

### DC Output
![Pasted image 20230919232140](Attachments/Pasted%20image%2020230919232140.png)
- Logic circuits, feed into
- A [Opto-Isolator](../../../Distilled%20Notes/Opto-Isolator.md) to reduce noise and prevent damage to the processor from transient spikes
- And an amplifier, to make out isolated signal large enough to actually control external devices.

## Analog (Continuous) Input
- Signal of <4.0mA equates to **Zero**
- Signal of 20mA equates to **2048** for an 11bit Input ($2^{input bits}$)
*The reason the starting point is 4mA is for safety. If the instrument fails or the signal cable is damaged, the current falls to zero and the PLC can set of alarms/warnings immediately.* (Not possible for signals that pass through zero volts)

## Digital (Discrete) Input
- Represented as ON or OFF (HIGH or LOW, 1 or 0)
Pushbuttons? [Circuit Symbols](../../../Distilled%20Notes/Circuit%20Symbols.md)
![Pasted image 20230920000442](Attachments/Pasted%20image%2020230920000442.png)

# [Ladder Logic](../../../Distilled%20Notes/Ladder%20Logic.md)
The three most common instructions in ladder logic:
![Pasted image 20230920010023](Attachments/Pasted%20image%2020230920010023.png)

- Simple programming """""language"""""
- Illustrated by a simple electrical relay - (Relay logic preceded PLC's)

**A simple relay circuit, power circuit for a field motor**
![Pasted image 20230920005621](Attachments/Pasted%20image%2020230920005621.png)
**And here's that same circuit represented in ladder logic**
![Pasted image 20230920005735](Attachments/Pasted%20image%2020230920005735.png)
Hey whaddya know its actually pretty simple

- **Majority** of simple PLC switching tasks can be implemented this way
- There exists a set of **individual instructions** that make up the complete PLC language (60-100, dunno why there's not an exact number)
- Functions vary from **simple timers and counters** to more sophisticated control functions such as **PID and advanced arithmetic**.

## Multi Input/Output Rungs
![Pasted image 20230920010420](Attachments/Pasted%20image%2020230920010420.png)
Each of the inputs in **series** (S2, S3) are the equivalent of the Boolean **AND (.)**
Each of the inputs in **parallel** are the equivalent of a Boolean **OR (+)**
$$Coil = S1 + (\bar{S2} .S3)$$


It is also possible to have **multi output** rungs, provided the **OTE instructions are NEVER places in series**. They must always be parallel and in contact with the **Neutral** rail.

![Pasted image 20230920011328](Attachments/Pasted%20image%2020230920011328.png)
While multi outputs are **necessary in some cases**, its beneficial to divide the rung into several smaller rungs for the purpose of program clarity.

### Start-Stop Rung
- A large rung can be broken down into simple Boolean expressions, such as for the simple rungs shown above.
- We can use a simple START/STOP rung is used
- Two **push buttons** are used for the **start and stop inputs** 
![Pasted image 20230920224446](Attachments/Pasted%20image%2020230920224446.png)
- In this case our start and coil are normally open and our stop is normally closed.
- Initial coil output is off, and push buttons are not activated.
- When the start PB is pressed the rung is **satisfied** (=1) and the stop = 0 (normally closed) so the coil is turned **ON**.
- This *also satisfies the bottom path through the rung on the next scan, since coil = 1 and stop = 1*
- *When the start button is released the top path becomes false but **the rung is still satisfied by the bottom path, the coil remains on until after the start pb is released.***
```ad-note
Pressing the 'stop' button (stop = 1) breaks the rung so the coil is turned **OFF** and remains off until after the stop button is released.

```


## Ladder Logic Components
### Switches
![Pasted image 20230920004521](Attachments/Pasted%20image%2020230920004521.png)
Power flows though these when they are closed. 
The normally **open** is true when the **input/output status bit controlling it is 1**. 
The normally **closed** is true when the **input/output status bit controlling it is 0**.

### Coils
![Pasted image 20230920004702](Attachments/Pasted%20image%2020230920004702.png)
Coils represent **relays** that are energized when power flows to them.
When a **coil is energized** it causes a **corresponding output** to **turn on** by changing the state of the **status bit controlling the output to 1**.
That same output status bit maybe used to control normally open/closed contacts anywhere in the program.

### Boxes
![Pasted image 20230920004920](Attachments/Pasted%20image%2020230920004920.png)
Represent v**arious instructions or functions** that are **executed when power flows** to the box. Some of these functions are **timers, counters or math operations**.

### PBs
![Pasted image 20230920000442](Attachments/Pasted%20image%2020230920000442.png)

### Example of an AND Operation
![Pasted image 20230920005044](Attachments/Pasted%20image%2020230920005044.png)
Each **rung** or network on a ladder program represents a logic operation.
Here both inputs **A and B must be true for the output C to be true**.

### Example of an OR Operation
![Pasted image 20230920005214](Attachments/Pasted%20image%2020230920005214.png)
Here either or both input A or B can be true and C will be true.

### Example of a NOT Operation
![Pasted image 20230920005311](Attachments/Pasted%20image%2020230920005311.png)
You get the idea, C is one when A is 0. When A becomes 1, the switch opens and C becomes 0


# Programming Procedure
- PLC’s are very versatile in the respect that programming changes can be made on-line while the processor is in Run Mode.

- This is equivalent to making changes in a compiled ‘C’ program while it is being executed.

- To introduce programming edits into the existing code while in Run Mode the following procedure is followed.

- Rungs can be edited and inserted into the On-Line PLC code. These changes only take place when finished.
- Once all edited rungs are entered switch the processor to TEST mode, where we can insert new code and have it scanned along with existing code.
- If any code is marked for deletion this code is prevented from being scanned.
- Once you are confident that the edit rungs are correct Assemble the code which permanently activates the new code, and removes any code marked for deletion.
![Pasted image 20230920230416](Attachments/Pasted%20image%2020230920230416.png)
![Pasted image 20230920230422](Attachments/Pasted%20image%2020230920230422.png)
- Text in the **yellow** and *green* boxes are the **address description** and *address symbol*.



# PLC Communications
*PLC Common uses of Comms Ports*
- Changing resident PLC Programs - Uploading/Downloading
- Forcing I/O Points and memory elements from a remote terminal.
- Linking a PLC into a control hierarchy containing several sizes of PLC and computer
- Monitoring Data and Alrms via Operator Interface Units (OIUs)

## Serial Comms
PLC Communications facilities normally provides serial transmission of information.

**Common Standards**
*RS 232*
- Used in **short distance computer communications** with a majority of computer hardware and peripherals
- Max effective distance of approx 30m at 9600 baud rate

*RS 422 / RS 485*
- Used for long distant comms, often between several PCs in a distributed system. RS 485 can have a maximum distance of about 1000m.

*Local Area Network (LAN)*
- Links devices on the same network providing data exchange management or protocol.
- Lets devices on the same network "talk" to each other
- LANs provide common high speed data communications bus which interconnects any or all devices on the same network
- LAN is commonly used in business to share software packages




Examples
---
## Input Connections

### DC Input Circuit
![Pasted image 20230919225710](Attachments/Pasted%20image%2020230919225710.png)

### AC Input Circuit
![Pasted image 20230919231338](Attachments/Pasted%20image%2020230919231338.png)
![Pasted image 20230919231952](Attachments/Pasted%20image%2020230919231952.png)
#todo figure out what TTL means

# Useless as far As I Know
---
# Leading Brands
**American:**
1. Allen Bradley
2. Gould Modicon
3. Texas Instruments
4. General Electric (Still around)
5. Westinghouse
6. Cutter Hammer
7. Square D

**European:**
1. Siemens
2. Klockner & Mouller
3. Festo
4. Telemechanique

**Japanese:**
1. Toshiba
2. Omron
3. Fanuc
4. Mitsubishi

# Examples of Programming Devices
- Industrial Terminal (Allen Bradley)
- Program Development Terminal (General Electric)
- Programming Pane (Gould Modicon)
- Programmer (Square D)
- Program Loader(Idec-Izumi)
- Programming Console (Keyence/Omron)

# What you need to work with a PLC
1. Programming Terminal
2. PLC Software (Manufacturer specific usually, although some follow industry standards)
3. Comms cable between Programming Terminal to PLC
4. Backup copy of ladder program (in case) 
5. Documentation (RTFM)

# Commercially Available

## Rockwell Automation
AB PICs. Note that AB is part of the Rockwell Automation
![Pasted image 20230920225303](Attachments/Pasted%20image%2020230920225303.png)

## Siemens Simatics PLC's
![Pasted image 20230920225413](Attachments/Pasted%20image%2020230920225413.png)

## Modicon TSX PLC's
![Pasted image 20230920225444](Attachments/Pasted%20image%2020230920225444.png)

# PLC Terms
- On-line: Refers to the program code currently in the PLC memory.

- Off-line: Refers to the copy of the program code stored on the programming computer.

- Up-Load: Refers to the act of copying the current On-line code from the PLC to the programming computer . (Note the previous code on the programming computer is lost during this transfer if a copy is not made)

- Down-Load: Refers to the act of copying the code from the programming computer into the PLC’s memory. (note the previous PLC code is lost during this transfer).

- Note: It is important to realize that changing the On-line program will not change the Off-line program on the programming computer. Invariably at the end of any edit there must follow an Up-load or Down-Load to make the Online and Off-line programs the same.

- Run Mode: The PLC actively scanning the code and driving outputs.

- Program Mode: The PLC is not being scanned (All outputs disabled)

- Remote Mode: programming computer can change the PLC between Run and Program.

- Note: There is a physical key on the front of each PLC processor module, which allows the PLC to be switched between Run, Remote and Program Mode.

# Selecting a PLC
**Criteria**
- Number of logical inputs and outputs.
- Memory
- Number of special I/O modules
- Scan Time
- Communications
- Software

**OUTPUT-PORT POWER RATINGS**

Each output port should be capable of supplying sufficient voltage and current to drive the output peripheral connected to it.

**SCAN TIME**

This is the speed at which the controller executes the relay-ladder logic program. This variable is usually specified as the scan time per 1000 logic nodes and typically ranges from 1 to 200 milliseconds.

**MEMORY CAPACITY**

The amount of memory required for a particular application is related to the length of the program and the complexity of the control system. Simple applications having just a few relays do not require significant amount of memory. Program length tend to expand after the system have been used for a while. It is advantageous to a acquire a controller that has more memory than is presently needed.

# Troubleshooting?
1. Look at the process

2. PLC status lights

HALT - something has stopped the CPU

RUN - the PLC thinks it is OK (and probably is)

ERROR - a physical problem has occurred with the PLC

3. Indicator lights on I/O cards and sensors

4. Consult the manuals, or use software if available.

5. Use programming terminal / laptop.