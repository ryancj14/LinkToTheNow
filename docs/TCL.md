# TCL

## TCL Commands
 
* puts - prints the string      	
    * (\n does not, but \\n does do a ‘\n’ newline character)
    * (\t does not but \\t does do a ‘\t’ tab character)
* set - sets a variable’s value
    * $ - gives the value of a variable
    * “ “ – a full string including spaces (recognizes variable values w/ $)
    * { } – a full string including spaces (does not recognize $ for values)
* expr - evaluates an expression and stores it in the set;
    * \[ ] – gives the result of another statement with statement
        * ex. `set c [expr “$a + $b”]`
    * && - AND    	        	
    * || - OR        	        	
    * ! – NOT
    * & - Bitwise AND      	
    * | - Bitwise OR          	
    * ^ - Bitwise XOR
    * << - Binary Left Shift   
    * >> - Binary Right Shift  
    * == - Equals
* incr - increments the value
* arrays – set array(0) value1
    * ex. `set items(0) boot`
* exec \<bash command> -  have the outer (bash) shell execute said command
* tclsh – go to a tcl shell (not vivado)    
* exit – leave tcl shell

### *if* / *while* / *for* functions 
They are similar to c++.
```tcl
if {expression} {statement} else {statement}
if {expression} {statement} elseif {expression} {statement}
```
```tcl
while {expression} {
        	statement;
        	statement;
        	…
}
```
```tcl
for {initialization} {condition} {increment} {
        	statement;
        	…
}
```
mostly used for referencing a large list
* break – terminates loop and continues to next statement
* continue – skips to next iteration of loop
```tcl
foreach index [array names arrayName] {
        	statement;
        	…
}
```
***
### Strings
* string compare string1 string2 – compares the strings lexographically, 0 if equal, otherwise 1 or -1
* string index \<string> \<index> – returns the character at that index
* string length \<string> – returns length
* string range string index1 index2 – returns all of the characters from index1 to index2
string tolower string – returns the string in lowercase
* string toupper string – returns the string in uppercase
* string trim trimCharacters – trims from both sides (default is whitespace)
* string match stringPattern string – returns 1 if the string matches the pattern
* append string1 string2 – append a string to another
***
### Lists
* set list {{item1} {item2} {item3}}
* puts “Item2 is: [lindex $x 2]” (lindex – return variable at index of list)
* concat $a $b – combines two lists (a and b)
* linsert – inserts item at position in list
* lreplace – replaces item with new item at position in list
* lappend – appends new item to the list
* lsort – returns new sorted list
* llength – returns the length of the list
***
### Files
* open “filename” \<option>
    * a / a+ / r / r+ / w / w+
    * + - for reading and writing
    * r – for reading
    * w – for writing (creates the file if it does not exist)
    * a – for writing (sets the current location to end of file)
* read $openfile – reads the file
* close $openfile – closes the file
* gets $openfile \<var> – put the next line of the file into var
* puts $openfile \<string> – puts the string into the file
 
```tcl
set fp [open “input.txt” r]
set file_data [read $fp]
puts $file_data
close $fp
```
```tcl
set fp [open “input.txt” r]
while { [gets $fp data] >= 0 } {
        	puts $data
}
close $fp
``` 
```tcl
set fp [open “input.txt” w+]
puts $fp “test”
close $fp
```
***
### Functions (Proc)
functions in tcl are called procedures (proc)
```
proc procName {argument} {
        	statement
}
```
to call functions simply put its name
```
procName {argument}
```
***
***

w/ NEXYS 4 Board
```
create_project <project name> <Path of project> -part xc7a100tcsg324-1
```

