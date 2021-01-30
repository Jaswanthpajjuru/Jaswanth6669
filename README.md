# workshop on open lane/sky 130
![Screenshot_2021-01-30-10-13-02-299_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106347501-f9538d00-62e4-11eb-8e73-6c10287ce521.jpg)
# About the project
OpenLANE is a computerized RTL to GDSII stream dependent on a few segments including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom philosophy contents for plan investigation and streamlining. It is an instrument begun for genuine open source tape-out experience and accompanies APACHE version 2.0 . The objective of OpenLANE is to create clean GDSII with no human intercession. OpenLANE is tuned for Skywater 130nm open-source PDK and can be utilized to create hard macros and chips.
# Architecture of a chip
Chip is focused in the package.package and chip are associated by wires with the goal that they can impart the signs in and out.The bundles has PADS:these cushions are utilized to impart signs all through the chip.The size of the bundle is given the size of the die.A center comprises of foundary IP's and macros.
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
![Screenshot_2021-01-30-20-03-22-686_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106359101-6a6f6080-6336-11eb-9c02-027cd5d297fa.jpg)
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

 we need to type the command given below 
 
 floorplan.tcl
 
 next we need to run floorplan for that we have to give
 
 run_floorplan
 
 After floorplan execution
 
![IMG-20210127-WA0017 (2)](https://user-images.githubusercontent.com/78246315/106356384-3475b080-6325-11eb-8900-f8c0bdb4ac76.jpg)
Similarly as with any remaining stages, the floorplanning will be run by setup settings in the plan explicit config.tcl file. The output the floorplanning stage is a DEF file  which depicts center zone and arrangement of standard cell sites.

## view floorplan in magic
 For thus we have to give the following inputs
 
 Magic technology file (sky130A.tech)
 
 Def file of floorplan
 
 Merged LEF file
 ![IMG-20210127-WA0002 (2)](https://user-images.githubusercontent.com/78246315/106356546-663b4700-6326-11eb-9929-d0778bd90284.jpg)
 
 ## placement
 The subsequent stage after floorplanning is placement. The blended netlist is planned to standard cells and floorplanning stage needs to decided the standard cells columns. Open LANE does situation in two phases 
Global Placement - It is to decrease the wirelength Detailed Placement - Legalizes arrangement of cells into standard cell lines while holding fast to worldwide position To do situation in OpenLANE run_placement

### viewing placement in magic

![IMG-20210127-WA0018 (2)](https://user-images.githubusercontent.com/78246315/106357097-ffb82800-6329-11eb-802c-8e9d66dcab06.jpg)

### layout

![IMG-20210127-WA0015 (2)](https://user-images.githubusercontent.com/78246315/106356730-d1394d80-6327-11eb-9568-e234e9cca522.jpg)

## Standard cell design

1.Inputs - PDKs (Process design kits), DRC and LVS rules, SPICE models, library and user characterized specs. 2.Design Steps - Design steps of cell configuration includes Circuit Design, Layout Design, Characterization. The  software GUNA used for characterization. The characterization can be named Timing Characterization, Power Characterization and Noise Characterization. 3.Outputs - Outputs of the Design are CDL (Circuit Description Language), GDSII, LEF, removed Spice netlist (.cir ), timing, clamor, power.libs, work.

### Standard cell consists of 7 steps. They are
1.Link Model File of CMOS containing property definitions.
2.Specify process corner(s) for the cell which has  to be characterized.
3.Specify cell delay and slew thresholds percentages.
4.Specify timing and power tables.
5.Read the parasitic extracted netlist.
6.Apply input or stimulus.
7.Provide necessary simulation commands.

# workshop day 3
## Design library cell
### Magic Layout View of Inverter Standard Cel

Refer: https://github.com/nickson-jose/vsdstdcelldesign for cells
![IMG-20210127-WA0014 (2)](https://user-images.githubusercontent.com/78246315/106357244-f2e80400-632a-11eb-9219-90d0a111470c.jpg)

### Invoke magic
![IMG-20210127-WA0011 (2)](https://user-images.githubusercontent.com/78246315/106357299-40647100-632b-11eb-89da-e401931951e7.jpg)
### Layout Magic
![IMG-20210127-WA0010 (2)](https://user-images.githubusercontent.com/78246315/106357318-73a70000-632b-11eb-9858-52ea920095d2.jpg)

## Magic key features
1.Color Palette - Defines layers and associated colors Continuous DRC

2.Device Inference - Automatic recognition of NMOS and PMOS devices
## PEX EXTRACTION WITH MAGIC
![Screenshot_2021-01-30-18-50-44-277_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106357507-7bb36f80-632c-11eb-97ca-0820579e1020.jpg)

After ngspice simulation 
![IMG-20210127-WA0006 (2)](https://user-images.githubusercontent.com/78246315/106358419-0a76bb00-6332-11eb-9a8e-b62b9c7c6b05.jpg)
we get the output given below
![Screenshot_2021-01-30-18-58-03-051_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106357668-828eb200-632d-11eb-98b4-9befe588f5aa.jpg)
Plotting the output vs time while sweeping input
![Screenshot_2021-01-30-18-58-03-051_com android chrome (3)](https://user-images.githubusercontent.com/78246315/106357681-93d7be80-632d-11eb-8290-7984a820eb2a.jpg)

# workshop day 4
## Layout Timing and CTS flow
Place and routing is performed by GDS files which are generated by Magic . The abstract information will present in metal and pin information. The PnR tool will use the abstract view as LEF information to perform interconnect.
![Screenshot_2021-01-30-19-05-57-374_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106357852-bdddb080-632e-11eb-8b4d-98ce6be82511.jpg)
Tracks are utilized in the routing .Routes can go over the tracks or metal follows can go over the tracks. The record is saying that for the li1 layer the x or level track is at a balanced of 0.23 and a pitch of 0.46. The balance is the separation from the birthplace to the steering track in either the x or y bearing. It is a large portion of the pitch so that implies the tracks are revolved around the cause.

## standard cell pi placement

On-track standard cell pin placement is important for DRC free P n R flow. Pins should align with the li1 and met1 most popular routing directions. Throughout voltaic cell creation this idea should be accounted  to confirm a cell is aligned with routing grids in Magic then  we are able to show a grid on high of the g d s file.

Displaying the grid in magic
![Screenshot_2021-01-30-19-06-02-660_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106357998-8faca080-632f-11eb-84a3-26d446e143df.jpg)
we can ensure that our pin placement is optimized for PnR flow
![Screenshot_2021-01-30-19-06-02-660_com android chrome (3)](https://user-images.githubusercontent.com/78246315/106358011-a3580700-632f-11eb-80a7-013c79cee35a.jpg)
## LEF generation in magic
Magic allows to generate the cell LEF which takes information directly from magic teriminal
![Screenshot_2021-01-30-19-06-02-660_com android chrome (4)](https://user-images.githubusercontent.com/78246315/106358096-05b10780-6330-11eb-905c-a097cab00d49.jpg)

### Generated cell LEF
![Screenshot_2021-01-30-19-06-07-412_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106358180-6f311600-6330-11eb-9a02-b43b475ff7d0.jpg)
To include newcells in openlane we need to do initial configuration

1.Fully characterize new cell with GUNA for specified corners
2.Include cell level liberty file in top level liberty file 
3.Reconfigure synthesis switches in the config.tcl file 
4.Overwrite previous run to include new configuration switches
5.Add additional statements to include extra cell LEFs
6.Check synthesis logs to ensure cell has been integrated correctl
![IMG-20210127-WA0022 (2)](https://user-images.githubusercontent.com/78246315/106358258-1b72fc80-6331-11eb-9d7f-f3d3b93bd04a.jpg)
## CLOCK TREE SYNTHESIS
By completing the floorplan and standard cell placement in Open LANE .We insert the clock tree for sequential elements in this design. The main concerns regarding the generation of the clock tree are the two which are mentioned below 
1.Clock skew - Difference in arrival times of the clock for sequential elements across the design.
2.Delta delay - Skew introduced through capacitive coupling of the clock tree nets run clock tree synthesis in OpenLANE
![Screenshot_2021-01-30-19-06-10-706_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106358604-3f374200-6333-11eb-9c26-ec6ee61b7cf8.jpg)
## Post CTS - STA Analsys
### Invoking openroad from openlane
 Timinig analysis is done by creating .db database file. The database file is created from the post-cts LEF and DEF files. 
 To generate the .db files within Openroad.
 ![Screenshot_2021-01-30-19-06-10-706_com android chrome (3)](https://user-images.githubusercontent.com/78246315/106358618-5f670100-6333-11eb-8816-ac2417bdea96.jpg)
 # Workshop day5 
 ## Final steps in RTL - GDSII
After generating our clock tree network and verifying post routing STA checks . Now we are ready to generate the power distribution network in OpenLANE.
![Screenshot_2021-01-30-19-06-13-382_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106358775-3eeb7680-6334-11eb-9779-2e15f2dc6bd0.jpg)
### The PDN feature in OPENLANE creates:
1.Power ring global to the entire core.
2.Power halo local to any preplaced cells.
3.Power straps to bring power into the center of the chip.
4.Power rails for the standard cells.
![Screenshot_2021-01-30-19-06-13-382_com android chrome (3)](https://user-images.githubusercontent.com/78246315/106358785-50348300-6334-11eb-92e0-f8632a115e2b.jpg)
## Routing 
### Global and Detailed Routing
OpenLANE uses TritonRoute as the routing tool for implementation of designs.

Routing consists of 2stages thay are,
1.Global Routing - Routing guide is generated for interconnects on our netlist defining what layers on the chip each of the nets will be reputed.
2.Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides.
![Screenshot_2021-01-30-19-06-16-846_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106358838-a9041b80-6334-11eb-9518-c3fdcf559ea9.jpg)
### In case of DRC errors persist after routing the user has two options:
   1.Re-run routing with higher QoR settings.
   2.Manually fix DRC errors specific in tritonRoute.drc file.
## SPEF EXTRACTION
After routing competion interconnect parasitics are extracted to perform sign-off post-route STA analysis.Finally the parasitics are extracted into a SPEF file.
## Acknowledgements
@ Nickson Jose - VSD VLSI Engineer @ Kunal Ghosh - Co-founder (VSD Corp. Pvt. Ltd) @ Praharsha

 






















