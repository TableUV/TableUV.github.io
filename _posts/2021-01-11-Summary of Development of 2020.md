---
title: Summary of the developments of 2020
categories: 
    -  General
author_staff_member: tsugumi
date: 2021-01-11 # needs to be a valid date (present or a past date)
---
<!-- Don't use Heading 1 -->

## Beginning of 2021
With an end to a challenging year to everyone, we all look forward for a bright and exciting year!

To get you all even more excited, the official website for the project has launched!
In this "Blogs" section, we will be posting the latest development progresses to keep you all updated. 

To begin with, the summaries of the development for each team are posted below. 
Feel free to leave a comment below with any questions!!

### Architecture Design
**Member** Jack
<img src="/images/blog/post1/soft-arch.png" alt="Software Architecture" class="landscape"/>
<img src="/images/blog/post1/hardware-arch.png" alt="Hardware Architecture" class="landscape"/>

### Mechanical
**Member** Jack

<img src="/images/blog/post1/mech_p2.png" alt="Mechanical P2" class="portrait"/>
<img src="/images/blog/post1/mech_p1.png" alt="Mechanical P1" class="portrait"/>

#### Summary
Prototype  V2.3.27 [327 Iterations]
- Fine tuned for the FDM Printer
- Still having trouble with  leakage issue. (wip)

#### What's next?

### Electrical
**Member** Tsugumi, Jerome 

#### Summary

The electrical team worked on the component selection, architecrture design, modelling &simulation, design calculation, and the schematic & layout design for the TableUV robot. By the end of the 2020, 7 custom PCBs designs were completed from scratch, and the gerber files were sent to be manufactured by PCBWay. 

Below are the 3D images of the PCB designs. 

<img src="/images/blog/post1/mcu_board.png" alt="MCU Board" class="small"/>
<img src="/images/blog/post1/driver_board.png" alt="Power & Driver Board" class="small"/>
<img src="/images/blog/post1/charger_board.png" alt="Battery Charger Board" class="small"/>
<img src="/images/blog/post1/tof_board.png" alt="ToF Sensor Board" class="small"/>
<img src="/images/blog/post1/ir_board.png" alt="IR Sensor Board" class="small"/>
<img src="/images/blog/post1/collision_board.png" alt="Collision Sensor Board" class="small"/>
<img src="/images/blog/post1/uv_array_board.png" alt="UV Sensor Array Board" class="small"/>


#### What's next?
The electrical team will be manufacturing the boards manually using hot plate and hand soldering once the compoenents and PCBs arrive. The boards will be tested on bench, and after any possible bugs/issues are solved, the firmware development will take in place. 

### Software 
**Member** Dong Jae

#### Summary
In terms of software, most of the work was based on creating a reliable simulation platform to test the functionality of the robot and also to serve as testing and understanding how the general high-level architecture of the robot will be organized.

Within Webots, different sensors were configured on to the robot with their parameters initialized to match the sensors that we are using in our actual robot to closely imitate the robot. The following snippet shows some of these initializations as an exmaple.

```
% TOF
TOF_FOV = 0.471;            %[rad]
TOF_WIDTH = 64;             %[px]
TOF_HEIGHT = 64;            %[px]
TOF_IS_SPHERICAL = false;
TOF_NEAR = 0.01;            %[m]
TOF_MIN_RANGE = 0.01;       %[m]
TOF_MAX_RANGE = 4;          %[m]
TOF_MOTION_BLUR = 0;
TOF_NOISE = 0;
TOF_RESOLUTION = -1;
```

Other then sensor initialization, the main focus was using the encoder data along with the IMU to perform localization of the robot. This required determining a kinematic model of the robot and the using the data to determine the robots pose with fair amount of accuracy. The pose estimation of the robot was compared to its true values as the simulation provides actual position and orientation of the robot.

<img src="/images/blog/post1/simulation_map.PNG" alt="MCU Board" class="landscape"/>
<img src="/images/blog/post1/simulation_orientation.PNG" alt="Power & Driver Board" class="landscape"/>

#### What's next?
Simulation will require implementation SLAM (simultaenouls localization and mapping) using the ToF sensors. Using this we would generate a global map that will be used to determine the path that the robot will take in order to clean the surface. Maybe some visual feedback of which areas of the table have been covered and which have not could be good addition to the simulation. When all of these features are implemented, we can measure the time taken for the robot to clean to better optimize for performance.









