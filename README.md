# workshop on open lane/sky 130
![Screenshot_2021-01-30-10-13-02-299_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106347501-f9538d00-62e4-11eb-8e73-6c10287ce521.jpg)
# About the project
OpenLANE is a computerized RTL to GDSII stream dependent on a few segments including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom philosophy contents for plan investigation and streamlining. It is an instrument begun for genuine open source tape-out experience and accompanies APACHE version 2.0 . The objective of OpenLANE is to create clean GDSII with no human intercession. OpenLANE is tuned for Skywater 130nm open-source PDK and can be utilized to create hard macros and chips.
# Architecture of a chip
Chip is focused in the package.package and chip are associated by wires with the goal that they can impart the signs in and out.The bundles has PADS:these cushions are utilized to impart signs all through the chip.The size of the bundle is given the size of the die.A center comprises of foundary IP's and macros.

MACROS(Digital blocks are called as macros) eg:Socs,SP1

FOUNDARY IP's(these are manufactured at foundary where all these are manufactured) eg: PLL,adc0,ac1,dac,SRAM
![Screenshot_2021-01-30-10-22-41-409_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106347686-a11d8a80-62e6-11eb-9543-7e6cee9f3c1a.jpg)
# Physical Design Flow
## RTL TO GDS FLOW (Physical Flow)
### RTL DESIGN 
RTL plan and social demonstrating are performed with an equipment portrayal language (HDL). EDA apparatuses will utilize the HDL to perform planning of more elevated level parts to the semiconductor level required for actual usage. HDL demonstrating is typically performed utilizing either Verilog or VHDL. One of two plan strategies might be utilized while making the HDL of a microarchitecture.

It provides the overview of circuit design

1.Combinational logic    

2.Registers 

1.Modules.

BEHAVIORAL MODELING – Allows the microarchitecture modeling to be performed with behavior-based modeling in HDL. This method bridges the gap between C and HDL allowing HDL design to be performed.

### Synthesis
We plan the ciricuts by utilizing HDL.the planned rtl is changed over into circuits comprised of various segments from the standard cell library.the resultant circuit is in the HDL as door level netlist.these standard cells have normal formats which has fixed stature square shape and width is in the whole number numerous of units.
### Floor and Power Planning
The point is to plan the silicon zone and make a strong force appropriation organization (PDN) to control every one of the orchestrated netlist's individual segments. Furthermore, to guarantee an authorized GDS document, large scale position and blockages should be recognized before situation happens. We create the ring that is connected to the cushions in force arranging, which hauls power around the chip's edges. We additionally have power ties that utilization higher metal layers to convey capacity to the center of the chip, limiting IR fall and the issue of electro-movement.
### Placement
Detect the standard cells on the floorplane lines, agreed with objections portrayed in the advancement lef record. Position is done in two phases: Global and Detailed. In Global circumstance endeavors to find ideal circumstance for all phones yet they may be covering and not changed in accordance with segments, separated game plan takes the overall position and approves the aggregate of the courses of action endeavoring to stick to what the overall circumstance needs.
### CTS (clock tree synthesis)
Clock tree amalgamation is used to make the clock course network that is used to pass on the clock to each continuous segment. The guideline objective is to make an association with unimportant inclination across the chip. H-trees are a commonplace association geology that is used to achieve this target.
### Routing
Executes the interconnect structure between standard cells using the extra open metal layers after CTS and PDN age. The guiding is performed on guiding frameworks to ensure unimportant DRC botches.

## INTRODUCTION TO OPENLANE
Process Design Kit (PDK) is the interface between the CAD fashioners and the foundry. The PDK is an assortment of documents used to demonstrate a manufacture cycle for the EDA devices utilized in planning an IC. PDK's are customarily shut source and henceforth are the restricting component to open-source Digital ASIC Design. Google and Skywater have broken this disgrace and distributed the world's first open-source PDK on June 30th, 2020. This advancement has been an impetus for open-source EDA apparatuses. This workshop centers around utilizing the open-source RTL2GDS EDA apparatus, OpenLANE, related to the Skywater 130nm PDK to play out the full RTL2GDS stream as demonstrated below

