# Unit 7: Multi-GPU Systems

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 3 of Unit 7)

---

## 1. Scale Up vs. Scale Out

| | **Scale up = multi-GPU** | **Scale out = multi-node** |
|---|---|---|
| What you add | **More GPUs in one node** | **More nodes** in the system |
| Hardware | One node with many GPUs + a **high-speed GPU interconnect** | Many nodes, each with its own processing, **connected by a network** |
| Data distribution | Across GPUs | Across nodes |
| Load balancing | Between GPUs | Between nodes |
| Fault tolerance | **Lower**: one failed GPU can affect the whole system | **Higher**: one failed node doesn't take down the system |

---

## 2. How GPUs Talk Inside a Server

| Technology | What it does | Limitation |
|---|---|---|
| **PCIe** | The traditional server interconnect | **Becomes a bottleneck** as workloads grow and GPUs get faster |
| **NVLink** | Connects GPUs **much faster than PCIe** so they can **share memory** at high speed | In **all-to-all** communication, some GPU pairs **still fall back to slower PCIe** |
| **NVSwitch** | **Any GPU can talk directly to any other GPU with no bottleneck.** Every GPU connects over NVLink to all the NVSwitch fabrics | It's the answer for **scaling beyond 8 GPUs** and for **all-to-all** traffic |

- **All-to-all operations** happen when every GPU needs to talk to every other GPU at once, e.g. distributing data. They're **common in AI and HPC**.

---

## 3. DGX H100 Spec Sheet

| Component | Spec |
|---|---|
| GPUs | **8× H100** |
| GPU interconnect | **NVSwitch**: **4× fourth-generation NVLink switches** |
| Networking | **10× ConnectX-7** network interfaces at **400 Gb/s** each, **up to 1 TB/s peak bidirectional** |
| CPUs | **2× Intel Xeon Platinum 8480C** = **112 cores** |
| System memory | **2 TB** |
| Storage | **30 TB NVMe SSD**, using **8× U.2 NVMe drives as a data cache** |
| AI performance | **32 petaFLOPS** (32 quadrillion FLOPS) |
| OS | **DGX OS**, a customized **Ubuntu Linux** with system-specific optimizations, drivers, and diagnostic and monitoring tools. **Pre-installed, tested and supported. Turnkey** |
| Size | **8 rack units (8U)**, fits a standard **19-inch rack**. Heavy enough to **need a mechanical lift** |

### Physical layout
- **Front:**
  - the gold bezel
  - **12 dual-fan modules**
  - **8 U.2 NVMe drives**
  - a **front console board** (VGA and USB for a **crash cart**)
  - the **power distribution board**
  - a **midplane** linking the motherboard tray, the GPU tray and the front components
- **Rear:** the **GPU tray on top**, the **motherboard tray below**, and the **power supplies**.
- It's a **modular** design.

---

## 4. The Wider DGX and Blackwell Portfolio
- **DGX systems** are **multi-GPU AI supercomputers**: top GPUs, ultra-fast interconnects and an integrated software stack. The family runs from **H100 and H200** to **Blackwell**, across **cloud and on-prem**.
- **GB300 NVL72:**
  - a **fully liquid-cooled, rack-scale** system
  - **36 Arm-based Grace CPUs + 72 Blackwell Ultra GPUs**, linked by **fifth-generation NVLink** into one platform
  - **purpose-built for test-time scaling inference and AI reasoning**
  - also runs **diffusion-based real-time video generation** from world foundation models such as **NVIDIA Cosmos**, for physical AI
- **RTX PRO 6000 Blackwell Server Edition:**
  - **96 GB of GDDR7**
  - handles **agentic AI, physical AI, scientific computing, rendering, 3D graphics and video**
  - **RTX PRO servers** built on it bring Blackwell performance and efficiency to **AI factories and every enterprise workload**

---

## Key Terms
- **Scale up / scale out**: more GPUs per node / more nodes.
- **NVLink**: NVIDIA's high-speed GPU-to-GPU link, much faster than PCIe.
- **NVSwitch**: a switch fabric giving full-bandwidth **any-to-any** GPU communication.
- **All-to-all**: every GPU exchanging data with every other GPU at the same time.
- **ConnectX-7**: the 400 Gb/s network adapter in DGX H100.
- **DGX OS**: NVIDIA's optimized, supported Ubuntu for DGX.
- **NVL72**: a rack-scale system with 72 GPUs linked by NVLink.

## Exam Tips
- **Scale up means multi-GPU. Scale out means multi-node. Multi-node has better fault tolerance.**
- **PCIe bottlenecks. NVLink is faster. NVSwitch removes all-to-all bottlenecks and scales past 8 GPUs.**
- Memorize the **DGX H100** specs: **8× H100, 4 NVSwitches, 10× ConnectX-7 at 400 Gb/s, 2× Xeon (112 cores), 2 TB RAM, 30 TB NVMe, 32 PFLOPS, 8U, DGX OS (Ubuntu)**.
- **GB300 NVL72 = 36 Grace + 72 Blackwell Ultra, liquid-cooled**, built for **reasoning and test-time scaling**.
