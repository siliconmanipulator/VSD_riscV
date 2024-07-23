
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
