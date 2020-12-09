# ME314-Final-Project

# Overview

This is a default project "Jack/Dice in the box" for ME314 Machine Dynamics at Northwestern University. The goal of this project is to simulate a box bouncing inside of a moving box. The drawing below shows the configuration and transformation of frames I used. For simulation, I simulate the dice starting at the center of the box with zero initial velocity and zero theta for 5 seconds with a time step of 0.01s.

# Drawing and transformation of the modeling system

![2020-12-08 10-57](https://user-images.githubusercontent.com/70287453/101658699-defae280-3a0a-11eb-86d6-e8e3f1ea89b1.jpeg)

* Transformations of frame in the program are list below:

      g_WB1: The transformation from world to center of the box(0, x_box, y_box)

      g_WB2: The transformation from center of the box to final box frame(theta_box,0, 0)

      g_WD1: The transformation from world to center of the dice(0, x_dice, y_dice)

      g_WD2: The transformation from center of the box to final dice frame(theta_dice,0, 0)

      g_WB: The transformation from world to box frame.(g_WB1*g_WB2)

      g_WD: The transformation from world to dice frame.(g_WD1*g_WD2)

      g_BD: Transformation from box frame to dice frame.(g_WB^-1 *g_WD)
      
![Screenshot from 2020-12-08 11-05-24](https://user-images.githubusercontent.com/70287453/101659321-8b3cc900-3a0b-11eb-8816-d57be1043692.png)

#  Calculation Description

* Eular-Lagrange Equations:

To calculate the EL-Equations, the first thing to do is to find the kinetic and potential energy of the
whole system (Box and Dice). The velocity of the dice and box can be calculated by their rigid-body
transformation from world frame(g_WB and g_WD). The inertia matrices is a diagonal matrix of
vector [1, 1, J_box/J_dice] and I used 1 for both inertia of box and dice (Assume the center of the mass
is the center of the geometry). The kinetic energy then can be calculated after finding the velocity and
inertia matrices. The potential energy of the system is also calculated from the rigid-body
transformation of objects in world frame.