![Screenshot_2021-01-30-11-03-02-265_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106348260-e5128e80-62ea-11eb-90cc-daa86211f580.jpg)
### 1 Synthesis
Yosys - Performs RTL synthesis using GTech mapping
 abc - Performs technology mappin to standard cells described in the PDK. We can adjust synthesis techniques using different integrated abc scripts to get desired results
 OpenSTA - Performs static timing analysis on the resulting netlist to generate timing report
 Fault – Scan-chain insertion used for testing post fabrication. Supports ATPG and test patterns compaction
 ### 2 Floorplan and PDN
 Init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
  Ioplacer - Places the macro input and output ports
  PDN - Generates the power distribution network
  Tapcell - Inserts welltap and decap cells in the floorplan
  Placement – Placement is done in two steps, one with global placement in which we place the designs across the chip, but they will not be legal placement with some           standard cells overlapping each other, to fix this we perform a detailed placement which legalizes the design and ensures they fit in the standard cell rows
  RePLace - Performs global placement
  Resizer - Performs optional optimizations on the design
  OpenPhySyn - Performs timing optimizations on the design
  OpenDP - Perfroms detailed placement to legalize the globally placed components
  ### 3 CTS
  TritonCTS - Synthesizes the clock distribution network
  ### 4 Routing
  FastRoute - Performs global routing to generate a guide file for the detailed router
  TritonRoute - Performs detailed routing from global routing guides'
  SPEF-Extractor - Performs SPEF extraction that include parasitic information
  ### 5 GDSII Generation
   Magic - Streams out the final GDSII layout file from the routed def
  ### Checks
  Magic - Performs DRC Checks & Antenna Checks
  Netgen - Performs LVS Checks
  # workshop day 1
  ## Inception of open source EDA
  ## Sky water pdk files
  
![IMG-20210127-WA0027 (2)](https://user-images.githubusercontent.com/78246315/106348941-0fb31600-62f0-11eb-86cb-2809a8530dc9.jpg)
it contains every one of these files in pdks Skywater-pdk – it Contains all the foundry gave PDK related records Open_pdks – it Contains contents which are utilized to overcome any barrier between shut source and open-source PDK to EDA device similarity Sky130A – These are open-source viable PDK files.

## Invoking openlane
![IMG-20210127-WA0024 (2)](https://user-images.githubusercontent.com/78246315/106349027-9a941080-62f0-11eb-8816-f97301ae3db7.jpg)
 1.The script which runs the openlane flow is ./flow.tcl
 2.OpenLANE can be run interactively or in autonomous mode
 3.To run openlane interactively use the command -interactive option with the ./flow.tcl script
## package importing
To import we need to run the command below given
![IMG-20210127-WA0023 (2)](https://user-images.githubusercontent.com/78246315/106349084-f65e9980-62f0-11eb-800c-b19a31514566.jpg)
## prepare design 
prep is used to make file structure
![IMG-20210127-WA0022 (2)](https://user-images.githubusercontent.com/78246315/106349124-53f2e600-62f1-11eb-9595-ea953ee7d2cd.jpg)
## Synthesis
![IMG-20210127-WA0020 (2)](https://user-images.githubusercontent.com/78246315/106349147-a0d6bc80-62f1-11eb-93e5-a1a73762fd77.jpg)
# workshop day 2
## Chip floorplanning and standadrd cells
In Floorplanning we set 1.Die Area 2.Core Area 3.Core Utilization 4.Aspect Ratio 5.Place Macros 6.Power distribution network 7.Place input and output pins.

## Aspect ratio and utilization factor
Utilization factor is the proportion of the size of the involved center to that of the die.typicallically we go for use factor of 0.5-0.7.by setting them in this reach permits us to do streamlining of position and to do feasible directing .Aspect proportion is the state of your chip by the stature of the center zone separated by the width of the center territory. In the event that the viewpoint proportion is 1 methods the chip as a square. for any remaining the chip is fit in rectangular shape.
## Preplaced cells
The cells which are utilized for significant purposes by putting in them in a gathering we structure preplaced cell.these preplaced cells are put in the circuit once they will be they can't be eliminated.
## Decoupling Factors
we utilize these Decoupling Capacitors close to the preplaced cells on the grounds that the cells require the voltage which assists with running. at the point when the voltage to the circuit from the source prior to arriving at the cells their is a voltage drop to address these difficult we use Decoupling Capacitors which produces the voltage which is adequate for the cell and again after the release the Decoupling Capacitors get charged in this manner they go about as a force supply.
## power planning
During the Floor arranging stage is fundamental for lower clamor in computerized circuits ascribed to voltage drop. Coupling capacitance is shaped between interconnect wires and the which are helpful to either for charged or released which address either the rationale 1 or the rationale 0.charge related with coupling capacitors might be unloaded to ground. On the off chance that there are insufficient ground taps charge will amass at the tap and the ground line will act like a huge resistor, raising the ground voltage and bringing down our commotion edge. To determine this issue a hearty PDN with comprises many force tie taps are expected to bring down the opposition with the PDN.
## Pin placement
Pin placement is a significant piece of floor wanting to limit buffering and to improve the force utilization and to have viable planning delays. As a rule, ideal pin arrangement will be went with less buffering and uses less force utilization. In the wake of doing stick situation is framed we need to put consistent cell blockages along the I/O ring to separate between the center area and I/O area.





