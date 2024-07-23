
# NASSCOM-VSD_riscV_SoC Design

## Day- 1
Task: To calculate the Flop ratio after the systhesis of RTL of picorv32a.


### Step 1 - Invoking Openlane
Run `docker` in Openlane floder to activate bash\
Run ` ./flow.tcl -interactive` to invoke Openlane\
Include package `package require openlane 0.9`\
Run `prep -design picorv32a`. We are selecting the "picorv32a.v" design on which we will execute the RTL to GDS flow.

#### Invoking Openlane


![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_1/1%20invoking%20openlane.png)

After the preparation, we can see a new directory with today's date has created within 'runs' folder in 'picorv32a' folder.

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_1/2%20design%20setup.png)

#### Merging tech lef and cell lef

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_1/3%20merging%20of%20tech%20lef%20and%20cell%20lef.png)

#### Run Synthesis of the RTL
Run `run_synthesis`

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_1/4%20flop%20ratio.png)

` Flop % = 100*(no. of D-flip-flops/total no. of cells)
= 161300/14876 = 10.842969% `



## Day 2- Good floorplan and vs Bad floorplan and Itroduction to library cells

### Running Floorplan
Run `run_floorplan` in openlane bash
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/2%20Review%20Floorplan%20in%20Magic.png)

#### Calculating chip area
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/1%20die%20area.png)

#### Magic layout view
Run 
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/2%20Review%20Floorplan%20in%20Magic.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/3%20Instruction%20for%20using%20Magic.png)

Standard cells kept in the lower part of design
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/4%20Standard%20cells%20kept%20in%20the%20lower%20part%20of%20design.png)

#### Run Placement

Run `run_placement` in openlane bash\
To see layout after floorplan\
Run

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_2/5%20Placement%20in%20VLSI%20Design.png)
