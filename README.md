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
