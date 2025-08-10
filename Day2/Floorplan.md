# 1. To run the floorplan
- In the TCL interactive, give command:'%run_floorplan'
- Precendence order : skywater pdk('sky130A_fd_sc_hd_config.tcl'), 'config.tcl'(under 'designs/runs'), 'README.md'(mentioned below)
<img width="948" height="475" alt="image" src="https://github.com/user-attachments/assets/6f100259-637a-439a-81f6-8975c5927598" />


# 2. The floorplan information directory under 'openlane/configurations'
- The following image describes the output of the command: 'less README.md', which displays the variables that can be set during synthesis flow, floorplan, and other steps of the VLSI-design flow. (For this 'openlane'>'configuration'>'README.md')
  
    <img width="1909" height="958" alt="day2_floorplan readme file" src="https://github.com/user-attachments/assets/4202c4ab-76bd-467b-bfc3-9c1a60a78137" />
- In the floorplan.tcl file, the default paramters which ae set for floorplan are shown, as in the screenshot attached below.
<img width="955" height="490" alt="image" src="https://github.com/user-attachments/assets/7f9e5574-787e-41e4-ac99-b3de0878489c" />
- Always the design parameter value mentioned in the README.md will follow the precedence order mentioned( the value in the pdk tcl file is the one copied onto README.md file as well, and has to be overwritten over config.tcl)
# 3. Calculating Die Area
- Under the results for floorplan ('designs/picorv32a/10-08_09_16/results/floorplan'), the command si run:'$less picorv32a.floorplan.def' (the .def file), which displays the locations and dimensions of the die.

  <img width="813" height="209" alt="image" src="https://github.com/user-attachments/assets/0485a1f8-1665-4a88-aeaf-aead17e1ce3e" />

- As shown in the figure below, the area of the die can be calculated using the values in the second parenthesis highlighted(**first** parentheses consists- **lower left X and Y** coordinates, **second** one denotes **upper right X and Y** values).
- The area of the die can be calculated using these latter X and Y as the product. Here:
-   Area = X x Y = 660685   ×   671405 = 4,43,58,72,12,425 square micron meters data-base units. (The unit is mentioned as microns, i.e 1 unit micron = 1000 data-base units.)
-   Rather Area = (660685/1000)   ×  (671405/1000) = 443587.212425 square micron meters
  
  <img width="959" height="470" alt="image" src="https://github.com/user-attachments/assets/0a82d91d-8534-4a8c-9804-d8eae4e8e2a2" />