To be run at project start
```tcl
set_msg_config -new_severity "ERROR" -id "Synth 8-87"
set_msg_config -new_severity "ERROR" -id "Synth 8-327"
set_msg_config -new_severity "ERROR" -id "Synth 8-3352"
set_msg_config -new_severity "ERROR" -id "Synth 8-5559"
set_msg_config -new_severity "ERROR" -id "Synth 8-6090"
set_msg_config -new_severity "ERROR" -id "Synth 8-6858"
set_msg_config -new_severity "ERROR" -id "Synth 8-6859"
set_msg_config -new_severity "WARNING" -id "Timing 38-313"
set_msg_config -new_severity "ERROR" -id "Timing 38-282"
set_property INCREMENTAL false [get_filesets sim_1]
set_property -name {xsim.simulate.runtime} -value 100ns -objects [get_filesets sim_1]
```
The tcl commands that are important for controlling vivado gui and functions
vivado                     	- starts up vivado with the gui
vivado /home/student/project_1/project_1.xpr   	- opens up project_1
vivado -mode tcl     	- starts up vivado without the gui
start_gui                  	- starts the gui
stop_gui                  	- stops the gui (returns to tcl shell mode)
open_project /home/student/project_1/project_1.xpr    	- opens project_1 (must use .xpr file)
 
launch_simulation -simset sim_1   	- launches the sim_1 simulation (simset must be specified)
open_wave_config /home/student/project_1/project_tb_behav.wcfg   	- opens the specific waveform
create_wave_config /home/student/project_1/new_title.wcfg   	-creates a new waveform
save_wave_config  	-
current_sim    - set the current simulation object or get the current simulation object
relaunch_sim - recompile the design and restart the simulation
set_property top tb_SevenSegment [get filesets sim_1] – sets top to file within sim_1
set_property top_lib xil_defaultlib [get filesets sim_1] – probably unnecessary
close_sim    	- closes the simulation
exit              	- closes Vivado
 
update_compile_order -fileset sources_1 	- possibly has a purpose, ran when project opened
reset_run synth_1              	- resets the run if it has been done before
launch_runs synth_1          	- runs the synthesis
launch_runs impl_1            	- runs the implementation
 
synth-design -rtl -name rtl_1          	- opens the elaborated design
close_design                                   	- closes elaborated design
 
get_sites -filter { SITE_TYPE == "AMS_ADC" }        	- finds the sits with the specific type
 
get_cells      	- finds the cells under the conditions specified
get_nets
show_schematic [get_nets txd_tx]
 
report_property [get_cells cell_name]                  	- report all properties
get_property PROPERTY [get_cells cell_name]      	- get the property specified
filter [get_cells]  [PROPERTY == SET]                      	- filter results by property
 
get_bel_pins                	     	Get a list of bel_pins. If a design is loaded, gets the constructed site type bels.
get_bels                    	         	Get a list of bels. If a design is loaded, gets the constructed site type bels.
get_board_parts             	  	Get the list of board_part available in the project
get_boards                  	      	This command is auto loaded by Tcl. To explicitly load the command type 'load_features board'.
get_cells                   	         	Get a list of cells in the current design
get_cfgmem_parts            	   This command is auto loaded by Tcl. To explicitly load the command type 'load_features labtools'.
get_clock_regions           	 	Get the clock regions for the current device.
get_clocks                  	       	Get a list of clocks in the current design
get_debug_cores             	 	Get a list of debug cores in the current design
get_debug_ports             	 	Get a list of debug ports in the current design
get_designs                 	      	Get a list of designs in the current project
get_drc_checks              	   	Get a list of DRC rule check objects
get_drc_ruledecks           	 	Get a list of DRC rule deck objects
get_drc_violations          	 	Get a list of DRC violations from a previous report_drc run
get_example_designs     	 	Get a list of example designs
get_files                   	         	Get a list of source files
get_filesets                	       	Get a list of filesets in the current project
get_generated_clocks 	    	Get a list of generated clocks in the current design
get_hierarchy_separator    	Get hierarchical separator character
get_highlighted_objects     	Get highlighted objects
get_interfaces              	    	Get a list of I/O port interfaces in the current design
get_io_standards            	 	Get a list of IO standards.
get_iobanks                 	     	Get a list of iobanks.
get_ip_upgrade_results      	Get a list of results for IP upgrades during the current project
get_ipdefs                  	       	Get a list of IP from the current IP Catalog
get_ips                     	          	Get a list of IPs in the current design
get_lib_cells               	       	Get a list of Library Cells
get_lib_pins                	      	Get a list of Library Cell Pins
get_libs                    	          	Get a list of Libraries
get_macros                  	     	Get a list of macros in the current design
get_marked_objects          	  Get marked objects
get_methodology_checks 	  Get a list of Methodology rule check objects
get_methodology_violations Get a list of Methodology violations from a
                            	               	previous report_methodology run
