# openlane_rtltogds
## vlsi flow using opensource tool
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
run_synthesis
```
![VirtualBox_vsdworkshop_12_04_2025_21_38_47](https://github.com/user-attachments/assets/26cc62ea-14a6-4d96-a8c3-f6b7cdb17193)
### flop ratio ###
no of dff/ no of cells= 1613/18036= 0.08943
![VirtualBox_vsdworkshop_13_04_2025_17_56_34](https://github.com/user-attachments/assets/554e4f79-e2e5-459e-a440-482b13e001a3)
