# Unit 7: Introduction to DPUs (and NVIDIA-Certified Systems)

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 4 of Unit 7)

---

## 1. What a DPU Is
- The **third pillar** of the data center, alongside the CPU and GPU.
- A **data center infrastructure on a chip**. It enables **software-defined, hardware-accelerated** IT infrastructure.
- **Why it's needed:** running infrastructure services on the host CPU **steals CPU cores** and **hurts application performance**, sometimes severely.

### The DPU mission: offload, accelerate, isolate

| Verb | Meaning |
|---|---|
| **Offload** | Takes infrastructure tasks **off the server CPU**, freeing it for **applications** (the "money-making" work) |
| **Accelerate** | Runs those functions **faster than the CPU** using **dedicated hardware accelerators**, which speeds up network traffic and apps |
| **Isolate** | Moves critical **data plane and control plane** functions into a **separate domain on the DPU**, protecting them **even if the host CPU or its software is compromised** |

- A DPU has **specialized accelerators for networking, security and storage**. They're **more efficient and use less power** than CPU cores.
- It also suits compute-heavy jobs where **space is tight**, such as the **far edge**.

---

## 2. NVIDIA BlueField-3
- The **third-generation** NVIDIA DPU and infrastructure compute platform, **from cloud to core to edge**.
- Connectivity: **400 Gb/s Ethernet** or **NDR 400 Gb/s InfiniBand**.
- It offloads, accelerates and isolates **software-defined networking, storage, security and management**.

### BlueField use cases

| Area | How BlueField helps |
|---|---|
| **Cloud / CSPs** | The **largest CSPs** use it for efficiency and scale. Runs in **bare-metal and virtualized clouds**, and **Kubernetes clusters** (often on bare metal). **Secures bare-metal clouds** |
| **Cybersecurity** | **Next-generation firewalls (NGFW)**, **micro-segmentation**. Enables **zero trust everywhere**, pushing security **to the edge of every server**, not just the perimeter |
| **Storage** | **NVMe over Fabrics (NVMe-oF)**, **GPUDirect Storage**, data integrity, decompression, deduplication. **Remote storage performance rivals direct-attached storage** |
| **HPC/AI, telco, enterprise storage, CDN** | Faster performance and new functions |
| **Video streaming** | **Offloads streaming** from the CPU, saving CPU cycles |

## 3. NVIDIA DOCA
- **The open cloud SDK and acceleration framework for BlueField DPUs.** It does for DPUs what **CUDA** does for GPUs.
- It uses **industry-standard APIs** to **quickly build** networking, storage and infrastructure services on BlueField. It supports **BlueField-3**.

---

## 4. NVIDIA-Certified Systems
- **What they are:** **NVIDIA GPUs + NVIDIA networking** in servers from **leading vendors**. They follow **NVIDIA design best practices** and **pass certification tests** for **performance, manageability, scalability and security**.
- **Why:** enterprises can **confidently pick optimized hardware** with **enterprise-grade support**, from small setups to **at-scale** deployments.
- **Security at every layer**: **platform, network and application**. Applies in the data center, at the edge, and on laptops and desktops.

### Validated capabilities

| Capability | Benefit |
|---|---|
| **GPU acceleration** | Record-setting ML, DL and analytics, plus fast video processing and rendering |
| **High-speed interconnects** | Move data **directly to GPUs** quickly |
| **Encryption offload for TLS and IPsec** | **Secures data in motion** without losing throughput |
| **Key management + secure boot** | **Host-level security** |
| **Accelerated GPU↔server data transfer** | Efficient **multi-node** processing for the biggest jobs, such as **large model training** |
| **Multi-Instance GPU (MIG)** | **Splits one GPU** into independent instances for flexible use **within a host** |

---

## Key Terms
- **DPU**: data processing unit, an infrastructure-on-a-chip that offloads, accelerates and isolates.
- **Data plane / control plane**: packet handling / management logic. Both can run isolated on the DPU.
- **BlueField-3**: NVIDIA's third-generation DPU, with 400 Gb/s Ethernet or NDR InfiniBand.
- **DOCA**: the SDK for programming BlueField DPUs.
- **NVMe-oF**: NVMe over Fabrics, network access to NVMe storage.
- **GPUDirect Storage**: a direct path between storage and GPU memory.
- **Zero trust**: security enforced at every server, not just the perimeter.
- **NVIDIA-Certified System**: a partner server validated with NVIDIA GPUs and networking.

## Exam Tips
- **The DPU mission is offload, accelerate, isolate.** Know what each word means.
- **DPUs free CPU cores** for applications and **protect infrastructure if the host is compromised**.
- **DOCA is for DPUs as CUDA is for GPUs.**
- **BlueField-3 runs at 400 Gb/s (Ethernet or NDR InfiniBand).** Use cases: CSP and bare-metal clouds, **zero trust / NGFW / micro-segmentation**, **NVMe-oF and GPUDirect Storage**, video streaming.
- **Certified systems = NVIDIA GPUs and networking on partner servers, tested for performance, manageability, scalability and security.**
- **Certified security features:** TLS and IPsec offload, secure boot, key management.
