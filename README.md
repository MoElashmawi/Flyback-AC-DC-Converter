Flyback AC-DC Converter — 12V SMPS
PCB Design Project | KiCad 10.0.1 | Mohamed Elashmawi
A complete Switch-Mode Power Supply (SMPS) designed from scratch using the Flyback
topology, converting 230VAC mains input to a regulated 12V DC output. This project
covers full schematic design, PCB layout, and 3D validation.

## 📷 Overview

### Schematic
![Schematic](images/schematic.png)

### PCB Layout
![PCB Layout](images/pcb_layout.png)

### 3D Render
![3D Render](images/3d_render.png)

⚡Specifications

Parameter Value

Input Voltage 230VAC (50Hz)
Output Voltage 12V DC

Topology Flyback (Isolated SMPS)

PWM Controller VIPer22A (DIP-8)

Transformer EE25-13-7

Rectifier Bridge KBP206

Output Diode SB360 (Schottky)

Feedback / Isolation EL817 Optocoupler + TL431

Input Protection Varistor + NTC Thermistor + Fuse (500mA)

EMI Filter Schaffner RN102-0.3-02-12M

🔧Circuit Architecture

The design is divided into four functional blocks:

1.🔌Input Filter ( Eingangsfilter )

Varistor (RV1): Overvoltage/surge protection

NTC Thermistor (TH1): Inrush current limiting at startup

EMI Filter (FL1 - Schaffner RN102): Common-mode noise suppression

Fuse (F1 - 500mA): Short-circuit protection

X-Capacitor (C1 - 100nF/275VAC): Differential-mode noise filtering

2.⚙️Power Stage ( Leistungsstufe )

Bridge Rectifier (D15 - KBP206): Full-wave AC-to-DC conversion

Bulk Capacitor (C2 - 22µF/400V): DC bus smoothing

VIPer22A PWM Controller (U1): Integrated MOSFET + PWM control IC

Fast Recovery Diode (D1 - FR107): Demagnetization protection

Flyback Transformer (T1 - EE25-13-7): Galvanic isolation & energy transfer

RCD Snubber (R3, C3, D1): MOSFET drain spike clamping

3.🔋DC Output ( DC Ausgang )

Schottky Diode (D5 - SB360): Low forward-drop rectification

Output Inductance (L1 - 10µH): Output ripple reduction

Output Capacitors (C5–C8 - 470µF/16V): Output voltage smoothing

Status LED (D3) + Resistors: Power-on indication

4.🔁Feedback / Regulation ( Rückkopplung )

TL431 (U2): Programmable precision shunt regulator

EL817 Optocoupler (U3): Galvanic isolation of feedback signal

Trimmer (RV3 - 500Ω): Output voltage fine adjustment

Divider Network (R6, R7, R4, R5): Voltage sensing

📐Key Design Decisions

RCD Snubber Design

The Flyback topology generates high-voltage spikes on the MOSFET drain during turn-off

due to transformer leakage inductance. An RCD clamp circuit (R3 = 100kΩ, C3 =

2.2nF/1kV, D1 = FR107) was implemented to absorb these spikes and protect the VIPer22A

internal MOSFET.

Optocoupler Feedback Loop

The EL817 optocoupler in combination with the TL431 shunt regulator creates a stable,

isolated feedback loop. This ensures regulated 12V output regardless of input voltage or

load variations.

EMI & Input Filtering

A Schaffner common-mode choke (FL1) combined with an X-capacitor (C1) and NTC

thermistor (TH1) provides a complete input EMI filter, preventing conducted noise from

entering the mains supply.

📦Bill of Materials (Key Components)

Reference Component Value / Part Number

U1 PWM Controller VIPer22ADIP-E

U2 Shunt Regulator TL431DBZ

U3 Optocoupler EL817

T1 Transformer EE25-13-7

D5 Schottky Diode SB360

D15 Bridge Rectifier KBP206

D1 Fast Recovery Diode FR107

FL1 EMI Filter Schaffner RN102-0.3-02-12M

RV1 Varistor 275VAC

TH1 NTC Thermistor —

C2 Bulk Capacitor 22µF / 400V

C5–C8 Output Capacitors 470µF / 16V

RV3 Trimmer 500Ω

🎓What I Learned

Complete SMPS design flow from topology selection to PCB manufacturing files

Deep understanding of the VIPer22A integrated PWM controller and its peripheral

design

RCD snubber calculation for MOSFET protection in flyback converters

Optocoupler feedback loop design for isolated DC-DC regulation

PCB layout best practices for mixed high-voltage / low-voltage circuits

Proper grounding strategies to minimize EMI in switch-mode supplies

Integration of STEP 3D models in KiCad for component validation

⚠️Safety Notice

This project involves dangerous mains voltages (230VAC). The schematic and PCB are

provided for educational and design reference only. Do not build or test this circuit

without proper knowledge, equipment, and safety precautions.

👤Author

Mohamed Elashmawi B.Sc. Elektrotechnik und Informationstechnik — TU Dortmund

📄License
This project is open-source for educational purposes. Feel free to use, adapt, and learn from
it — credits appreciated!
