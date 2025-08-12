# Working in Magic
    # Command to download the lab files
        wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
    # Since lab file is compressed command to extract it
        tar xfz drc_tests.tgz
    
    # Change directory into the lab folder
        cd drc_tests
    
    # List all files and directories present in the current directory
        ls -al
    
    # Command to view .magicrc file
        gvim .magicrc
    
    # Command to open Magic tool as GUI
        magic -d XR &

Creating a contact using Magic
<img width="698" height="444" alt="image" src="https://github.com/user-attachments/assets/d2a27e0a-b1d5-4ab1-bd2a-b1a7947e8c1f" />

# Error in Poly.9 Spacing shown in vim editor
<img width="603" height="398" alt="image" src="https://github.com/user-attachments/assets/2ee6c9ef-f936-4ff4-a2b8-c06180c4f4f0" />

The DRC rule was changed in the vim editor, to try and remove the drc rule check error, for _npolyres_
<img width="921" height="449" alt="image" src="https://github.com/user-attachments/assets/611eaa31-a22a-4c21-b188-9a30db78ca88" />

- To copy, select using cursor the component to copied, and prss key C and to paste press C at another area, using area cursor.
- To delete, select component by pressing key S from keyboard, and press key D
- To paint, select an area using cursor, and using centre button of the mouse, click on the colour from the right side-panel.

# Describe DRC error as a geometrical construct

This is the result of the violation of the error in which the area number mentioned(here 1030) is the value by which nwell must overlap with dnwell on the inside.

<img width="668" height="401" alt="image" src="https://github.com/user-attachments/assets/eeee22a1-46bf-41aa-afb6-36ca8d15aa4e" />

<img width="893" height="417" alt="image" src="https://github.com/user-attachments/assets/8c375562-86d4-4b4a-80e7-dd7f454190ee" />

- Since only one style can be viewed at a time, as per that style, the changes are required to be made on using **_cif ostyle_**
- Therefore, it's best to always use the simple edge-based DRC rules
- The style of processing used for DRC, can be checked under the section **style DRC** in the vim editor of that sky130.tech file. (In our case they are styles - _fast_(works on back-end metal layers, and large digital designs without allowing interfering Magic to check the metal layers below), _full_ (checks everything i.e all the metal layers, bottom and top))
- The commands to change between these drc styles in the Magic design Command Window are **drc style drc(fast)** and **drc style drc(full)**

<img width="808" height="470" alt="image" src="https://github.com/user-attachments/assets/6a0ce02c-ea38-44d6-88a2-5c5f72f22300" />

# Find missing or incorrect rules and fix them

**Rule:** (nwell.4)

- All n-wells will contain metal-contacted tap (rule checks only for licon on tap) . Rule exempted from high voltage cells inside UHVI. (Every nwell must have n-type layer contact, in magic called **ncontact** or **n_sc**)
- This rule is a CIF output rule, rather than a simple edge-based rule.

<img width="782" height="416" alt="image" src="https://github.com/user-attachments/assets/aa859df1-e19c-47e1-8484-04d17b29956b" />

<img width="869" height="460" alt="image" src="https://github.com/user-attachments/assets/aaf1c8bd-0771-4ffd-9f8a-1861eb3811d5" />

- The general idea of this rule is to take all the ntype contacts and expand the area to fill nwell below the layer. This is done using the cif operator : **bloat_all**. In our case, we basically filter out of the all the ntype contacts that contain nwell filled in, and the remaining are the erroneous ones.
- In the second drc check, the whole nwell4 is found to have error

<img width="905" height="410" alt="image" src="https://github.com/user-attachments/assets/61035078-fc80-45ca-8fb5-71662b28b43e" />

**The following image shows the error-nwells in the Magic Window:**(done by placing a contact in the Nwell)

<img width="860" height="470" alt="image" src="https://github.com/user-attachments/assets/b18e607d-41b6-4b95-8cef-e9d9b78c4956" />

Key points to remember:
1. Some rules are unimplemented because there are no layers yet to represent them (Eg: UHVI layer isn't represented in Magic, so they can't be implemented)
2. Some layers require specific cif command to view. For example, the n+ implant layer and p+ implant layer(nsd and psd respectively) to be viewed, after selecting the right DRC style to view them.
