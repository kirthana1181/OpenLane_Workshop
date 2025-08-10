# Congestion-aware Placement
1. Congestion takes place in OpenLANE takes place in two stages
2. To run placement in the flow.tck interactive environment, give the command - '% run_placement'.<img width="882" height="440" alt="image" src="https://github.com/user-attachments/assets/17d59599-96aa-402a-bf71-bfb4452a93b9" />

3. Under 'designs/picorv32a/10-08_16-13/results/placement', the Magic window is opened entering the .def file of the successfully generated placement of the synthesis run at the time 16:13 hrs and dated 10/08.
4. In this program, the overflow decreases over time(OVFL) for the placement to be right and the design to converge.
5. The placement generated file is opened in Magic as shown below:<img width="1916" height="723" alt="day2_magic_screenshot_proof_placement" src="https://github.com/user-attachments/assets/b5ceb4f7-ffa5-4a25-bc68-17f104d27036" />
<img width="959" height="502" alt="image" src="https://github.com/user-attachments/assets/2ace58fd-d46a-4d2e-8ab5-9d0a650a41de" />
6. PGN(Power Ground Network) is generally created during floorplan, but in OpenLANE it is being created after CTS, i.e just before Routing as PGN/PDN(Power Distribution Network).
