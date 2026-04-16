# Network Delay Measurement using SDN (Mininet + Ryu)

## Problem Statement
This project demonstrates how Software Defined Networking (SDN) can be used to measure and analyze network delay between hosts. The goal is to observe how latency (RTT) changes under different network conditions.

## Tools Used
- Mininet
- Ryu Controller
- OpenFlow
- tc (traffic control)

## Topology
Two hosts (h1, h2) connected via a switch (s1) controlled by a remote SDN controller.

## Setup Steps
1. Start Ryu controller:
   ryu-manager controller.py

2. Start Mininet:
   sudo mn --controller remote --switch ovsk

## Execution

### Scenario 1: Normal Network
Command:
   h1 ping h2
Result:
   RTT ≈ 1–2 ms

### Scenario 2: Introduced Delay
Command:
   sudo tc qdisc add dev s1-eth1 root netem delay 100ms
   h1 ping h2
Result:
   RTT ≈ 100+ ms

### Scenario 3: Delay Removed
Command:
   sudo tc qdisc del dev s1-eth1 root netem
   h1 ping h2
Result:
   RTT returns to ≈ 1–2 ms

## Observations
- RTT increases significantly when delay is introduced.
- SDN allows dynamic control of network behavior.
- Flow rules continue to function while performance changes.

## Conclusion
This project successfully demonstrates latency measurement and analysis using SDN. It highlights the flexibility of SDN in controlling and observing network performance.

## Screenshots
(Attach all screenshots here)
