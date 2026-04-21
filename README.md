# Multi-Switch Flow Table Analyzer (SDN Project)

---

##  Project Description
This project demonstrates analysis of flow tables in a Software Defined Network (SDN) using Mininet and POX controller.  
The network consists of multiple switches and hosts, and traffic is generated to observe how flow rules are installed and used.

---

##  Objective
To analyze flow table entries in multiple switches and understand how packets are forwarded in an SDN environment.

---

##  Tools Used
- Mininet
- POX Controller
- Open vSwitch (OVS)
- Ubuntu

---

##  Topology
Linear topology with:
- 3 Switches (s1, s2, s3)
- 3 Hosts (h1, h2, h3)

---

##  Steps to Run

### 1. Start Controller
```bash
cd ~/pox
./pox.py forwarding.l2_learning
```

### 2. Start Mininet
```bash
sudo mn --topo linear,3 --controller=remote
```

### 3. Generate Traffic
```bash
h1 ping h2
h1 ping h3
h3 ping h1
```

### 4. Analyze Flow Tables
```bash
sh ovs-ofctl dump-flows s1
sh ovs-ofctl dump-flows s2
sh ovs-ofctl dump-flows s3
```

---

##  Output Explanation
- **n_packets** → Number of packets matched by the rule  
- **n_bytes** → Total data transferred  
- **actions** → Defines how packets are forwarded  

---

##  Key Observations
- Flow rules are installed dynamically by the controller  
- Only switches handling traffic will have active flow entries  
- Packet count helps identify active vs inactive flows  

---

##  Conclusion
The project successfully demonstrates how flow tables work in an SDN environment and how traffic is managed across multiple switches.
