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



