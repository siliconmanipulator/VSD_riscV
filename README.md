
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




## Day 3- Design library cell using Magic Layout and ngspice characterization

#### Cloning vsdstdcelldesign repository
Run 
```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
``` 
in openlane folder

Copy the sky130A.tech from magic tool folder to the newly clones directory (vsdstdcelldesign).

Now let's open inverter Layout in Magic

Run `magic -T sky130A.tech sky130_inv.mag &`

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/1.png)

#### Extracting SPICE list
Run the following command in Magic terminal (tkcon)
```bash
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```
#### Opening the SPICE file and editing

Run `vim sky130_inv.spice`

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/2.png)

#### Opening the SPICE file
Run `ngspice sky130_inv.spice` 
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/3.png)

#### Simulate SPICE in ngspice

Run `plot y vs time a`
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/4%20b4%20changing%20cap%20cap%20.2f.png)

Some peaks are coming in output.\
To remove peaks change cap load to 2 femto Farrad

#### Plot after changing cap load
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/5%20changing%20cap%202fF.png)

#### Rise Time

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/7.%2050_%20of%203.3.png)

#### Fall Time
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/8.%20fall%20time%20calc.png)

#### Propagation Delay (Cell Rise Delay)
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/9%20cell%20rise%20delay%20tpd%2050_%20change.png)

#### Cell Fall Delay
![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_3/10%20cell%20fall%20delay.png)






# Project Title

A brief description of what this project does and who it's for

## Day 4

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/1.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/2.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/3.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/4.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/5.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/6.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/7.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/8.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/9.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/10.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/11.png)

![](https://github.com/siliconmanipulator/VSD_riscV/blob/main/day_4/12.png)