get_msg_config              	  	Returns the current message count, limit, or the message configuration rules previously defined by the set_msg_config command.
get_net_delays              	   	Get the routed or estimated delays in picoseconds on a net from the driver to each load pin.
get_nets                    	        	Get a list of nets in the current design
get_nodes                   	      	Get a list of nodes in the device.
get_package_pins            		Get a list of package pins
get_param            	             	Get a parameter value
get_partition_defs          	 	Get a list of PartitionDefs
get_parts                   	        	Get a list of parts available in the software
get_path_groups            	  	Get a list of path groups in the current design
get_pblocks                 	      	Get a list of Pblocks in the current design
get_pins                    	         	Get a list of pins in the current design
get_pips                    	         	Get a list of programmable interconnect points (pips) on the current device.
get_pkgpin_bytegroups     	Get a list of package pin byte groups.
get_pkgpin_nibbles            	Get a list of pkgpin nibbles.
get_ports                            	Get a list of ports in the current design
get_pplocs                          	Internal TCL task for reporting PPLOCs on pins or nets
get_pr_configurations        	Get a list of partition configurations
get_previous_transition     	This command is auto loaded by Tcl. To explicitly load the command type 'load_features simulator'.
get_primitives                     	Get a list of available unisim primitives for a part
get_projects                	      	Get a list of projects
get_property                	     	Get properties of object
get_reconfig_modules        	Get a list of ReconfigModules
get_runs                    	Get a list of runs
get_selected_objects      	 	Get selected objects
get_simulators              	    	Get registered simulators
get_site_pins               	     	Get a list of site_pins.
get_site_pips               	     	Get a list of site_pips from the given object.
get_sites                   	         	Get a list of Sites
get_slrs                    	          	Get a list of slrs.
get_speed_models            	   Get a list of speed_models in the device.
get_template_bd_designs  	Get a list of IPI example designs
get_tiles                   	         	Get a list of tiles.
get_timing_arcs             	   	Get a list of timing arcs
get_timing_paths            	 	Get timing paths
get_wires                   	       	Get a list of wires.
Command   	Description
get_cells      	Get logic cell objects based on name/hierarchy or connectivity
get_pins      	Get pin objects based name/hierarchy or connectivity
get_nets      	Get net objects by name/hierarchy or connectivity
get_ports    	Get top-level netlist ports by name or connectivity
all_inputs    	Return all input ports in the current design
all_outputs  	Return all output ports in the current design
all_ffs          	Return all flip flops in current design
all_latches   	Return all latches in current design
all_dsps       	Return all DSP cells in the current design
all_rams      	Return all ram cells in the current design
all_clocks    	Get a list of all defined clocks in the current design
 
Filtering
All get_* commands provide a -filter option. There is also an independent filter command.
Filtering provides a mechanism to reduce lists of returned objects based on the object
properties. For example, to filter on a LIB_CELL type you could do the following:
> get_cells -filter {LIB_CELL == FDCE}
You can combine multiple filters together:
> get_ports -filter {DIRECTION == in && NAME =~ *clk*}
You can filter directly on Boolean properties:
> get_cells -filter {IS_PRIMITIVE && !IS_LOC_FIXED}
Valid operations are: ==, !=, =~, !~, <=, >=, >, < as well as && and || between filter patterns
 
Common TCL Commands
This page provides a brief summary of common TCL commands that may help you during your laboratory assignments.
 
Project Management
Command   	        	Description
create_project        	Create new Vivado Project
 
 
Project Management
Creating a new project
create_project <project name> <Path of project> -part xc7a100tcsg324-1
 
Adding a Verilog file to the project
add_files -norecurse C:/wirthlin/ee220/git/labs/StructuralVerilog/solution/TestFunction.v
update_compile_order -fileset sources_1
 
Adding a constraints file (.xdc) to the project
add_files -fileset constrs_1 -norecurse <filename.xdc>
 
