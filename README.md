# SV06_SKR_3_EZ_Klipper
My Klipper config for the Sovol SV06 with a SKR 3 EZ board.

It includes KAMP and Z_TILT_ADJUST + Display.
Based of this ones: 
- https://github.com/Pr20100/SOVOL-SV06-Klipper-profile
- https://github.com/bassamanator/Sovol-SV06-firmware

Use this case( also is in this one i based my hw install):
- https://www.printables.com/model/382629-sovol-sv06-skr-3-ez-mainboard-case-upgrade

- I use a meanwell lrs-350-24 powersupply, and all my "bushes" are ORIGINAL Igus Drylin RJ4JP-03-08(for the bed and gantry) & RJ4JP-01-08(For the Z's), i do not recommend that amazon ones where you get a pack of 10 for almost nothing, the tolerances on them are not good!
- Also added the bearing 688ZZ to the leadscrews.
- In drivers.cfg you notice in Z and Z1 the run_current are diferents, that is because my left Z stepper is stronger than the right one and if i set it to 0.700 like the right one it will get really hot,
and if i set the right one to 0.600 like the left one, the left was faster than the right one causing Z binding and the grantry be out of level.
- So play with the run_current on the Z's, i do not recommend go higher than 0.800... check you stepper temps...
- Also do not touch stealthchop_threshold leave at 99999.

- I will try later to include some pictures of the hw install.

@@@@@@@@@@ GCODE FOR SLICER START / END PRINT MACROS @@@@@@@@@

#### PRUSASLICER ####
in Printer settings / General/
Gcode flavor : KLIPPER

in Printer settings / Custom Gcode
  - START GCODE :
START_PRINT EXTRUDER=[first_layer_temperature] BED=[first_layer_bed_temperature]
  - END GCODE :
END_PRINT

#### SUPERSLICER #### 
in Printer settings / General/
Gcode flavor : KLIPPER

in Printer settings / Custom Gcode
  - START GCODE :
START_PRINT EXTRUDER=[first_layer_temperature] BED=[first_layer_bed_temperature]
  -  END GCODE :
END_PRINT

#### ORCA SLICER #### 
in Printer settings / Machine G-CODE/
Gcode flavor : KLIPPER

in Printer settings / Custom Gcode
  - START GCODE :
START_PRINT EXTRUDER=[first_layer_temperature] BED=[first_layer_bed_temperature]
  -  END GCODE :
END_PRINT

#### CURA #### 
in top menu Settings / Manage printers / Printers / select your printer then Machine settings

  - START GCODE :
START_PRINT EXTRUDER={material_print_temperature_layer_0} BED={material_bed_temperature_layer_0}
  - END GCODE :
END_PRINT

