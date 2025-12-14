## Lab 16 – Verify IP Parameters for Mac OS (GUI)

### Lab Objective
Verify IP configuration parameters on a macOS host using the graphical user interface (GUI), including IPv4 address, subnet mask, default gateway, DNS servers, and DHCP behavior.

---

### Execution Environment
This lab was completed using a browser-based virtual desktop environment due to the lack of native macOS hardware. The environment provides a macOS-style graphical network configuration interface suitable for validating host-side IP parameters.

---

### Network Configuration (GUI)

![Mac OS IP configuration window showing IPv4 address, subnet mask, and gateway](./screenshots/lab16-mac-ip-config.png)

The following IPv4 parameters were observed via the GUI network settings panel:

- **IP Address:** 192.168.1.2  
- **Subnet Mask:** 255.255.255.0  
- **Default Gateway:** 192.168.1.3  
- **Addressing Method:** Manual (Static)  
- **DNS Servers:** Not configured (static configuration)

---

### Network Settings Overview

![Mac OS network settings overview showing wired connection](./screenshots/lab16-network-settings.png)

The active wired network interface was selected from the Network settings panel to verify interface status and IP assignment.

---

### DHCP Lease Renewal (macOS Concept)
On a native macOS system, renewing a DHCP lease is performed via the following GUI path:

System Settings → Network → <Active Interface> → TCP/IP → Renew DHCP Lease

This action forces the host to request updated IP configuration parameters from the DHCP server, including:
- IPv4 address
- Subnet mask
- Default gateway
- DNS servers

---

### Platform Limitation
The virtual desktop environment used does not expose a macOS-specific **“Renew DHCP Lease”** button. DHCP lease management is handled automatically by the underlying network manager, and manual renewal via GUI is not available in this environment.

This limitation does not affect the learning objective of the lab, which is to understand **where and how IP parameters are verified and renewed on macOS systems**.

---

### Verification Summary
- Successfully verified IPv4 addressing parameters via GUI
- Confirmed subnet mask and default gateway values
- Documented DHCP lease renewal process conceptually
- Accurately documented platform limitations

---

### Lab Takeaway
This lab reinforces host-side IP verification skills on macOS systems, emphasizing GUI-based inspection of network configuration and an understanding of DHCP lease renewal behavior in real-world troubleshooting scenarios.
