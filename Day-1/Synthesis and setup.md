# The steps to design a File are:

# 1. Setting up Data for design file using command after opening docker:
**To open the docker, for entering prompts in the docker bash:
$ docker**
- **Then open the flow interactive terminal using command : '$ ./flow.tcl -interactive'**
- **This opens the openlane interactive command environment in bash**
- **TO prepare the design file, use the following command in the bash as**
**% prep -design picorv32a**
- **Following this the message displayed is '[INFO]:Preparation complete'**

# 2. To review files after design prep and run synthesis
- **under 'designs/picorv32a' there is the 'runs' folder, which contains all the results and information of the synthesised file stored under the name of the created date and time(eg. '12-08_10-49')**
- **under this runs folder is where we can see all the other related files to 'runs' namely - 'tmp','logs','results','reports','config.tcl', and 'cmds.log'**
- **under 'tmp' is the .lef file that contains all the information about layers, vias and the cell-level design information under the heading 'MACRO sky 130...'(eg. "merged.lef")**
- **The commands file 'cmds.log' contains a record of all the commands executed over the file**
- **The results are stored in the 'results' folder, where further it is stored as 'reports' generated and the 'log' file**
- **An important file is the config.tcl, which contains the information on the default parameters used in the "run"**
- **Open the 'config.tcl' file in the terminal using command: 'less config.tcl', where we can view all the information about properties of the design**
- **To RUN the SYNTHESIS, under the flow interactive run the command: '%run_synthesis'**
# 3. Steps to characterize the results
- **After the Synthesis is completed the message is displayed '[INFO]:Synthesis was successful'**
  <img width="930" height="458" alt="image" src="https://github.com/user-attachments/assets/4555addf-761f-4056-9291-e559bf58cbb8" />

- **The flop ratio(count of flops) is determined as - (number of flops(basically T flip-flop))/(total number of cells)**
  for example:
  given- 'sky130_fd_sc_hd_dfxtp_4 _**1634**_' and 'Number of cells:  _**17323**_',
  the flop ratio is - 1634/17323 = 009432546325694163828436183109161
  in percentage comes as ~ 9.43% = Percenatage of DFFs in the cell area

  <img width="954" height="475" alt="image" src="https://github.com/user-attachments/assets/d09ca29f-6129-49e3-8869-05c8ee7d1b4a" />
  
# 4. The Results Folder
- Open the 'results/' folder, and further, open the 'synthesis/' folder
- To view the synthesised netlist, use command: 'less picorv32a.synthesis.v', where all the mappings are done.
- The timing reports are contained in the 'reports/' directory
  _**Note : To exit the terminal of any environment, press Q or enter':wq'**_
- To check the STA analysis report, 'runs/'>'{latest date_file}'>reports>synthesis>give command to open the '..stat.rpt'(eg: 'less 1-yosys_4.stat.rpt')

  <img width="958" height="503" alt="image" src="https://github.com/user-attachments/assets/899fc279-8fbe-43c4-84f7-489b2daa551b" />


