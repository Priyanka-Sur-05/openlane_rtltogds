# openlane_rtltogds
# vlsi flow in using opensource tool
TOOLS USED: 
  1. RTL + synthesis: yosys, abc
  2. STA : opensta
  3. DFT: Fault
  4. floorplan placement CTS: openRoad
  5. logic equivalence check: yosys 
  6. physical verification: magic and netgen

pdk: 130nm pdk (sky130)
// go to the openlane directory where src file, design file, config.tcl files exist.
write command

./flow.tcl -interactive
//openlane launched.
package require openlane 0.9
prep -design picorv32a
run_synthesis
