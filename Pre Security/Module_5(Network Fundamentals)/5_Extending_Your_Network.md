# Room: Extending Your Network

**Path:** Networking

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand how networks move beyond local communication: how services become publicly accessible via **port forwarding**, how traffic is controlled and secured with **firewalls**, how **VPNs** create secure encrypted tunnels, and how devices like **routers**, **switches**, and **VLANs** enable scalable, secure communication. This is a foundational room for understanding real-world network infrastructure, not just theory.

---

## Key Concepts

* **Port Forwarding:** Exposes an internal service to the public Internet by forwarding traffic from a public IP/port to an internal IP/port.
* **Firewall:** Border security for a network — inspects traffic and decides whether it's allowed or blocked.
* **VPN (Virtual Private Network):** Creates a secure, encrypted tunnel over the Internet between devices on separate networks.
* **Router:** A Layer 3 device that connects different networks and routes packets between them.
* **Switch:** A device that connects multiple devices within a network, forwarding frames (Layer 2) or also routing packets (Layer 3, for Layer 3 switches).
* **VLAN (Virtual LAN):** A logical separation of devices within the same physical network infrastructure.

---

# Task 1: Introduction to Port Forwarding

## What Is Port Forwarding?

Port forwarding is a mechanism that allows services running inside a private network to be accessed from the public Internet.

Without port forwarding, services (e.g. web servers) are accessible only within the same local network — this internal-only network is often called an **intranet**.

## Example Scenario

A web server runs on IP `192.168.1.10`, port `80`. Only devices inside `192.168.1.0/24` can access it.

To make this web server publicly accessible, port forwarding is configured on the router: external traffic hitting the public IP (e.g. `82.62.51.70:80`) is forwarded to `192.168.1.10:80`.

## Key Distinction: Port Forwarding vs Firewalls

| Concept | Purpose |
|---|---|
| Port Forwarding | Opens a path to a service |
| Firewall | Decides whether traffic is allowed through that path |

**Important:** Port forwarding does not equal security. It only exposes a service.

## Configuration Location

Port forwarding is always configured on the **router**, as it sits at the boundary between the private network and the public Internet.

## Answer

**Q) What is the name of the device that is used to configure port forwarding?**
A) Router

---

# Task 2: Firewalls 101

## What Is a Firewall?

A firewall acts as border security for a network. It inspects traffic and decides whether it should be **allowed** or **blocked**.

## What Can Firewalls Inspect?

Firewalls analyze packets based on:

* Source network
* Destination network
* Port number
* Protocol (TCP / UDP)

This process is called **packet inspection**.

## Firewall Categories

### Stateful Firewall

* Tracks the entire connection
* Makes decisions based on session behavior
* More intelligent but resource-heavy

**Example:** Allows the initial TCP handshake, but can then block later malicious behavior — up to blocking the entire host.

### Stateless Firewall

* Evaluates each packet independently
* Uses static rule sets
* Faster and lightweight, but less intelligent

**Example:** Excellent against DDoS, since it has no context of previous packets.

| Category | Inspects |
|---|---|
| Stateful | Entire connection |
| Stateless | Individual packets |

## OSI Layer Operation

Firewalls primarily operate at **Layer 3 (Network)** and **Layer 4 (Transport)**.

## Answers

**Q) What layers of the OSI model do firewalls operate at?**
A) 3 & 4

**Q) What category of firewall inspects the entire connection?**
A) Stateful

**Q) What category of firewall inspects individual packets?**
A) Stateless

---

# Task 3: Practical — Firewall Configuration

## Objective

* Block malicious traffic (red packets)
* Allow legitimate traffic (green packets)
* Target: web server `203.0.110.1`
* Protocol to block: port 80

This task reinforces rule-based packet filtering and a visual understanding of firewall behavior.

## Flag

`THM{FIREWALLS_RULE}`

---

# Task 4: VPN Basics

## What Is a VPN?

A **Virtual Private Network (VPN)** creates a secure, encrypted tunnel over the Internet that allows devices on separate networks to communicate as if they were on the same private network.

## Core Benefits

| Benefit | Explanation |
|---|---|
| Secure Connectivity | Safely connects distant networks |
| Privacy | Encrypts data in transit |
| Anonymity | Obscures traffic from ISPs/intermediaries |

## TryHackMe VPN Use Case

TryHackMe uses VPNs to:

* Securely connect learners to vulnerable machines
* Prevent public exposure of lab systems
* Avoid ISP or legal issues

## VPN Technologies

| Technology | Purpose |
|---|---|
| PPP | Authentication & encryption |
| PPTP | Tunneling mechanism (weak encryption) |
| IPSec | Strong encryption using the IP framework |

## Answers

**Q) What VPN technology only encrypts & provides authentication of data?**
A) PPP

**Q) What VPN technology uses the IP framework?**
A) IPSec

---

# Task 5: LAN Networking Devices

## What Is a Router?

* Connects different networks
* Performs routing
* Operates at Layer 3
* Chooses optimal paths based on distance, reliability, and speed

## What Is a Switch?

Switches connect multiple devices within a network.

### Layer 2 Switch

* Uses MAC addresses
* Forwards frames
* No routing capability

### Layer 3 Switch

Combines frame forwarding (Layer 2) with packet routing (Layer 3).

## VLANs (Virtual LANs)

VLANs allow logical separation within the same physical network — devices share the same infrastructure, but communication rules are enforced between segments, improving security and segmentation.

