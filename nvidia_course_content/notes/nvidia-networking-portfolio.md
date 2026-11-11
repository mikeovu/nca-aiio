# Unit 8: NVIDIA Networking Portfolio

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 3 of Unit 8)

---

## 1. The Network Is the Foundation
- **"The data center is the new unit of compute"**, and the **network** is what makes it work as one system.
- **Agentic AI and reasoning models** are **data- and latency-sensitive**, not just compute-heavy. They span **thousands of GPUs across racks and rows**.
- NVIDIA offers **end-to-end InfiniBand and Ethernet** solutions.

### Where each technology fits

| Technology | Role | Direction |
|---|---|---|
| **NVLink** | **Scale up**: GPUs in a server, or in tightly coupled servers, behave like **one large memory and compute pool**. Essential for **model parallelism** | Inside the node or rack |
| **InfiniBand (Quantum)** and **Spectrum-X Ethernet** | **Scale out**: the high-speed **east-west compute fabric** between nodes, for multi-node training and inference | **East-west** |
| **BlueField DPU** | **Secures and accelerates north-south traffic**: user access, control planes, storage fabrics. Offloads networking, security and storage from the CPU | **North-south** |

---

## 2. Spectrum-X: Ethernet Built for AI
- **The first Ethernet platform designed specifically for AI clouds.** It delivers **near-perfect bandwidth and very low latency**.
- **The secret is NVIDIA's RoCE extensions**, which go beyond standard RoCE:

| Extension | What it does |
|---|---|
| **RoCE Adaptive Routing** | **Fine-grained, dynamic load balancing.** It **reroutes RDMA traffic** around congestion, choosing paths from live **switch state (queue occupancy, port utilization)** |
| **RoCE Congestion Control** | **Limits the injection rate** of flows at congested ports. This means **fewer packet drops** on lossy networks, **less congestion spreading** on lossless ones, **less buffer use, lower latency and better burst tolerance**. It also provides **performance isolation** |

- **These extensions need the Spectrum-4 switch AND the BlueField-3 DPU working together.** They're unique to NVIDIA.
- It's **tuned and validated across the full NVIDIA stack**, but it's still **standards-based Ethernet**, **interoperable with any Ethernet device**.

---

## 3. Quantum-X800: InfiniBand for Trillion-Parameter AI
- The **next generation of Quantum InfiniBand**. It's the **highest-performance end-to-end 800 Gb/s networking**.
- **Components:**
  - the **Quantum-X800 InfiniBand switch**
  - the **ConnectX-8 SuperNIC**
  - **LinkX** cables and transceivers

| Component | Key specs |
|---|---|
| **Quantum-X800 switch** | **144 ports × 800 Gb/s.** **SHARPv4** in-network computing, adaptive routing, **telemetry-based congestion control**, performance isolation, and a dedicated port for **UFM (Unified Fabric Manager)** |
| **ConnectX-8 SuperNIC** | **Up to 800 Gb/s** over **InfiniBand and Ethernet**. **PCIe Gen6, up to 48 lanes**, which allows **PCIe switching** inside GPU systems |

---

## 4. Co-Packaged Optics (Silicon Photonics)
- **Replaces pluggable transceivers** with **silicon photonics in the same package as the switch ASIC**.
- Compared with traditional networks:
  - **3.5× better power efficiency**
  - **10× higher network resiliency**
  - **1.3× faster time to deploy**

| Switch | Specs |
|---|---|
| **Quantum-X Photonics (Quantum 3450-LD)** | **115 Tb/s** InfiniBand, **144 × 800 Gb/s** ports, **liquid-cooled**. Connects **over 10,000 GPUs** in a **non-blocking two-level fat-tree** at 800 Gb/s |
| **Spectrum-X Photonics SN6810** | **128 × 800 Gb/s** Ethernet |
| **Spectrum-X Photonics SN6800** | **512 × 800 Gb/s** Ethernet |

---

## Key Terms
- **Scale up vs. scale out**: NVLink inside a node or rack vs. InfiniBand or Ethernet between nodes.
- **East-west / north-south**: server-to-server traffic / traffic in and out of the data center.
- **Spectrum-X**: NVIDIA's AI Ethernet platform (Spectrum-4 switch + BlueField-3).
- **RoCE Adaptive Routing / Congestion Control**: NVIDIA's dynamic load balancing / injection-rate limiting.
- **Quantum-X800**: NVIDIA's 800 Gb/s InfiniBand platform.
- **SHARP**: in-network computing that runs collective operations inside the switch.
- **UFM**: Unified Fabric Manager, which manages InfiniBand fabrics.
- **SuperNIC**: ConnectX-8, an 800 Gb/s NIC for IB or Ethernet.
- **Co-packaged optics**: optics built into the switch package instead of pluggable modules.
- **Fat-tree**: a non-blocking multi-level switch topology.

## Exam Tips
- **NVLink scales up. InfiniBand and Spectrum-X scale out (east-west). BlueField handles north-south.**
- **Spectrum-X needs Spectrum-4 + BlueField-3** for **RoCE Adaptive Routing and Congestion Control**, and it's still standard, interoperable Ethernet.
- **Adaptive routing balances load dynamically using switch queue and port state. Congestion control limits injection rate at hot ports.**
- **Quantum-X800 = 144 × 800 Gb/s + SHARPv4 + UFM.** The **ConnectX-8 SuperNIC** does 800 Gb/s on IB *or* Ethernet over **PCIe Gen6**.
- **Co-packaged optics give 3.5× power efficiency, 10× resiliency and 1.3× faster deployment.**
