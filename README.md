# openlane_rtltogds
## vlsi flow using opensource tool
## DAY 1 ##
TOOLS USED: 
  1. RTL + synthesis: yosys, abc
  2. STA : opensta
  3. DFT: Fault
  4. floorplan placement CTS: openRoad
  5. logic equivalence check: yosys 
  6. physical verification: magic and netgen

pdk: 130nm pdk (sky130)
// go to the openlane directory where src file, design file, config.tcl files exist.

**write command**
```
./flow.tcl -interactive
```
>__openlane launched.__
```
package require openlane 0.9
prep -design picorv32a
```
>__synthesis start__
```
run_synthesis
```
![VirtualBox_vsdworkshop_12_04_2025_21_38_47](https://github.com/user-attachments/assets/26cc62ea-14a6-4d96-a8c3-f6b7cdb17193)
### flop ratio ###
no of dff/ no of cells= 1613/18036= 0.08943 \
this information are present in log file
![VirtualBox_vsdworkshop_13_04_2025_17_56_34](https://github.com/user-attachments/assets/554e4f79-e2e5-459e-a440-482b13e001a3)
output file: picorv32a_synthesis.v

## DAY 2 ##

![RUN_FLLORPLAN OUTPUT](https://github.com/user-attachments/assets/e99ab75d-74c0-4bdd-89df-c44fb6abcf8d)
> _Floorplan start_

``` run_floorplan ```\
output file: picorv32a.floorplan.def\
in the def file " picorv32a.floorplan.def" is located in\
/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-04_14-17/results/floorplan
### calculation of die area ###
unit distance : height x width : 660685 671405
_in micron : 660685/1000 x 671405/1000 = 660.685x671.405= 443587.212 micron_

![die area](https://github.com/user-attachments/assets/f63e5570-a15f-447c-ad74-840bf8c797cc)

### magic layout open ###
``` magic -T Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130a.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def& ```
![MAGIC OPENED](https://github.com/user-attachments/assets/4eb06512-eaeb-4f1d-ab50-a56b1e86f902)
# SUMMARY UPTO THIS TIME #
> ### Change directory to openlane flow directory
> cd Desktop/work/tools/openlane_working_dir/openlane 

> ### alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
> ### Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
> docker 
> ### Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
> ./flow.tcl -interactive

> ### Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
> package require openlane 0.9

> ### Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
> prep -design picorv32a

> ### Now that the design is prepped and ready, we can run synthesis using following command
> run_synthesis

> ### Now we can run floorplan
> run_floorplan
