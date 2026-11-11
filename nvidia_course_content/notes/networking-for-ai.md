# Unit 8: Networking for AI

**Exam mapping:** Topic 2, *AI Infrastructure*, and Topic 3, *AI Operations*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 1 of Unit 8)

---

## 1. The Four Networks in an AI Data Center

| Network | Purpose |
|---|---|
| **Compute network** | **Minimizes bottlenecks and maximizes performance** for AI workloads (GPU-to-GPU traffic between jobs). Adds **redundancy** for hardware failures and keeps **costs down** |
| **Storage network** | **High-throughput access to shared storage.** Benefits from high bandwidth and advanced **fabric management** |
| **In-band management network** | Connects to the **management nodes**. It's the main network for **everything except job traffic and high-speed storage**: **SSH, DNS, job scheduling**, the **NFS home file system**, and external services (**NGC registry**, code repos, data sources) |
| **Out-of-band (OOB) management network** | **Remote management even when servers are offline** or unreachable in-band: **remote power control, remote serial console, temperature and power sensors** |

**Why keep management separate?** So management traffic **doesn't interfere** with cluster services or user jobs.

---

## 2. Why AI Needs a Special Network
- **GPU utilization must stay as high as possible.** GPUs have so many processing elements that they need **constant feeding** with data.
- **Moving data in and out of the GPU is expensive** in time.
- Models and datasets keep growing, and **many models run across multiple GPU nodes**, so data must move between GPUs.
- **Performance comes from the interplay of data management, GPU utilization and network configuration**, not hardware alone.
- Inside a server, the **CPU, memory and storage** must also keep up so the **GPU doesn't sit idle**.

### Network factors that affect performance
1. **Network topology**
2. **Bandwidth and latency**
3. **Network protocols**
4. **Data transfer techniques**
5. **Management methods**

---

## 3. Traditional vs. AI-Optimized Network

| | **Traditional / cloud ("north-south")** | **AI-optimized ("east-west", GPU-to-GPU)** |
|---|---|---|
| Carries | Storage, control traffic. A legacy network | **GPU-to-GPU** traffic and high-speed storage |
| Transport | **TCP** | **RDMA** |
| Loss | Can be lossy | **Lossless** (needed for RDMA) |
| Jitter | **Tolerates high jitter** | **Must avoid jitter** |
| Latency | Not critical | **Low latency** |
| Applications | **Many independent apps** with no dependencies | Like **HPC**: **nodes depend on each other** |
| What limits it | Individual app performance | **The slowest element sets the speed of the whole cluster**: a slow CPU, high jitter or high **tail latency** |
| Key metric | — | **How long an AI training job takes from start to finish** |

---

## 4. AI Factories vs. AI Clouds

| | **AI factory** | **AI cloud** |
|---|---|---|
| Used for | The **largest training jobs**: building and refining **huge foundation models at extreme scale** | **Hyperscale, multi-tenant** services running **many smaller jobs** |
| Tenants and jobs | **One tenant**, **one or a few jobs** at a time | **Many users**, many jobs |
| Network | **NVLink + InfiniBand with in-network computing** | Traditionally **Ethernet** |
| What's changing | — | AI clouds now **sometimes need to run large generative AI workloads**, and **traditional Ethernet is too slow** for them. That's the reason for AI-optimized Ethernet (Spectrum-X, covered later in this unit) |

---

## Key Terms
- **Compute / storage / in-band / out-of-band networks**: the four networks in an AI data center.
- **Out-of-band (OOB)**: management access that works even when the server OS is down (power, console, sensors).
- **North-south vs. east-west**: traffic in and out of the data center vs. server-to-server traffic inside it.
- **RDMA**: remote direct memory access, which needs a lossless network.
- **Jitter / tail latency**: variation in delay / the slowest responses. Both slow down an entire AI cluster.
- **AI factory vs. AI cloud**: a single tenant running giant jobs vs. many tenants running smaller jobs.

## Exam Tips
- **Know the four networks:** compute, storage, **in-band** (SSH, DNS, scheduling, NFS home, NGC) and **out-of-band** (power, serial console, sensors, works when the server is offline).
- **Traditional networks use TCP and tolerate jitter. AI networks use RDMA, are lossless and low-jitter.**
- **In an AI cluster, the slowest node or link sets the pace.** The key metric is **job completion time**.
- **AI factories run on NVLink + InfiniBand. AI clouds run on Ethernet**, which now needs to be AI-optimized.
