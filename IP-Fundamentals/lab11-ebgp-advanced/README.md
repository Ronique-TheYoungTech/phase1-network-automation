# Lab 11 — eBGP Neighbor Formation + Verification (Packet Tracer 2901)

## Lab Objective
Establish an **eBGP** peering between two routers (**R1 AS 100** and **R2 AS 200**) using **loopback-based neighbor addresses**, and verify BGP status using IOS show commands.

## Lab Purpose
This lab practices the fundamentals of:
- Building an eBGP relationship
- Advertising networks into BGP
- Verifying BGP neighbors and protocol state
- Documenting **Packet Tracer limitations** when valid IOS commands are not supported in the simulator

---

## Topology
- Two Cisco **2901** routers: **R1** and **R2**
- Physical link between routers using **GigabitEthernet**
- Loopbacks used to represent advertised/peering endpoints

> ✅ Screenshot:
- `screenshots/lab11-topology.png`

---

## IP Addressing Plan

### R1
- **G0/0:** `192.168.10.1/24`
- **Loopback1:** `192.168.1.1/24`
- **Loopback100:** `192.168.100.1/24`

### R2
- **G0/1:** `192.168.10.2/24`
- **Loopback1:** `192.168.2.1/24`
- **Loopback200:** `192.168.200.1/24`

---

## Configuration Steps

### 1) Configure Hostnames (R1 / R2)
> ✅ Screenshots:
- `screenshots/r1-hostname-config.png`
- `screenshots/r2-hostname-config.png`

---

### 2) Configure Interfaces + Bring Links Up

#### R1 — Interface + Loopbacks + Static Route
> ✅ Screenshot:
- `screenshots/r1-int-config.png`
- `screenshots/r1-loopback-config.png`

Example (reference):
```cisco
conf t
 hostname R1
 interface g0/0
  ip address 192.168.10.1 255.255.255.0
  no shut
 interface lo1
  ip address 192.168.1.1 255.255.255.0
 interface lo100
  ip address 192.168.100.1 255.255.255.0
 ip route 192.168.200.0 255.255.255.0 192.168.10.2
end
```
R2 — Interface + Loopbacks + Static Route

✅ Screenshot:

screenshots/r2-int-config.png

screenshots/r2-loopback-config.png

Example (reference):
conf t
 hostname R2
 interface g0/1
  ip address 192.168.10.2 255.255.255.0
  no shut
 interface lo1
  ip address 192.168.2.1 255.255.255.0
 interface lo200
  ip address 192.168.200.1 255.255.255.0
 ip route 192.168.100.0 255.255.255.0 192.168.10.1
end

3) Configure eBGP
R1 — BGP AS 100

✅ Screenshot:

screenshots/r1-ebgp-config.png

Example (reference):
conf t
 router bgp 100
  neighbor 192.168.200.1 remote-as 200
  network 192.168.10.0 mask 255.255.255.0
  network 192.168.1.0  mask 255.255.255.0
end

R2 — BGP AS 200

✅ Screenshot:

screenshots/r2-ebgp-config.png

Example (reference):
conf t
 router bgp 200
  neighbor 192.168.100.1 remote-as 100
  network 192.168.10.0 mask 255.255.255.0
  network 192.168.2.0  mask 255.255.255.0
end

Verification
1) Confirm BGP Neighbor State

✅ Screenshots:

screenshots/r1-bgp-verification.png

screenshots/r2-bgb-verification.png

Commands used:
show ip bgp summary

2) Confirm Routing Protocol Status

✅ Screenshots:

screenshots/r1-ip-protocol-verification.png

screenshots/r2-ip-protocol-verification.png

Commands used:
show ip protocols

3) Check BGP Routes (If Supported)

✅ Screenshots:

screenshots/r1-route-bgp-verification.png

screenshots/r2-route-bgb-verification.png

Commands used:
show ip route bgp


4) Ping Testing (Loopback Source)

✅ Screenshots:

screenshots/r1-ping-source-loopback.png

screenshots/r2-ping-source-loopback.png

Attempted command:
ping <destination> source loopback1

Packet Tracer Limitations Observed (Important)

Packet Tracer does not fully support all IOS features/commands on the 2901 platform.
Some commands returned “Invalid input”, but that does NOT mean the command is wrong in real Cisco IOS — it means the simulator is limited.

Unsupported / Rejected Commands Observed

Examples that threw errors in Packet Tracer:

neighbor <ip> update-source loopbackX

neighbor <ip> ebgp-multihop <n>

neighbor <ip> timers <keepalive> <hold>

neighbor <ip> password <value>

ping <ip> source loopbackX

✅ Key takeaway:

Valid IOS commands can still fail in Packet Tracer due to feature limitations.
For real-world behavior, labs should be validated in tools like GNS3 / EVE-NG / CML, or on actual IOS images/hardware.

