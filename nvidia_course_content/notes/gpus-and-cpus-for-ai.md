# Unit 7: GPUs and CPUs for AI

**Exam mapping:** Topic 1, *Essential AI Knowledge*, and Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript (part 2 of Unit 7)

---

## 1. Quick Recap
- **CPUs** run **complex instruction sets** on a few, increasingly multi-core processors. **GPUs** run **simple instruction sets** across **many cores** at the same time. They work **together**.
- **GPU architecture** covers the compute units, memory, caches, rendering pipelines and interconnects.

## 2. NVIDIA Architectures at a Glance

| Architecture | Type | Built for | Named after |
|---|---|---|---|
| **Blackwell** | GPU (latest) | **Large-scale generative AI**: training and inference for the **largest LLMs** | **David Blackwell**, a mathematician and statistician (probability, game theory, information theory). He independently developed **dynamic programming** and the **Rao–Blackwell theorem** |
| **Hopper** | GPU (prior flagship) | Large-scale **AI, HPC and data analytics**, e.g. conversational AI | **Grace Hopper**, one of the first programmers of the **Harvard Mark I**. She invented one of the first **linkers** |
| **Ada Lovelace** | GPU | **Gaming, AI-powered graphics, ray tracing**, plus data center workloads (L40S) | **Ada Lovelace**, whose notes on Babbage's **Analytical Engine** are considered the **first computer program** |
| **Grace** | **CPU** (Arm) | **HPC and data centers**. Combines **Arm CPU architecture** with NVIDIA AI and parallel-computing expertise | Grace Hopper |

- **Multi-Instance GPU (MIG)** on **Blackwell and Hopper** splits one GPU into **up to 7 fully isolated instances**, each with its **own high-bandwidth memory, cache and compute cores**.

---

## 3. GPU Products

### B200 (Blackwell)
- **208 billion transistors** plus HBM. Described as the **world's largest, most powerful accelerator**.
- **Second-generation Transformer Engine**: custom Blackwell **Tensor Cores** + **TensorRT-LLM** + **NeMo**. It speeds up training and inference for **LLMs and mixture-of-experts (MoE)** models.
- **Confidential Computing** protects data and models **without a performance penalty**.
- **Fifth-generation NVLink** scales **up to 576 GPUs**, for **trillion and multi-trillion-parameter models**.
- **Decompression engine** plus access to **Grace CPU memory** speeds up whole **database query pipelines** for data analytics.
- **RAS engine** (reliability, availability, serviceability) spots faults early to **minimize downtime**.

### H100 (Hopper)
- **80 billion transistors** and a **Transformer Engine** for LLMs.
- **Confidential Computing**: processes sensitive data in an **encrypted, isolated environment**, which matters especially in the **cloud**.
- **900 GB/s GPU-to-GPU** interconnect.
- **MIG** lets multiple users or apps share one GPU securely.
- Example use: training neural networks for **self-driving cars**.

### L40S (Ada Lovelace)
- For **generative AI and LLM inference and training, 3D graphics, rendering and video**.
- **Fourth-generation Tensor Cores**, the specialized units that speed up DL training and inference.
- **Advanced video acceleration**. Ada GPUs deliver **up to 2× the power efficiency** of the previous generation.

---

## 4. Grace CPU and the Superchips
- **NVIDIA Grace** is NVIDIA's **first data center CPU**. It's **Arm-based** and built for **HPC**, and also suits **cloud and hyperscale** because it's **energy-efficient and scalable**.
- It's ideal for **memory- and bandwidth-hungry** workloads: **genomics, computational fluid dynamics, quantum chemistry**.

| Superchip | Combination | Best for |
|---|---|---|
| **Grace Hopper (GH200)** | Grace CPU + **H100 GPU** over **NVLink-C2C** (chip-to-chip) | The **most versatile platform for scale-out**. **Coherent CPU↔GPU memory**, a large **unified memory model**. It shines when **CPU performance and memory bandwidth** matter: **recommenders, graph databases, scientific computing** |
| **Grace Blackwell (GB200)** | Grace CPU + **two B200 GPUs** over NVLink-C2C at **900 GB/s bidirectional** | **Coherent unified memory** that **simplifies programming** for **trillion-parameter LLMs**, multimodal transformers, large simulations and 3D generative models |
| **Grace CPU Superchip** | **Two Grace CPUs** (CPU-only) | CPU apps where **performance, energy efficiency and density** matter: scientific computing, cloud, analytics, enterprise, hyperscale. It packs the performance of a **flagship two-socket x86-64 server into one superchip** |

---

## Key Terms
- **MIG (Multi-Instance GPU)**: splits one GPU into up to 7 isolated instances.
- **Transformer Engine**: hardware and software in Hopper and Blackwell that speed up transformer models.
- **Tensor Cores**: specialized units for deep learning math.
- **Confidential Computing**: processing data in an encrypted, isolated environment on the GPU.
- **NVLink-C2C**: a coherent chip-to-chip link between Grace and the GPU.
- **Superchip**: CPU and GPU (or CPU and CPU) packaged together with NVLink-C2C.
- **MoE (mixture of experts)**: a model architecture the Blackwell Transformer Engine speeds up.

## Exam Tips
- **Architecture to product:** Blackwell → **B200**, Hopper → **H100**, Ada Lovelace → **L40S**, Grace → the **Arm CPU**.
- **Know the numbers:** B200 has **208B transistors**, **5th-gen NVLink**, scales to **576 GPUs**. H100 has **80B transistors** and **900 GB/s** GPU-to-GPU. **MIG gives up to 7 instances.**
- **Both H100 and B200 have Confidential Computing.**
- **GH200 = Grace + H100. GB200 = Grace + 2× B200.** Both use **NVLink-C2C** for **coherent unified memory**.
- **Grace targets HPC, memory-bound workloads and energy-efficient hyperscale.**
- **L40S fits mixed workloads:** generative AI plus graphics, rendering and video.
