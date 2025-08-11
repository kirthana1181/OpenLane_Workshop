# Working in Magic - basic introduction to layers and lef using Inverter
- To open magic, the command in terminal under the 'openlane/vsdstdcelldesign/' directory containing .mag file of inverter:
'magic -T sky130A.tech sky_inv.mag'(the name of inverter mag file is 'sky_inv').
- The below image represents the transistor-level view of Inverter in magic.

<img width="842" height="539" alt="image" src="https://github.com/user-attachments/assets/957a9f64-1603-4eb7-8e0d-ea165acb6232" />

- In magic, the root cell box is defined as : <width> x <height> (llx,lly),(urx,ury) <area> (unit square)
