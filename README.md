# Cura-ABL-Klipper
my Start Gcodes

for Printer.cfg:
--------------------------------------
[gcode_macro G29]
gcode:
 BED_MESH_CALIBRATE
--------------------------------------


Basic Gcode standard heating:
--------------------------------------
; Ender 3 Custom Start G-code
G92 E0 ; Reset Extruder
G28 ; Home all axes
G29 ; ABL
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish
--------------------------------------

Heating Nozzle after Bedlevel
--------------------------------------
 ; Ender 3 Custom Start G-code
M190 S{material_bed_temperature} ; start heating the bed to what is set in Cura and WAIT
M104 S{material_print_temperature} ﻿T0 ; start preheating hotend WITHOUT wait to what is set in Cura
M280 P0 S160 ; BLTouch alarm release
G4 P100 ; delay for BLTouch
G28 ; home
G29 ; auto bed leveling
M190 S{material_bed_temperature} ; start heating the bed to what is set in Cura and WAIT
M109 S{material_print_temperature} ﻿T0 ; start heating hotend to what is set in Cura and WAIT
G92 E0 ; Reset Extruder

G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish 
--------------------------------------
