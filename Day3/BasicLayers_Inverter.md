# Working in NGSpice and Magic - basic introduction to layers and lef using Inverter
- To open magic, the command in terminal under the 'openlane/vsdstdcelldesign/' directory containing .mag file of inverter:
'magic -T sky130A.tech sky_inv.mag'(the name of inverter mag file is 'sky_inv').
- The below image represents the transistor-level view of Inverter in magic.

<img width="842" height="539" alt="image" src="https://github.com/user-attachments/assets/957a9f64-1603-4eb7-8e0d-ea165acb6232" />

- In magic, the root cell box is defined as : <width> x <height> (llx,lly),(urx,ury) <area> (unit square)
- To extract the design, in the command window of Magic, enter: 'extract all'. This creates a .ext file, within the same file location. (in our case: 'sky130_inv.ext')
- This .ext file is used to produce a spice file, using the command:'exttospice', as shown below(here we are extracting the parasitic capacitance values)
- (Drain,gate,source, substrate) = (ad,pd,as,ps); (w,l) = width,length of the corresponding transistor.
  
<img width="662" height="437" alt="image" src="https://github.com/user-attachments/assets/c5d8674c-58e4-4182-8838-e29cb80c53db" />

- The generated spice is then opened in the vim editor, using the command:'vim sky130_inv.spice'(the spice file generated is _sky130_inv.spice_), as shown.
- The nmos is denoted with _..._nfet_..._ similarly for pmos(in the naming _...pfet..._)
  
  <img width="857" height="518" alt="image" src="https://github.com/user-attachments/assets/204ac0d3-e96e-4e2b-8e4a-d15ac37f0dfe" />


- Creating the spice deck, editing in vim editor:(generated spice file)
  
  <img width="613" height="520" alt="image" src="https://github.com/user-attachments/assets/77b17b12-e87a-4e0e-af1f-6035955b93d8" />

- To run in ngspice, we give the command :'ngspice <source_file>' (here source file - sky130_inv.spice). The below is the code present in the spice file
  <img width="617" height="343" alt="image" src="https://github.com/user-attachments/assets/ac94c271-6dbd-4bcb-989e-f4d4bce86364" />

  <img width="728" height="475" alt="image" src="https://github.com/user-attachments/assets/26372d58-da87-4231-9352-a26ac1587057" />

-The below is the output waveform generated - Vout Vs time
  <img width="959" height="468" alt="image" src="https://github.com/user-attachments/assets/8264f66f-64d9-4f71-9917-73d2e2b2a0b5" />
-  the spike present can be eliminated by increasing the C4 (the capacitance between nmos and gnd)
# Characterize the Inverter Cell
- Determined by 4 values :
  1. Rise transition time
  2. Fall Transition time
  3. Propagation delay(cell rise delay)
  4. Cell Fall Delay.
- Here the **_Rise transition time = time at 80% of output val - time at 20% of the output val_** = 2.2ns -2.6 ns =0.04ns
  (below image for 20% of output val(~0.66V, time =2.16ns)
  <img width="791" height="251" alt="image" src="https://github.com/user-attachments/assets/8c85d65c-5e11-47cf-aa0b-84d4a8a1701e" />
  (similarly, 80% of output val(~3.3V) is 2.64V, time =2.2ns)
  <img width="740" height="462" alt="image" src="https://github.com/user-attachments/assets/7595ec3f-b4c7-4650-8936-22a1688eae67" />
**_Propagation Delay - time taken to reach 50% of o/p val-time taken to reach 50% of i/p val_**
   = 2.18029ns -2.14986ns= 0.03043ns
  
  <img width="320" height="185" alt="image" src="https://github.com/user-attachments/assets/d5ba1d0f-1ac2-40c0-84c3-4ca91b0386ef" />
  <img width="502" height="263" alt="image" src="https://github.com/user-attachments/assets/e5b2e2c9-25f7-4e62-9b1e-6acc1028a73d" />


