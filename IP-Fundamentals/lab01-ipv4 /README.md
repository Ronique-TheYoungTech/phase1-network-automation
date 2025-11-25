🧭 Overview

This lab covers foundational IPv4 interface configuration, verification, and troubleshooting using Cisco 2901 routers with HWIC-2T modules. Interfaces used:

R1: Serial0/3/0 (DCE)

R3: Serial0/3/1 (DTE)

Direct point-to-point serial connection

🖥️ Network Topology

According to the PDF (page 2):

Two Cisco 2901 routers

Serial DCE/DTE connection

HDLC encapsulation

R1 (S0/3/0) ---- Serial Link ---- (S0/3/1) R3

 🎯 Lab Objectives

Configure Hostnames for R1 and R3

Configure IPv4 Addresses on Serial Interfaces

Configure Loopbacks on R3

Verify & Troubleshoot interface states and connectivity

🔧 Configuration Steps
Step 1 — Configure Hostnames

R1
![Router1 Hostname Configuration](./screenshots/r1-hostname-config.png)

```bash
conf t
hostname R1
end
```
R3
![Router3 Hostname Configuration](./screenshots/r3-hostname-config.png)

```bash
conf t
hostname R3
end
```
Step 2 — Configure Serial Interfaces
R1 — Serial0/3/0 (DCE)

(Clock rate required on DCE side)
![Clock Rate Configuration](./screenshots/r1-clockrate-config.png)

```bash
conf t
interface Se0/3/0
 clock rate 800000
 no shutdown
end
```




 
