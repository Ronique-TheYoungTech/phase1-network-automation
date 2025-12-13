# Lab 9 – PPP Authentication Using CHAP

## Lab Objective
The objective of this lab is to configure **PPP encapsulation with CHAP authentication** between two Cisco routers using serial interfaces, and to verify proper authentication, clocking, and link operation.

---

## Lab Topology

![PPP CHAP Topology](lab10-topology.png)

---

## Devices Used
- Cisco 2901 Router (R1)
- Cisco 2901 Router (R2)
- Serial DCE/DTE connection

---

## Step 1 – Configure Router Hostnames

### R1 Hostname Configuration
![R1 Hostname Configuration](r1-hostname-config.png)

### R2 Hostname Configuration
![R2 Hostname Configuration](r2-hostname-config.png)

---

## Step 2 – Configure Serial Interface IP Addresses

### R1 Serial Interface Configuration
![R1 Serial Interface Configuration](r1-int-config.png)

### R2 Serial Interface Configuration
![R2 Serial Interface Configuration](r2-int-config.png)

---

## Step 3 – Configure Clock Rate on DCE Side

### R2 Clock Rate Configuration
![R2 Clock Rate Configuration](r2-clockrate-config.png)

### Verify DCE and Clock Rate
![Show Controllers Verification](r2-show-controllers-verification.png)

---

## Step 4 – Enable PPP Encapsulation

### R1 PPP Encapsulation
![R1 PPP Configuration](r1-ppp-config.png)

### R2 PPP Encapsulation
![R2 PPP Configuration](r2-ppp-config.png)

---

## Step 5 – Configure CHAP Authentication

### R1 CHAP Configuration
![R1 CHAP Configuration](r1-chap-config.png)

### R2 CHAP Configuration
![R2 CHAP Configuration](r2-chap-config.png)

> **Note:**  
> - CHAP usernames must match the peer router hostname  
> - CHAP passwords must match on both routers  

---

## Step 6 – Debug PPP Authentication

### Enable PPP Authentication Debugging (R2)
![PPP Authentication Debug](r2-debug-ppp.png)

### Disable PPP Authentication Debugging (R2)
![PPP Authentication Undebug](r2-undebug-ppp.png)

---

## Step 7 – Verify PPP Operation

### R1 PPP Verification
![R1 PPP Verification](r1-ppp-verification.png)

### R2 PPP Verification
![R2 PPP Verification](r2-ppp-verification.png)

---

## Packet Tracer Limitations

- `debug ppp authentication` output is limited compared to real Cisco IOS
- CHAP challenge/response messages are not fully displayed
- `show ppp session` provides minimal information in Packet Tracer

These limitations are documented for future **network simulator development and comparison with real IOS behavior**.

---

## Key Commands Used

```text
encapsulation ppp
ppp authentication chap
ppp chap hostname <hostname>
ppp chap password <password>
username <peer> password <password>
clock rate 800000
show controllers serial
show ppp session
debug ppp authentication
undebug all

