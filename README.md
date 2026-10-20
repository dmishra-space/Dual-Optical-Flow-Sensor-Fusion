# Dual Optical-Flow Sensor Fusion: GPS-free position hold for a PX4 drone

**Project page with flight video:** https://dmishra-space.github.io/Dual-Optical-Flow-Sensor-Fusion/

Master's thesis project by Divyanshi Mishra (MSc Aerospace Engineering, University of Pisa), carried out at ZHAW Zurich University of Applied Sciences (Nov 2025 - Feb 2026).

## Result
- About **43 s of autonomous position hold with GPS disabled**
- Attitude error held within **±2°** during the hold

## What it does
- **Controller:** ROS2 offboard position-hold node in Python on a Raspberry Pi 4, with cascaded position and velocity loops commanding PX4's attitude and rate loops on a Pixhawk 4.
- **Sensor fusion:** quality-weighted fusion of two Holybro H-Flow optical-flow sensors, sent to PX4's EKF2 through a custom uORB topic (`FusedOpticalFlow`) for sensor redundancy.
- **Safety:** three-layer fallback (estimator-validity checks, communication monitoring, safe-hover fallback).
- **Logging:** logger and dashboard nodes for reviewing every flight.

## Stack
PX4 v1.14.3 · ROS2 Humble · Pixhawk 4 · Raspberry Pi 4 · two Holybro H-Flow sensors · Python

## Repository structure
```
ros2_nodes/          dmux_node.py, fusion_node.py, controller_node.py, logger_node.py, dashboard_node.py
ros2_package/        ROS2 package files (package.xml, setup.py, setup.cfg)
px4_modifications/   FusedOpticalFlow.msg (custom uORB message)
scripts/             start.sh, Makefile, uav_fusion.yml
index.html, *.mp4    project page and flight video (GitHub Pages)
```

## Author
Divyanshi Mishra · [LinkedIn](https://www.linkedin.com/in/divyanshi-mishra-9a928426b) · divyanshimishrayo1@gmail.com
