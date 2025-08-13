# Autoware-with-Carla-creating-bridge-with-ROS2

This project establishes a **bridge** between the **CARLA Simulator (v0.9.15)** and **Autoware** using **ROS 2**.  
It allows sensor data, vehicle control commands, and simulation information to be exchanged seamlessly between CARLA and Autoware, enabling autonomous driving experiments in a high-fidelity simulated environment.

---

## 📌 Requirements

To run this project, you will need:

- **CARLA** 0.9.15  
- **ROS 2** (Humble or compatible)  
- **Autoware** (Humble)  
- **Docker**  
- **Rocker** (for running GUI applications inside Docker containers)  

---

## 🚀 Steps to Run

### 1️⃣ Launch CARLA 0.9.15

```bash
# CARLA run command here
./CarlaUE4.sh -carla-rpc-port=1403 -quality-level=Low -prefernvidia
```

### 2️⃣ Launch the Bridge
Docker container for the tumgeka/carla-autoware-bridge:latest image, which connects CARLA and Autoware via ROS 2.
```bash
# Docker container command here
docker run -it -e RMW_IMPLEMENTATION=rmw_cyclonedds_cpp --network host tumgeka/carla-autoware-bridge:latest
```
```bash
# Bridge Launch command here
ros2 launch carla_autoware_bridge carla_aw_bridge.launch.py port:=1403 town:=Town10HD
```
### 3️⃣ Launch the Bridge
Docker image for autoware humble
```bash
# Command for the image of autoware humble
 docker pull ghcr.io/autowarefoundation/autoware:humble-2024.01-cuda-amd64
```
Run the autoware humble container
```bash
#Command command for autoware humble container
rocker \
  --x11 \
  --network host \
  --env RMW_IMPLEMENTATION=rmw_cyclonedds_cpp \
  --env LIBGL_ALWAYS_SOFTWARE=1 \
  --volume /home/ageda/projects/CARLA_0.9.15/Saleh/Carla-Autoware-Bridge:/workspace \
  -- \
  ghcr.io/autowarefoundation/autoware:humble-2024.01-cuda-amd64
```
Clone the CarlaT2 repository
```bash
#Cloning Carlat2
git clone https://github.com/TUMFTM/Carla_t2.git
```
Get the carla-autoware-bridge map from this link: https://syncandshare.lrz.de/getlink/fiBgYSNkmsmRB28meoX3gZ/

Launch Autoware
```bash
#Launch Autoware

ros2 launch autoware_launch e2e_simulator.launch.xml vehicle_model:=carla_t2_vehicle sensor_model:=carla_t2_sensor_kit map_path:=<path to /wsp/map>
```
