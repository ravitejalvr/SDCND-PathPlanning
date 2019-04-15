# CarND-Path-Planning-Project

Path Planning is the process in the Self Driving Car where the optimal path between two points is found.

The basic process is as follows:

- Get a Prediction of new state based on current state

- Expland the state obtained to generate trajectory

- Caluculate loss function and select the optimal path based on the result of the loss function

## Introduction

This work is done as part of Udacity Self-Driving Car NanoDegree program, Term-3 Project-2. In this project, we develop and implement a Path Planning algorithm in Highway conditions such that the car is able to change lanes, speed up, slow down etc. However, the car has to follow the below rules:

- The car should try to maintain the maximum speed of 50 mph

-  Car Should not move out of Drivable spaces and should not have collision with other vehicles

- TCar should complete one complete tun of the highway 

- Total Acceleration and Jerk should be less than 10 m/s.s and 10m/s.s.s respectively.
     
Frenet Coordinates are used as the car is driving in lanes which x and y coordiantes are not uniform. The s and d values specity corresponsing longitudinal and lateral values.
    
### Detecting Other Vehicles

For planning the path, continuous estimation of vehicles is necessary. The following detections are done in this project.

- Detect if there is Vehicle in front

- Detect if there is Vehicle blocking Left Lane

- Detect if there is Vehicle blocking Right Lane

### Intended Behavior Plan

Based on Detedted Vehicles in Host, Left and Right Lanes, decisions for behavior are taken. 

- If vehicle speed is at maximum speed, no further action is taken. 
   
- The vehicle's speed is below the maximum sspeed, it accelerates to maximum speed as long as there is no collision with other vehicles.

- Detect if there is a chance of collision. Change lanes / decrease speeds is collision is possible
   
If there is a chance of collision:

  - Change Lanes if room is available in Right Lane / Left Lane
  - Reduce speed if no lane change is possible
  
### Trajectory Generation

This is the process used for generating the trajectory of the vehicle:

- Select five positions of Vehicles (Last two positions in the previous data, and three positions at 30, 60, 90m in front), 

- Use Spline to generate the corresponding trajectory

- Calculate the specific s, d values of the trajectory based on the generated trajectory 
  
 ### Parameters used:

- x -  The car's x position in map coordinates

- y -  The car's y position in map coordinates

- s -  The car's s position in frenet coordinates

- d - The car's d position in frenet coordinates

- yaw -  The car's yaw angle in the map

- speed -  The car's speed in MPH

- previous_path_x - The previous list of x points previously given to the simulator

- previous_path_y -  The previous list of y points previously given to the simulator

- end_path_s - The previous list's last point's frenet s value

- end_path_d -  The previous list's last point's frenet d value
