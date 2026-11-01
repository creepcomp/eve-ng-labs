# EVE-NG Network Labs

A practical collection of network-engineering labs built for **EVE-NG**. This repository brings together hands-on scenarios for learning, practicing, and validating network concepts—from foundational IP addressing and VLANs to resilient campus and data-center architectures.

The labs are intended for network-engineering students, administrators, and anyone who wants a safe virtual environment in which to build and troubleshoot network designs.

## Contents

- [About the project](#about-the-project)
- [Lab collection](#lab-collection)
  - [Network fundamentals and architectures](#network-fundamentals-and-architectures)
  - [Switching and network discovery](#switching-and-network-discovery)
  - [Link aggregation and VLAN management](#link-aggregation-and-vlan-management)
- [Getting started](#getting-started)
- [Working with the labs](#working-with-the-labs)
- [Repository structure](#repository-structure)
- [Contributing](#contributing)
- [Issues and feedback](#issues-and-feedback)
- [License](#license)

## About the project

EVE-NG (Emulated Virtual Environment – Next Generation) makes it possible to build virtual network topologies and practice with supported network-device images. This repository is a growing collection of lab scenarios covering topics such as:

- IPv4 and IPv6 addressing
- Layer 2 switching, VLANs, and inter-VLAN routing
- Two-tier, three-tier, and spine-leaf network designs
- Small-office/home-office (SOHO) networking
- Cisco Discovery Protocol (CDP) and Link Layer Discovery Protocol (LLDP)
- Layer 2 and Layer 3 EtherChannel
- VLAN Trunking Protocol (VTP)

The repository currently contains topology downloads and lab descriptions for the scenarios listed below. The level of supporting material differs between labs; configuration files and completed solutions are not consistently included.

## Lab collection

### Network fundamentals and architectures

#### 01 · IPv4 and IPv6 Addressing

![IPv4 and IPv6 Addressing topology](https://github.com/hegdepavankumar/eve-ng-labs/assets/85627085/3a5f0015-c68b-4018-abbc-063efd3d2a97)

**Goal:** Configure IPv4 and IPv6 addresses on a Cisco router.

**Tasks:**
- Configure `GigabitEthernet0/0` with IPv4 `192.168.1.1/24` and IPv6 `2001:192:168:1::1/64`.
- Configure `GigabitEthernet0/1` with IPv4 `192.168.2.1/24` and IPv6 `2001:192:168:2::1/64`.
- Verify interface status and address configuration.

[Download topology](https://github.com/user-attachments/files/15542449/IPv4.and.IPv6.Addressing.zip)

---

#### 02 · Inter-VLAN Routing with a Multilayer Switch

![Inter-VLAN routing with multilayer switch topology](https://github.com/hegdepavankumar/eve-ng-labs/assets/85627085/715ccd5e-996a-412e-9d35-b33e380d43a6)

**Goal:** Build a Layer 2/Layer 3 switching environment and enable communication between VLANs.

**Tasks:**
- Configure a management IP address on the Layer 3 switch.
- Create VLANs (for example, VLAN 10 for Sales and VLAN 20 for HR).
- Assign access ports to the appropriate VLANs on the switches.
- Enable Layer 3 IP routing and verify inter-VLAN connectivity.

[Download topology](https://github.com/user-attachments/files/15542609/Inter.VLAN.Routing.with.Multilayer.Switch.zip)

---

#### 03 · Two-Tier Network Architecture

![Two-tier network architecture topology](https://github.com/hegdepavankumar/eve-ng-labs/assets/85627085/95056c2a-76b8-4c41-aca3-4ebce10465a9)

**Goal:** Understand a basic network design in which end devices connect to an access switch, and the switch connects to an edge router.

**Scenario and tasks:**
- Connect four PCs to one switch and connect the switch to a router.
- Use a private IPv4 subnet, such as `192.168.1.0/24`.
- Assign addresses to the PCs and configure the router's LAN interface as their default gateway.
- Configure an external or simulated upstream network if required.
- Test host-to-host and host-to-gateway connectivity; test external reachability when an upstream network is available.

**Example host addresses:** `192.168.1.2` through `192.168.1.5`.

[Download topology](https://github.com/user-attachments/files/15542759/Two-tier-architecture.zip)

---

#### 04 · Three-Tier Network Architecture

![Three-tier network architecture topology](https://github.com/user-attachments/assets/9a18cd60-da77-41cc-aa82-3098da44a614)

**Goal:** Design a scalable campus network using access, distribution, and core layers, with redundancy and high availability.

**Scenario and tasks:**
- **Access:** Connect four PCs to four access switches (`A-SW-1` to `A-SW-4`). Provide redundant uplinks from each access switch to the distribution layer.
- **Distribution:** Deploy two distribution switches and configure a two-link EtherChannel between them.
- **Core:** Deploy two interconnected core switches. Connect each core switch to both distribution switches and provide an upstream router connection.
- Define an IP addressing plan and VLAN assignments for network segments and management.
- Configure HSRP on the core switches, with one active and one standby gateway.
- Configure the required routing and verify failover and connectivity.

[Download topology](https://github.com/user-attachments/files/16409831/Three.tier.architecture.zip)

---

#### 05 · Spine-Leaf Data-Center Architecture

![Spine-leaf network architecture topology](https://github.com/user-attachments/assets/a782857e-e93d-43ba-8636-7baabf8daee6)

**Goal:** Explore a scalable data-center fabric designed for predictable paths, high throughput, and low latency.

**Scenario and tasks:**
- Build a topology with multiple spine and leaf switches.
- Connect every leaf switch to every spine switch.
- Add representative end devices and traffic flows.
- Evaluate latency, throughput, packet loss, and traffic distribution under different workloads.
- Consider how the fabric can scale by adding spine or leaf switches.
- Investigate load distribution and QoS where supported by the selected images.

**Deliverables to aim for:** A topology diagram, device configurations, test results, and a short analysis of performance and scalability.

[Download topology](https://github.com/user-attachments/files/16409944/Spine-leaf-architecture.zip)

---

#### 06 · Small Office / Home Office (SOHO)

![SOHO network topology](https://github.com/user-attachments/assets/d30fcc58-4e5b-47bf-add0-28cc47f39f5c)

**Goal:** Configure a small-office network containing a router, FortiGate firewall, switch, wireless access point, and client devices.

**Scenario and tasks:**
- Configure the router's WAN and LAN connectivity.
- Place the FortiGate firewall between the internal network and the upstream router; configure its interfaces and security policies.
- Configure the switch ports for PCs, workstations, IP phones, tablets, and the wireless access point.
- Provide wireless access to the internal network.
- Assign client addresses, using DHCP where appropriate.
- Verify local connectivity and permitted access to external resources.

**Addressing information in the original lab brief:** the router WAN is specified as `192.168.1.0/24`, the router LAN and FortiGate links are specified as `192.168.20.0/24`, and the client network is specified as `192.168.10.0/24`. Review the topology and resolve any overlapping or inconsistent interface/subnet assignments before configuring the lab.

[Download topology](https://github.com/user-attachments/files/16410066/Small-Office-Home-Office_SOHO.zip)

---

### Switching and network discovery

#### 07 · Standard VLANs

![Standard VLAN topology](https://github.com/user-attachments/assets/8a5d4252-ea76-48a0-a712-d18c5e59d9f6)

**Goal:** Configure a VLAN across two switches and verify Layer 2 connectivity between devices in that VLAN.

**Tasks:**
- Create VLAN 10 on both switches.
- Configure the inter-switch link on `G0/0` as a trunk on both ends.
- Assign the required access ports to VLAN 10.
- Connect end devices and verify communication across the trunk.

[Download topology](https://github.com/user-attachments/files/16410145/Standard-VLANs.zip)

---

#### 08 · Inter-VLAN Routing — Router-on-a-Stick

![Router-on-a-stick topology](https://github.com/user-attachments/assets/f4ab324b-c729-4a4f-851a-41a4852268d1)

**Goal:** Route traffic between VLANs using router subinterfaces over an 802.1Q trunk.

**Topology details:**
- VLAN 10 represents IT and uses `10.1.1.0/24`.
- VLAN 20 represents HR and uses `20.1.1.0/24`.
- The router (`Edge-R`) uses subinterface addresses `10.1.1.100` and `20.1.1.100` for the respective VLANs.
- PC-1 and PC-2 belong to VLAN 10; PC-3 and PC-4 belong to VLAN 20.

**Tasks:**
- Create VLANs 10 and 20 and assign access ports.
- Configure the switch-to-router link as a trunk.
- Configure and address the router's VLAN subinterfaces.
- Set the PCs' IP addresses, masks, and default gateways.
- Verify same-VLAN and inter-VLAN connectivity.

[Download topology](https://github.com/user-attachments/files/16410277/Inter-VLAN-Routing_Router.on.a.stick.zip)

---

#### 09 · Cisco Discovery Protocol (CDP)

![CDP topology](https://github.com/user-attachments/assets/c796894e-6d3c-4722-911e-aa832a2ed9a3)

**Goal:** Use CDP to discover directly connected Cisco devices and validate neighbor information.

**Tasks:**
- Check whether CDP is enabled globally and enable it where required.
- Check CDP on interfaces connected to neighboring Cisco devices.
- Inspect the CDP neighbor table on each device.
- Record device IDs, local interfaces, remote interfaces, and capabilities.
- Compare discovered neighbors with the topology diagram.
- Troubleshoot missing neighbors and consider disabling CDP on untrusted-facing interfaces.

[Download topology](https://github.com/user-attachments/files/16410368/Cisco-Discovery-Protocol_CDP.zip)

---

#### 10 · Link Layer Discovery Protocol (LLDP)

![LLDP topology](https://github.com/user-attachments/assets/d8322667-2fd1-4ae4-8ca7-681f233aaf6a)

**Goal:** Discover neighboring network devices using the vendor-neutral LLDP protocol.

**Topology details from the lab brief:**
- The switch connects to VPC4, IP Phone-1, and Router-1 (`Gi0/2`).
- Router-1 connects to the switch, IP Phone-2, and Router-2 (`Gi0/1`).
- Router-2 connects to Router-1 (`Gi0/0`).

**Tasks:**
- Enable LLDP globally on the supported routers and switches.
- Enable LLDP transmit/receive on the relevant interfaces.
- Inspect neighbor information on each device.
- Check phone LLDP support and settings where applicable.
- For VPCs that do not support LLDP, verify their attachment through the connected switch.

[Download topology](https://github.com/user-attachments/files/16410587/Link-Layer-Discovery-Protocol_LLDP.zip)

---

### Link aggregation and VLAN management

#### 11 · Layer 2 EtherChannel — PAgP, LACP, and Static Mode

![Layer 2 EtherChannel topology](https://github.com/user-attachments/assets/97125c6d-d5e6-4099-b744-18d0a6ccdc0d)

**Goal:** Practice Layer 2 link aggregation and compare the negotiation and configuration behavior of PAgP, LACP, and static EtherChannel.

**Suggested verification:** Check the port-channel state, member interfaces, and connectivity across the aggregated link.

[Download topology](https://github.com/user-attachments/files/16410787/Layer-2-Etherchannel-PagP-LACP-ON.zip)

---

#### 12 · Layer 3 EtherChannel — PAgP, LACP, and Static Mode

![Layer 3 EtherChannel topology](https://github.com/user-attachments/assets/33a3662f-29fe-4fb8-ad25-fc671cc77475)

**Goal:** Practice Layer 3 link aggregation and examine how routed port-channels operate.

**Suggested verification:** Check the port-channel and member-link state, configure the routed interface as required by the topology, and test Layer 3 reachability across the aggregated link.

[Download topology](https://github.com/user-attachments/files/16410848/Layer-3-Etherchannel-PagP-LACP-ON.zip)

---

#### 13 · VTP — Server, Client, and Transparent Modes

![VTP topology](https://github.com/user-attachments/assets/2dab9fae-c4fc-4f82-a71b-a2b8d3ae7fc3)

**Goal:** Explore VLAN Trunking Protocol modes and observe how VLAN information and configuration-revision behavior differ between them.

**Tasks:**
- Configure the VTP modes according to the topology.
- Verify VLAN propagation between the relevant switches.
- Observe the configuration revision number, with particular attention to transparent mode.
- Manually configure VLANs on the switch operating in transparent mode.

[Download topology](https://github.com/user-attachments/files/16410869/VTP-Clients-and-Servers.zip)

---

## Getting started

### Requirements

- An operational EVE-NG Community or Professional installation.
- The network-device images required by the individual lab.
- Sufficient CPU, memory, and storage for the selected virtual devices.
- A basic understanding of Ethernet, IP addressing, and network-device CLI operation.

> **Important:** EVE-NG does not provide vendor operating-system images with these topology archives. You must obtain and use device images in accordance with the relevant vendor licensing terms. Device availability and supported features depend on the image you install.

### Import a lab

1. Choose a lab from the [lab collection](#lab-collection).
2. Download its topology archive.
3. Extract the archive if it is packaged as a ZIP file.
4. Import the lab using the workflow supported by your EVE-NG installation and archive format.
5. Make sure the required device images are installed and mapped to the node templates used by the topology.
6. Open the lab, start the nodes, and complete the scenario's tasks.
7. Save your configurations and record your verification results.

Import procedures can vary depending on the archive contents and EVE-NG version. Follow any lab-specific instructions included with the download.

## Working with the labs

For a useful and repeatable learning process, work through each scenario in stages:

1. **Inspect:** Review the topology and identify device roles, links, and network boundaries.
2. **Plan:** Create an IP addressing table and identify VLANs, routing requirements, and expected traffic paths.
3. **Configure:** Apply the configuration incrementally rather than configuring every device at once.
4. **Verify:** Use appropriate commands and end-to-end tests to confirm that the lab behaves as expected.
5. **Troubleshoot:** Investigate failed tests systematically, checking interfaces, VLAN membership, trunks, routes, and protocol state.
6. **Document:** Save working configurations, command output, and any design decisions or issues you discovered.

Useful verification commands will depend on the platform and lab. On Cisco IOS-like devices, examples include `show ip interface brief`, `show ipv6 interface brief`, `show vlan brief`, `show interfaces trunk`, `show ip route`, `show etherchannel summary`, `show cdp neighbors`, and `show lldp neighbors`.

## Repository structure

The repository is organized around individual lab scenarios. Each lab should ideally contain its topology archive, a concise problem statement, and any supporting diagrams or configuration files that are available.

A suggested structure for future additions is:

```text
eve-ng-labs/
├── README.md
├── LICENSE
└── labs/
    ├── 01-ipv4-ipv6-addressing/
    ├── 02-inter-vlan-multilayer-switch/
    ├── 03-two-tier-architecture/
    └── ...
```

This is a suggested organization, not a claim that every directory currently exists in the repository.

## Contributing

Contributions that improve the labs or add useful scenarios are welcome. Before submitting a pull request:

- Give the lab a clear, descriptive name.
- Include the EVE-NG topology archive and a topology diagram where possible.
- Describe the objective, requirements, and expected results.
- Include tested configurations or verification output when available.
- Mention required device images and any platform-specific limitations.
- Do not include proprietary device images, credentials, or other material you are not authorized to distribute.

Open a pull request with a short explanation of the change.

## Issues and feedback

If you find a broken download, an unclear requirement, or a problem with a topology, please [open an issue](https://github.com/creepcomp/eve-ng-labs/issues). Include the lab name, the relevant device/image versions, what you expected to happen, and what happened instead. Avoid posting sensitive configuration data or credentials.

## License

This project is described in the source README as being licensed under the MIT License. See the [`LICENSE`](LICENSE) file in the repository for the applicable terms.

---

<p align="center">
  <strong>Built for learning, experimentation, and better network engineering.</strong>
</p>
