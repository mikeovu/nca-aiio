# Unit 8: InfiniBand and Ethernet

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 2 of Unit 8)

---

## 1. InfiniBand
- A networking technology built for **high throughput and low latency** with **minimal processing overhead**.
- The spec is maintained by the **InfiniBand Trade Association (IBTA)**. It covers everything **from the hardware layer to the application layer**.
- It connects **compute and storage** at high speed and includes **intelligent offload features**.
- **A favorite of traditional HPC** (scientific simulations on parallel clusters), also used in cloud data centers and GPU AI.
- **The most deployed high-speed interconnect for large-scale ML**, for both training and inference.

### RDMA: InfiniBand's key feature

| Term | Meaning |
|---|---|
| **DMA** (direct memory access) | A device, such as a GPU or network adapter, reads and writes **host memory directly without the CPU** |
| **RDMA** (remote DMA) | Accesses **memory on a remote system** without interrupting **that system's CPU** |
| **HCA** (host channel adapter) | An InfiniBand network adapter. It has **hardware offload** and **bypasses the TCP/IP stack** completely, for faster data movement with less CPU overhead |

**RDMA benefits:**
- **Efficient data transfer**: **OS bypass** gives the fastest possible access to remote data.
- **Efficient computing**: **lowers power, cooling and space** needs.
- Supports **message passing, sockets and storage protocols**.
- Supported by **all major operating systems**.

---

## 2. Ethernet
- **Introduced in 1979** and standardized as **IEEE** standards in the 1980s. It defines how devices **format and send data on a LAN**.
- **The dominant LAN technology**, because it keeps **getting faster while staying backward compatible**: **10 Mb/s → 100 Mb/s (mid-1990s) → up to 400 Gb/s** today.
- **Ethernet is general-purpose**, covering home, corporate LAN and data center. **InfiniBand has one goal: the highest-performance data center interconnect.**

### RoCE (RDMA over Converged Ethernet)
- Brings **RDMA to Ethernet networks**.
- It takes the **InfiniBand packet header** and **wraps it in a UDP header** carried over Ethernet.
  - **UDP** is simple, flexible and **compatible with legacy hardware**.
  - UDP encapsulation lets RoCE **cross Layer 3 (routed) networks**.
- RoCE is **open source** and a **formal IBTA standard**. It's increasingly important for **AI, storage and big data**, although **InfiniBand's native RDMA is still leaner**.

---

## 3. GPUDirect RDMA
- A **direct, peer-to-peer data path** between **GPU memory** and **NVIDIA network adapters**, so GPUs in **different servers** can talk directly.
- **Minimizes CPU use** and avoids **buffer copies through system memory**.
- NVIDIA adapters **combine data and send smart interrupts**, using **close to 0% of CPU cycles**.

### Packet flow

| Step | **Without GPUDirect RDMA** | **With GPUDirect RDMA** |
|---|---|---|
| 1 | The HCA receives packets from the remote node | The HCA receives packets |
| 2 | Packets cross **PCIe** and are **copied to system memory** | Packets go **straight to GPU memory** |
| 3 | The **CPU handles them** | — |
| 4 | **Copied again over PCIe to GPU memory** | — |

**What it saves:** **whole copy operations**, **PCIe transactions** and **CPU usage**, and it **lowers end-to-end latency**.

---

## Key Terms
- **InfiniBand (IB)**: a low-latency, high-throughput interconnect standardized by the IBTA.
- **HCA**: host channel adapter, the InfiniBand NIC.
- **DMA / RDMA**: direct memory access, local / remote, without the CPU.
- **OS bypass**: data moves without going through the kernel's TCP/IP stack.
- **RoCE**: RDMA over Converged Ethernet, an IB header wrapped in UDP over Ethernet.
- **GPUDirect RDMA**: the NIC reads and writes GPU memory directly, skipping system memory and the CPU.

## Exam Tips
- **InfiniBand is the most deployed interconnect for large-scale ML.** Its spec comes from the **IBTA**.
- **RDMA lets one system access another's memory without involving its CPU.** HCAs **bypass TCP/IP**.
- **RoCE = an InfiniBand header in UDP over Ethernet.** It can be **routed across Layer 3**.
- **GPUDirect RDMA skips the copy into system memory and the CPU**, giving lower latency and less CPU and PCIe load.
- **Ethernet is general-purpose and backward compatible (up to 400 Gb/s). InfiniBand is purpose-built for top performance.**
