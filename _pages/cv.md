---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Download
======
* [Download PDF CV](/files/CV_sept_25.pdf)

Education
======
* MS by Research (Robotics), International Institute of Information Technology, Hyderabad (IIIT Hyderabad), Aug 2022 — Present  
  Supervisor: Dr. Spandan Roy; CGPA: 9.67/10.00
* B.E. (Electronics and Instrumentation), Birla Institute of Technology and Science, Pilani (BITS Pilani), Aug 2016 — July 2020

Experience
======
* Research Associate — Non-Linear Control for Aerial Manipulation, Aug 2022 — Present  
  Robotics Research Center, IIIT Hyderabad; Supervisor: Dr. Spandan Roy  
  - Working on adaptive, switched, and impedance control for aerial manipulators; analyzing compliance via impedance control.

* Teaching Assistant — Robotics: Dynamics and Control; Mechatronics System Design, Monsoon 2023; Spring 2025  
  IIIT Hyderabad; Supervisors: Dr. Nagamanikandan Govindan, Dr. Spandan Roy, Dr. Harikumar Kandath  
  - Drafted and graded assignments, quizzes, projects, and exam papers; conducted weekly doubt-clearing sessions.

* Research Associate — Controller Design for Super-maneuvering Fighter Aircraft, Jan 2020 — June 2020  
  EEE, BITS Pilani; Supervisor: Dr. Bijoy Krishna Mukherjee  
  - Designed H-infinity controller for F-18 HARV; tested Herbst maneuver in MATLAB/Simulink.

* Project Associate — Intelligent Fuzzy Controller for Flow Control Systems, Aug 2019 — Dec 2019  
  EEE, BITS Pilani; Supervisor: Dr. Puneet Mishra  
  - Designed Takagi–Sugeno fuzzy controller to mitigate stiction in pneumatic valves; compared with PID using IAE/ITAE indices.

Technical Skills
======
* Languages: Python, C/C++, MATLAB, Bash
* AI & Control Libraries: PyTorch, TensorFlow, SKRL, Stable-Baselines3, SciPy, Control Toolbox
* Middleware & Planning: ROS 1, ROS 2, MoveIt 2, micro-ROS
* Simulation & Flight: Gazebo, IsaacSim, IsaacLab, PX4 SITL/HITL, MAVROS
* DevOps & Tooling: Docker, Docker Compose, Git/GitHub, VS Code Dev Containers
* Hardware & Sensors: Pixhawk 2.4.8, CUAV X7, NVIDIA Jetson, Dynamixel XM430, OptiTrack MoCap, Robotous RFT60, LiDAR, RGB-D cameras

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Research Collaborations
======
* Simone Baldi — Southeast University, Nanjing; guest with DCSC, TU Delft
* Wei Pan — University of Manchester
* Jianguo Zhao — Adaptive Robotics Lab, Colorado State University
