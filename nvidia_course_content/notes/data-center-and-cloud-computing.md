# Unit 6: Data Center and Cloud Computing

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Summarize the AI principles from earlier units.
2. Outline where AI workloads are hosted: **data centers and the cloud**.
3. List the **components of an AI data center**.
4. Describe what's needed to **manage and monitor** an AI data center.

> This unit is a **map of Section 2 (AI Infrastructure) and Section 3 (AI Operations)**. Each topic here gets its own unit later: compute (7), networking (8), storage (9), energy (10), reference architectures (11), cloud (12), management (13), orchestration (14).

---

## 1. Recap of Earlier Units
- AI has evolved through **ML → DL → generative AI**, each unlocking new capabilities. Generative AI creates stories, emails, music, images and video.
- **Accelerated computing (GPUs)** became essential as **CPU scaling hit its limits**.
- The **software stack** connects hardware and AI algorithms for performance and efficiency.

## 2. What a Data Center Is
- A **physical or cloud facility** that hosts essential business applications and data.
- **Three component groups:** **compute, storage and networking**, plus **power and cooling**.
- **Traditional data centers may fall short for AI** because AI is **data-intensive and compute-intensive**:
  - massive datasets need **high-performance, high-speed storage**
  - heavy computation runs on **multiple accelerated systems**
  - compute, storage and **management nodes** are networked into a **cluster**
  - the network must be **high-performance and low-latency** so it **isn't the bottleneck**

---

## 3. AI Data Center Infrastructure (6 aspects)

| Aspect | Key points |
|---|---|
| **Compute** | Training and inference need lots of power. **Accelerated systems** (powerful CPUs, memory, GPUs) process data spread across interconnected nodes. **GPU servers come from your OEM of choice** |
| **Networking** | AI jobs are **distributed across hundreds to thousands of nodes**. **Distributed computing** means many interconnected nodes working on one task over a **high-speed, low-latency network**. **"The network defines the data center"** and is the **backbone** of AI infrastructure |
| **Storage** | GPUs need **high, sustained data delivery** from storage. **Sequential read is the most common storage access pattern in neural network training** (per this unit; Unit 9 adds that records are read in **random order** across epochs). Consider **capacity, performance, network hardware and transfer protocols** |
| **Power, cooling and energy efficiency** | More compute means more power and heat. Poor cooling means **shorter equipment life, worse performance and more load on cooling**. **Accelerated computing is the most cost-effective path to energy efficiency** because it does more work per unit of energy. **Direct liquid cooling** improves heat transfer, needs less airflow, cools targeted spots and enables **waste-heat reuse** |
| **Reference architectures** | Documents with a **recommended, best-of-breed design** for implementing a system (compute servers, network fabrics, storage, management servers). Use them as a **foundation** for your own design |
| **Cloud** | Cloud GPU services are a **flexible, accessible alternative** to building and maintaining on-prem AI infrastructure |

---

## 4. Operating an AI Data Center

### Who faces which challenge

| Role | Challenge |
|---|---|
| **IT admins**: *infrastructure provisioning* | Diverse, often **container-based** data science workloads that differ from traditional enterprise IT. They must manage **GPU acceleration and high-speed networking** |
| **Data scientists**: *workload management* | Need **centralized compute** beyond their laptops but **lack the IT knowledge** to use it themselves. Need **scalable access** as they move from experiments to larger tests |
| **Line-of-business owners**: *resource monitoring* | Must ensure **optimal use of compute**, using accurate **usage data** to make business decisions |

### Container orchestration vs. job scheduling

| | **Container orchestration** | **Scheduling** |
|---|---|---|
| What | **Automates container operations**: provisioning, deployment, management, **scaling, load balancing** | **Assigns workloads to available compute resources** |
| Does | Handles tasks based on the environment's needs | **Launches and monitors jobs, manages the job queue**, makes sure jobs get the resources they need |
| Together | A **separate scheduler can work alongside an orchestrator** for advanced scheduling | |

---

## Key Terms
- **Data center**: a physical or cloud facility built from compute, storage and networking, plus power and cooling.
- [**Cluster**](https://www.nvidia.com/en-us/data-center/base-command-manager/): compute, storage and management nodes networked together.
- [**Distributed computing**](https://developer.nvidia.com/nccl): many interconnected nodes working together on one job.
- [**Reference architecture**](https://docs.nvidia.com/dgx-basepod/reference-architecture-infrastructure-foundation-enterprise-ai/latest/index.html): a documented, recommended best-practice design.
- **Direct liquid cooling**: cooling with liquid at the heat source. It's more efficient than air.
- [**Container orchestration**](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/index.html): automated deployment, scaling and load balancing of containers.
- [**Job scheduling**](https://www.nvidia.com/en-us/software/run-ai/): assigning jobs in a queue to available resources.

## Exam Tips
- **The 3 pillars of a data center are compute, storage and networking**, with power and cooling supporting them.
- **The network is the backbone.** It must be high-bandwidth and low-latency so it doesn't bottleneck GPUs.
- **Accelerated computing is the most cost-effective way to gain energy efficiency.**
- **Liquid cooling benefits:** better heat transfer, less airflow, targeted cooling, waste-heat reuse.
- **Match each role to its challenge:** IT admins (provisioning), data scientists (workload management), line-of-business owners (resource monitoring).
- **Orchestration manages containers. Scheduling assigns jobs to resources.** They're often used together.

---

## NVIDIA Documentation
Official NVIDIA pages for this lesson's main concepts (links checked November 10, 2026).

- [NVIDIA Base Command Manager](https://www.nvidia.com/en-us/data-center/base-command-manager/): cluster provisioning and management.
- [NVIDIA GPU Operator](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/index.html): GPUs in Kubernetes container orchestration.
- [NVIDIA Run:ai](https://www.nvidia.com/en-us/software/run-ai/): GPU workload scheduling and orchestration.
- [NVIDIA Collective Communications Library (NCCL)](https://developer.nvidia.com/nccl): multi-GPU and multi-node communication.
- [DGX BasePOD Reference Architecture](https://docs.nvidia.com/dgx-basepod/reference-architecture-infrastructure-foundation-enterprise-ai/latest/index.html): an example AI data center design.
