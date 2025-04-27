---
title: "Real-Time Social Navigation Strategy using Deep Reinforcement Learning"
summary: "Local navigation for autonomous mobile robots in crowded environments, leveraging
deep reinforcement learning (DRL) techniques"
date: 2024-05-01
type: "docs"
math: false
tags:
  - "Human-Robot Interaction"
  - "Local Planning"
  - "ROS2"
  - "Turtlebot4"
image:
  caption: "The image is taken from a published paper"
---

## Introduction

Our approach to local navigation for autonomous mobile robots in crowded environments, leveraging
deep reinforcement learning (DRL) techniques and 2D laser scans. Traditional navigation methods
struggle in densely populated areas, often leading to constant replanning and inefficiency. To address
this challenge, recent research has turned to DRL-based solutions, which have shown promising
results in mapless navigation using 2D laser scans.
In our proposed approach, we integrate the perception of risk posed by the moving crowd into
the observation space of our DRL system. By focusing on the K most hazardous obstacles, identified
based on collision probability, the robot can better assess risk even in unfamiliar crowd behaviors.
This targeted attention enables effective navigation in high-density crowds while maintaining scala-
bility.
Furthermore, we enhance learning efficiency by incorporating local waypoints into the reward
function, aiding in global path planning. Through extensive evaluation across various crowd scenar-
ios, we compare our approach with a recent state-of-the-art DRL-based method, demonstrating its
effectiveness under similar test conditions.

## Experiment Setup
​The virtual environment for this project was designed to simulate real-world scenarios and train reinforcement learning models effectively. The setup involved:

Simulation Platform:

Gazebo 11: Used in combination with ROS2 Foxy to create a stable simulation environment.
Custom Worlds: Developed to replicate realistic and dynamic environments, including static and moving obstacles.
Custom SDF Models: Simulated human walking patterns using randomized cylinder animations to mimic crowd movement.
Training Worlds:

Arena World: Optimized for training in mixed static and dynamic obstacle environments.
Corridor World: Simulated a realistic, constrained environment for validation and testing.
Room World: Designed for dense crowd scenarios, primarily dynamic obstacle avoidance.
Robot Models:

Training started with Turtlebot3 Waffle Pi, transitioning to Turtlebot4 Lite for deployment due to its dimensional resemblance to the final robot.
Custom URDF files were created for compatibility with Gazebo 11 and ROS2 Foxy.
Simulation Features:

Environments included randomized dynamic obstacles and realistic terrain features.
The LIDAR sensor was integral to robot perception and state estimation.
Deployment Interface:

ROS2-based Communication: A unique ROS-DOMAIN-ID facilitated real-time updates and commands between the host PC and onboard Raspberry Pi 4.
Host PC Requirements: Ubuntu 22.04 with ROS2 Humble for advanced computing tasks, ensuring better performance than onboard hardware.
This environment setup ensured robust training, testing, and deployment of the socially aware navigation system, allowing the robot to navigate crowded, dynamic environments effectively.

## Approach
Our project utilizes Deep Reinforcement Learning (DRL) to enable socially aware navigation for mobile robots in crowded environments. The approach prioritizes safe, efficient, and dynamic movement in real-world scenarios, leveraging modern reinforcement learning algorithms like Twin Delayed Deep Deterministic Policy Gradient (TD3).

Problem Formulation:

The robot navigates using 2D laser scans, incorporating both static and dynamic obstacles into the observation space.
A novel perceived risk framework focuses on the K most hazardous obstacles in the environment, based on collision probability.
Observations include:
Static environment data from LIDAR.
Goal-relative metrics like distance and heading.
Obstacle data including positions and velocities of the most hazardous objects.
Action and Reward Spaces:

Action Space: Continuous linear and angular velocity commands for smooth and adaptive movement.
Reward Structure: Designed to guide behavior, it penalizes collisions, incentivizes reaching goals, and introduces waypoint-based rewards for efficient pathfinding.
Reinforcement Learning Algorithm:

TD3 Enhancements:
Dual Critic Networks to mitigate overestimation bias.
Delayed actor updates for stability.
Action noise for better exploration.
The model learns an optimal policy by interacting with custom dynamic environments during training.
Simulation and Deployment:

Training was conducted in Gazebo 11 with ROS2 Foxy, using custom environments tailored to social navigation challenges.
Deployment on Turtlebot4 Lite in real-world settings validated the system, highlighting its robustness and areas for improvement.

## Videos
{{< youtube fk1wiQEG_PE>}}

**Read more about it on  [!Report](RSS_Team7.pdf)**
















 