## Answers

**Q) What is the verb for the action that a router does?**
A) Routing

**Q) What are the two different layers of switches?**
A) Layer 2, Layer 3

---

# Task 6: Practical — Network Simulator

## Objective

* Simulate packet traversal across a network
* Send a TCP packet from `computer1` to `computer3`
* Observe handshake, routing, and delivery steps

This task reinforces packet flow visualization, TCP handshake behavior, and routing logic.

## Answers

**Q) What is the flag from the network simulator?**
A) `THM{YOU'VE_GOT_DATA}`

**Q) How many HANDSHAKE entries are there in the Network Log?**
A) 5

---

# Task 7: Conclusion

## Key Takeaways

* Port forwarding **exposes** services — it does not **secure** them.
* Firewalls decide **what is allowed**, not what exists.
* VPNs provide **encrypted tunnels** over untrusted networks.
* Routers move **packets between networks**.
* Switches move **frames within networks**.
* VLANs enforce **segmentation** without extra hardware.

## Mindset Shift

Networking is not about cables and IPs — it's about **control**: who can talk, who cannot, over which protocol, and through which path. Understanding this is what separates users from security professionals.

---

# Key Terminology

* **Port Forwarding:** Forwards external traffic on a public IP/port to an internal IP/port, exposing a private service to the Internet.
* **Intranet:** A network accessible only internally, not from the public Internet.
* **Firewall:** A device/system that inspects traffic and allows or blocks it based on rules.
* **Packet Inspection:** Analyzing packets by source, destination, port, and protocol to make a filtering decision.
* **Stateful Firewall:** Tracks the entire connection/session before making a decision.
* **Stateless Firewall:** Evaluates each packet independently against static rules.
* **VPN (Virtual Private Network):** An encrypted tunnel over the Internet connecting separate networks/devices securely.
* **PPP:** VPN technology providing authentication and encryption only.
* **PPTP:** A tunneling mechanism with weak encryption.
* **IPSec:** A VPN technology providing strong encryption using the IP framework.
* **Router:** A Layer 3 device that connects and routes between different networks.
* **Switch:** A device connecting multiple devices within one network (Layer 2: frames/MAC addresses; Layer 3: adds routing).
* **VLAN (Virtual LAN):** Logical segmentation of devices sharing the same physical network infrastructure.

---

# Key Takeaways

* **Port forwarding** and **firewalls** solve different problems — forwarding opens a path to a service, while a firewall decides what's allowed through that path. Exposing a service isn't the same as securing it.
* **Firewalls** operate at Layers 3 and 4, and can be **stateful** (tracks whole connections, smarter but heavier) or **stateless** (per-packet, faster but less context-aware, great against DDoS).
* **VPNs** extend private-network-like communication over the public Internet through an encrypted tunnel, providing secure connectivity, privacy, and anonymity — TryHackMe itself uses this to safely connect learners to lab machines.
* VPN technologies vary in strength: **PPP** handles authentication/encryption, **PPTP** tunnels but with weak encryption, and **IPSec** provides strong encryption using the IP framework.
* **Routers** operate at Layer 3 and move packets *between* different networks; **switches** operate primarily at Layer 2 and move frames *within* a network (Layer 3 switches can also route).
* **VLANs** let a single physical network be logically segmented for better security and organization, without needing separate physical hardware per segment.
* Ultimately, networking infrastructure is about **control** — deciding who can communicate, over which protocol, and through which path.

---

## What I Learned

This room shifted my understanding of networking from "how data physically moves" to "how access and control are actually enforced" — which feels like a much more security-relevant way of thinking about infrastructure. The clearest takeaway was the distinction between **port forwarding** and **firewalls**: forwarding just opens a door from the public Internet to an internal service, while a firewall is what actually decides whether anyone should be allowed to walk through that door. That distinction is easy to overlook but crucial — a forwarded port with no firewall rules is just an open door.

The firewall task clarified the practical trade-off between **stateful** and **stateless** filtering: stateful firewalls understand the whole conversation and can react to bad behavior mid-connection, while stateless firewalls just check each packet in isolation against fixed rules, which makes them fast and effective against high-volume attacks like DDoS but blind to context. Completing the firewall practical — blocking malicious traffic to `203.0.110.1` on port 80 while letting legitimate traffic through — made rule-based filtering feel concrete rather than abstract, and earned the flag `THM{FIREWALLS_RULE}`.

Learning about **VPNs** connected directly back to something I already use as a student on TryHackMe: I now understand *why* it requires a VPN connection before accessing lab machines — to keep those vulnerable systems off the public Internet and avoid ISP/legal issues, while still letting learners reach them securely. Comparing PPP, PPTP, and IPSec also gave me a sense of how VPN technologies differ in strength, particularly that PPTP's weak encryption makes it a poor modern choice compared to IPSec.

Finally, distinguishing **routers** (move packets *between* networks, Layer 3) from **switches** (move frames *within* a network, primarily Layer 2, sometimes Layer 3) — and learning how **VLANs** let you logically segment one physical network — tied back nicely to earlier rooms on the OSI model. The network simulator practical, sending a TCP packet from `computer1` to `computer3` and counting 5 handshake entries in the log, reinforced how the Three-Way Handshake and routing actually play out step-by-step across real infrastructure, not just as a diagram. The room's closing point — that networking is fundamentally about *control*, not just cables and IPs — is a good mental model to carry forward into more advanced security topics.