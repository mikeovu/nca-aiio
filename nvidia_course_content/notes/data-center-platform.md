# Unit 7: Data Center Platform

**Exam mapping:** Topic 1, *Essential AI Knowledge*, and Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 1 of Unit 7)

## What Unit 7 as a whole should teach you
1. The key components and features of the **NVIDIA data center platform**.
2. **GPU and CPU requirements** for AI data centers, the products, and their use cases.
3. The purpose and capabilities of **multi-GPU systems**.
4. **Multi-node GPU interconnect** technology.
5. The role of **DPUs and DOCA**.
6. The benefits of **NVIDIA-Certified Systems**.

---

## 1. Accelerated Computing Is a Full-Stack, Data-Center-Scale Problem
- **Full-stack:** you have to optimize and integrate **every layer** (hardware, system software, libraries, frameworks) to get top performance.
- **Data-center scale:** **"The data center is the new unit of computing."** Applications span the whole data center, so every component must be optimized.

### The NVIDIA platform stack (bottom to top)

| Layer | Contents |
|---|---|
| **Hardware** | **GPUs, CPUs, DPUs**, which are built into servers |
| **Programming models** | **CUDA** for GPUs, **DOCA** for DPUs |
| **Acceleration libraries** | E.g. **CUDA-X**, which gives developers acceleration transparently across hardware |
| **Application frameworks** | Built for specific domains: **Riva** (conversational AI), **DRIVE** (autonomous vehicles), **Merlin** (recommenders) and more |

---

## 2. The Three Pillars: CPU + GPU + DPU

| Pillar | Job |
|---|---|
| **GPU** | **Accelerated computing**: parallel processing at huge scale for graphics and AI |
| **CPU** | **General application processing**, especially **single-threaded** work it does well |
| **DPU** | **Data-intensive infrastructure work**: **communications processing, compression, encryption**. It keeps the data center efficient |

- Together, **GPU + CPU + DPU** make up the **new unit of computing**.
- Just as every smartphone has graphics and AI processors, **every server and workstation will have accelerators**. Many will also have **DPUs** to speed up the **network, storage and security** services at the heart of cloud-native computing.

---

## 3. Ways to Get AI Compute

| Option | What it offers |
|---|---|
| **Cloud service providers (CSPs)** | Infrastructure **without managing or maintaining it**. High-density compute and virtual workstations **anytime, anywhere, with no physical data center**. Covered in a later unit |
| **OEM systems** | Systems from **established, certified vendors** built from standard components, giving **flexibility** |
| **NVIDIA DGX** | **Purpose-built** with optimized compute, networking and storage, plus **access to NVIDIA's expertise** for deployment and maintenance |

## 4. From Idea to Production
- An AI application goes from **ideation to a trained model in production** through several phases.
- The team includes **data scientists, data engineers, business analysts, DevOps and application developers**.

## 5. Where Accelerated Computing Runs
- **Cloud:** virtual desktops, apps, workstations and **optimized containers**, so data scientists can run GPU-accelerated AI from their desks.
- **Data center:** breakthrough performance at any scale **with fewer servers**, giving **faster insights and much lower cost**. **Sensitive data stays secure.**
- **Edge:** needs a scalable, accelerated platform for **real-time decisions at the point of action**: stores, factories, hospitals, smart cities. **NVIDIA Jetson** is the **edge platform**.

---

## Key Terms
- **Full-stack acceleration**: optimizing hardware, software and frameworks together.
- **Data center as the unit of computing**: applications span the whole data center.
- **CUDA / DOCA**: programming models for GPUs / DPUs.
- **CUDA-X**: NVIDIA's GPU acceleration libraries.
- **Riva / DRIVE / Merlin**: domain frameworks for conversational AI / autonomous vehicles / recommenders.
- **Jetson**: NVIDIA's platform for edge AI.

## Exam Tips
- **The three pillars are CPU (general, single-thread), GPU (parallel acceleration) and DPU (infrastructure: networking, security, storage).**
- **CUDA is for GPUs. DOCA is for DPUs.**
- **The data center is the new unit of computing**, which is why acceleration is full-stack.
- **The three ways to consume AI compute are cloud, OEM and DGX.**
- **Jetson is for the edge.**
