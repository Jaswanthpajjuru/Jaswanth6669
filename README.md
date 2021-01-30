# workshop on open lane/sky 130
![Screenshot_2021-01-30-10-13-02-299_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106347501-f9538d00-62e4-11eb-8e73-6c10287ce521.jpg)
# About the project
OpenLANE is a computerized RTL to GDSII stream dependent on a few segments including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom philosophy contents for plan investigation and streamlining. It is an instrument begun for genuine open source tape-out experience and accompanies APACHE version 2.0 . The objective of OpenLANE is to create clean GDSII with no human intercession. OpenLANE is tuned for Skywater 130nm open-source PDK and can be utilized to create hard macros and chips.
# Architecture of a chip
Chip is focused in the package.package and chip are associated by wires with the goal that they can impart the signs in and out.The bundles has PADS:these cushions are utilized to impart signs all through the chip.The size of the bundle is given the size of the die.A center comprises of foundary IP's and macros.

MACROS(Digital blocks are called as macros) eg:Socs,SP1

FOUNDARY IP's(these are manufactured at foundary where all these are manufactured) eg: PLL,adc0,ac1,dac,SRAM
![Screenshot_2021-01-30-10-22-41-409_com android chrome (2)](https://user-images.githubusercontent.com/78246315/106347686-a11d8a80-62e6-11eb-9543-7e6cee9f3c1a.jpg)
### Physical Design Flow
## RTL TO GDS FLOW (Physical Flow)
# RTL DESIGN 
RTL plan and social demonstrating are performed with an equipment portrayal language (HDL). EDA apparatuses will utilize the HDL to perform planning of more elevated level parts to the semiconductor level required for actual usage. HDL demonstrating is typically performed utilizing either Verilog or VHDL. One of two plan strategies might be utilized while making the HDL of a microarchitecture.

It provides the overview of circuit design

1.Combinational logic    

2.Registers 

1.Modules.

BEHAVIORAL MODELING – Allows the microarchitecture modeling to be performed with behavior-based modeling in HDL. This method bridges the gap between C and HDL allowing HDL design to be performed.

# Synthesis
we plan the ciricuts by utilizing HDL.the planned rtl is changed over into circuits comprised of various segments from the standard cell library.the resultant circuit is in the HDL as door level netlist.these standard cells have normal formats which has fixed stature square shape and width is in the whole number numerous of units.
# Floor and Power Planning
The point is to plan the silicon zone and make a strong force appropriation organization (PDN) to control every one of the orchestrated netlist's individual segments. Furthermore, to guarantee an authorized GDS document, large scale position and blockages should be recognized before situation happens. We create the ring that is connected to the cushions in force arranging, which hauls power around the chip's edges. We additionally have power ties that utilization higher metal layers to convey capacity to the center of the chip, limiting IR fall and the issue of electro-movement.