Simulation
Start the simulation
 
launch_simulation
Exit the simulation
 
close_sim
Restart the simulation
 
This restarts the simulation at time t=0 without exiting the simulation. You may want to run this command if you want to start the simulation over without relaunching the simulation tool.
 
restart
Run the simulation
 
run 10 ns
Force a value on a signal
 
add_force <signal_name> <value>
RTL Analysis
Generate schematic of RTL design:
 
synth_design -rtl -name rtl_1
Close schematic of RTL design:
 
close_design

TCL Examples
 Here is a basic compilation script that will compile all the HDL files in the current directory. It is in classical non-project mode and gives a starting point for a script you could create for your needs.

# Define a procedure (function)
# It will compile all the .sv, .v, and .vhd files in a directory.
# top is the name of the top level module in the design
proc compile {top} {
	puts "Closing any designs that are currently open..."
	puts ""
	close_project -quiet
	puts "Continuing..."
 
	# Create a design for a specific part
	link_design -part xc7a100t-csg324-3
   
	# Compile any .sv, .v, and .vhd files that exist in the current directory
	if {[glob -nocomplain *.sv] != ""} {
        	puts "Reading SV files..."
        	read_verilog -sv [glob *.sv]
	}
	if {[glob -nocomplain *.v] != ""} {
        	puts "Reading Verilog files..."
        	read_verilog  [glob *.v]
	}
    if {[glob -nocomplain *.vhd] != ""} {
        	puts "Reading VHDL files..."
        	read_vhdl [glob *.vhd]
	}
 
	puts "Synthesizing design..."
	synth_design -top $top -flatten_hierarchy full
   
	# Here is how you add a .xdc file to the project
	read_xdc $top.xdc
   
	# You will get DRC errors without the next two lineswhen you
	# generate a bitstream.
	set_property CFGBVS VCCO [current_design]
	set_property CONFIG_VOLTAGE 3.3 [current_design]
 
	# If you don't need an .xdc for pinouts (just generating designs for analysis),
	# you can include the next line to avoid errors about unconstrained pins.
	#set_property BITSTREAM.General.UnconstrainedPins {Allow} [current_design]
 
	puts "Placing Design..."
	place_design
   
	puts "Routing Design..."
	route_design
 
	puts "Writing checkpoint"
	write_checkpoint -force $top.dcp
 
	puts "Writing bitstream"
	write_bitstream -force $top.bit
   
	puts "All done..."
 
	# You might want to close the project at this pint, but probably not
	#close_project
 
	}
```

A Simple Design Analyzer Script
To illustrate some other functionality, here is a script that will print out a report on the currently open design:
```tcl
# Print the size statistics of an open Vivado design to the specified file.
# Specifically, the number of Cells, number of nets, number of sites, and
# the cell type distribution is printed.
# This may be useful to understand the size of designs being used for
# benchmark purposes.
proc print_cell_statistics { {filename "cell_stats.txt"} } {
   
	set fp [open $filename w]
   
	puts $fp "Benchmark: [get_property TOP [get_design]]"
	puts $fp "----------------------"
	#print size statistics
	puts $fp "\tCell Count: [llength [get_cells -hierarchical -quiet]]"
	puts $fp "\tNet Count: [llength [get_nets -hierarchical -quiet]]"
	puts $fp "\tSite Count: [llength [get_sites -filter IS_USED -quiet]]\n"
 
	#print distribution statistics
	puts $fp "\tCell Distribution: "
	set cell_distribution_map [generate_cell_distribution_dictionary]
   
	dict for {group cell_list} $cell_distribution_map {
    	puts $fp "\t\t$group: [llength $cell_list]"                                    
	}
   
	close $fp
}      
 
# Helper function used in print_cell_statistics
proc generate_cell_distribution_dictionary { } {
	set cell_dictionary [dict create]
   
	foreach cell [get_cells -hierarchical]  {
    	dict lappend cell_dictionary [get_property PRIMITIVE_GROUP $cell] $cell
	}
   
	return $cell_dictionary
}
```

----------------------------------
Initially created by Ryan Johnson, June 2020.