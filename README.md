# ⚡ Development of Hybrid Vehicle Powertrain Controller Using Stateflow  
**🚘 Real-Time Embedded Control Using Simulink, Stateflow & dSPACE MicroAutoBox**

This project demonstrates the design, simulation, and real-time validation of a **Hybrid Electric Vehicle (HEV) Powertrain Controller** using **Stateflow** in **Simulink**, deployed on a **dSPACE MicroAutoBox** via **ConfigurationDesk** and **ControlDesk**.

---

## 🧠 Project Overview

The HEV controller governs:
- **Driving Mode Selection**: Electric, Hybrid, or Engine-only
- **Torque Split Logic**: Between engine and motor
- **Battery Management**: SOC-based control with charge protection
- **Braking Logic**: Integration of regenerative and mechanical braking

The controller was simulated in Simulink/Stateflow and deployed in real-time using MicroAutoBox.

---


## 🧰 Tools & Technologies

| Tool               | Purpose                                                   |
|--------------------|-----------------------------------------------------------|
| 🧩 Simulink         | Plant modeling, input/output signal development           |
| 🔁 Stateflow        | Mode-based logic and control state machine                |
| 🧠 ConfigurationDesk| I/O configuration, signal routing, and hardware interface |
| 🎛️ ControlDesk      | Real-time signal tuning, monitoring, and data logging     |
| 🖥️ MicroAutoBox II  | Real-time embedded controller (DS1202)                    |
| 📊 MATLAB           | Post-processing and data analysis                         |

---

## 🔁 Control Features

- **EV Mode** – Pure electric drive during low-speed, high-SOC conditions  
- **Hybrid Mode** – Coordinated power delivery from engine and motor  
- **Engine Mode** – Activated during low SOC or high-speed conditions  
- **Regenerative Braking** – Captures kinetic energy to recharge the battery  
- **SOC-Based Control** – ChargeState and BatteryProtection flags for safety

---

## 🔧 Input/Output Configuration

| Signal Name            | Type             | Channel / Configuration     |
|------------------------|------------------|-----------------------------|
| APP                    | Analog Input     | AINx (Accelerator Pedal)    |
| BPP                    | Analog Input     | AINx (Brake Pedal)          |
| Vehicle Speed          | Simulated Input  | From plant model            |
| SOC                    | Simulated Input  | From battery subsystem      |
| Motor Torque           | Model Output     | Routed to ControlDesk       |
| Engine Torque          | Model Output     | Routed to ControlDesk       |
| Brake Torque           | Model Output     | Routed to ControlDesk       |
| Regen Torque           | Model Output     | Routed to ControlDesk       |
| ChargeState_Flag       | Boolean Output   | Digital Output (DOUT1)      |
| BatteryProtection_Flag | Boolean Output   | Digital Output (DOUT2)      |

---

## 🧪 How to Use

### 1. 📦 Simulink & Stateflow
- Open `HEV_Powertrain_Controller.slx` in MATLAB
- Review controller logic in the **Stateflow chart**
- Ensure input/output ports are mapped correctly for external interfacing

### 2. 🧠 ConfigurationDesk Setup
- Import the Simulink-generated `.sdf` into ConfigurationDesk  
- **Configure Signal Chain**:
  - Route analog inputs (APP, BPP) to model input ports  
  - Route model outputs (torques, flags) to digital/monitoring channels  
- Set signal data types (e.g., `double`, `boolean`) and define scaling if required  
- Build and deploy the application to **MicroAutoBox**

### 3. 🎛️ ControlDesk Integration
- Load the deployed `.sdf` or `.cdfx` file  
- Monitor live data: APP, SOC, torque outputs, mode transitions  
- Adjust setpoints and run dynamic drive-cycle simulations  
- Log data for analysis

---

## 📈 Learning Outcomes

✅ Design of real-time, state-based vehicle controllers  
✅ Integration of embedded systems with dSPACE MicroAutoBox  
✅ Signal routing and validation in ConfigurationDesk  
✅ Live data tuning, signal logging, and control validation in ControlDesk  
✅ HEV energy management strategies and torque control

---

## 📄 License

This project is provided for academic learning and demonstration purposes only.  
For reuse or citation, please contact the author.

---
