# Unit 4: Accelerating AI with GPUs

**Exam mapping:** Topic 1, *Essential AI Knowledge*, and Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Recall milestones in GPU history and how GPU technology evolved.
2. Explain the core components of GPU architecture and what they do.
3. Compare CPU and GPU architecture: strengths and limits of each.
4. Apply knowledge of GPU server systems to plan, configure and deploy GPUs.
5. Evaluate NVIDIA's AI GPU families for specific AI and DL use cases.

> The agenda mentions the last three NVIDIA GPU architecture generations, but the transcript doesn't cover them in detail. Use the unit summary PDF for those.

---

## 1. GPU History in Brief
- A **GPU** (graphics processing unit) is a specialized circuit that **rapidly manipulates memory to speed up building images** in a frame buffer for display.
- A **pixel** is the smallest displayable unit of an image, with a **position, color and brightness**. Every pixel has to be processed fast enough that the eye sees no lag.
- **Higher screen resolution** means more pixel density, which needs more processing power. **The GPU does that pixel processing.**
- **Timeline:**
  - **1970s**: computer graphics begin to evolve
  - **1980s**: separate **graphics display processors**
  - **1990s**: **separate, swappable graphics boards and cards**

## 2. GPU Architecture
- **Thousands of GPU cores**, the parts that process data. Having many cores is what makes **parallel processing** possible.
- **On-board cache memory** for fast, reliable data access.
- **High-speed GPU memory**, closest to the cores. It's built for the GPU and **can be shared with other GPUs**.

## 3. Why GPU Computing Took Off

| Driver | Detail |
|---|---|
| **Model growth** | State-of-the-art model size grew by **3 orders of magnitude in 3 years**. That needs GPU compute, which CPUs can't supply, plus mature frameworks and tools |
| **Full-stack NVIDIA** | Architecture and platforms, **CUDA**, frameworks, **Triton** and **NGC**. Ongoing **co-optimization of hardware and software** keeps adding performance |
| **Faster adoption** | Time to 100M users: **WhatsApp took 49 months, ChatGPT took 2 months** |
| **Energy and power limits** | Data centers use **over 200 TWh a year**, about **2% of global energy**, projected to reach **5% by 2030**. They're **power-limited** and take **years to build**, so operators must get more from what they have. **Accelerated computing** is the way to do that |
| **"Moore's Law is dead"** (Jensen Huang, since 2017) | Growth in transistor density is slowing, a **physics limit** on miniaturization. **CPUs can't keep up**, so accelerated computing needs a **full-stack approach** (hardware, software, frameworks) |

- **Proof point:** the NVIDIA AI platform with **H100** set time-to-train records. LLM training went from **days to hours**, and for the largest LLMs from **a month to a week**.
- **Grace Hopper GH200** is covered in Unit 7.

---

## 4. CPU vs. GPU

| | **CPU** | **GPU** |
|---|---|---|
| Instruction sets | **Complex** | **Simple** |
| Cores | Multi-core, **up to 128**, with **fast clock speeds** | **Over 10,000** on the latest cards |
| Designed for | Running **many different applications at once**, each with 1 or a few **time-sliced threads** | **Highly parallel** tasks, the same operation on millions of items (rooted in rendering pixels) |
| Latency strategy | **Minimizes latency** with **large caches + complex control logic** (prefetching) | **Hides latency with computation**: gives the GPU more threads than it has cores and switches between them |
| Silicon spent on | Much of it on **data movement** | Mostly **computation** |
| Performance per watt | **Relatively low**, because energy goes to moving data | **Very efficient** |
| Main memory | **Large but low bandwidth** | **Smaller but very high bandwidth**, e.g. **H100: 80 GB at about 2 TB/s**, roughly **10× CPU memory** |
| Weak spot | **Cache misses** hurt performance | Needs **lots of concurrent work** to hide latency |

### How the GPU hides latency
1. The scheduler starts a thread on an operation, e.g. an addition.
2. If the data isn't ready, the thread **fetches it from memory and stalls**.
3. The scheduler **switches to another thread**, building a pipeline of instructions across many threads.
4. When the first thread's data arrives, it carries on.
- A **large register file** holds the state of every thread, so **switching costs nothing**, even every clock cycle.
- **The more work you give a GPU, the better it hides latency.** On a CPU you usually run 1–2 threads per core instead.
- Many applications are **bandwidth-bound rather than compute-bound**, so the GPU's memory bandwidth alone gives big speedups.

### How acceleration works
- Applications have **sequential parts** and **parallel parts**. The parallel parts may be small, but they're usually the **most compute-intensive**. Offloading them to the GPU can give **orders-of-magnitude speedups**.
- **CPU ↔ GPU data flow.** The CPU and GPU each have **their own memory**:
  1. Copy the data from **CPU memory to GPU memory**, usually over the **PCIe bus**.
  2. Copy the **code** (kernel) to the GPU and launch it. It runs using the GPU's cache layers.
  3. Copy the **results back to CPU memory**.
- **NVLink** is a faster alternative interconnect, covered in a later unit.

---

## 5. GPU Server Systems
- A **GPU server** is built to speed up **deep learning, scientific simulation and data analytics** with thousands of parallel cores.
- **GPU form factors:** **PCIe** (most common), **SXM** and **MXM**.

| System | What it is |
|---|---|
| **DGX H100** | A **fully integrated hardware + software** solution, the basis for an AI center of excellence |
| **HGX H100** | **H100 Tensor Core GPUs + high-speed interconnects** that partners build "the world's most powerful servers" on |
| **H100 PCIe** | The **highest PCIe-card memory bandwidth**: **over 2,000 GB/s** |
| **MGX** | A **modular reference design** for many use cases, from remote visualization to edge supercomputing. It **improves ROI and shortens time to market** |

- **Ecosystem:** Cisco, Dell, HPE, IBM, Lenovo and others sell GPU servers with **2–16 GPUs each**, which can be **interconnected into multi-server systems**. **Every major cloud provider** offers NVIDIA GPUs.

### Where GPUs are used
- **Compute-intensive:** AI training and inference, data analytics, **HPC**.
- **General purpose:** visualization, rendering, virtual workstations, deep learning.
- **High-density virtualization:** virtual desktops and workstations.
- **Enterprise edge** (controlled environments) and **industrial edge** (rugged environments).
- **Desktop and mobile workstations:** design, content creation, data science, software development.

---

## Key Terms
- **GPU**: a highly parallel processor, originally for graphics, now the engine of accelerated computing.
- **Core**: the processing element. CPUs have a few powerful ones. GPUs have thousands of simple ones.
- **Latency hiding**: oversubscribing threads so the GPU computes while other threads wait on memory.
- **Register file**: on-chip storage for thread state. It's what lets the GPU switch threads at no cost.
- **Bandwidth-bound**: limited by how fast data moves, not by math throughput.
- **PCIe / SXM / MXM**: GPU form factors. **NVLink** is NVIDIA's high-speed GPU interconnect.
- **DGX / HGX / MGX**: an integrated system / a platform for partner servers / a modular reference design.
- **Moore's Law slowing**: the reason accelerated computing is needed.

## Exam Tips
- **CPU means low latency (big caches, complex control). GPU means high throughput (hides latency with many threads).**
- **GPUs have better performance per watt** because their silicon goes to computation, not data movement.
- **GPU memory is smaller but much faster.** Know **H100: 80 GB at about 2 TB/s**.
- **Offload flow:** CPU→GPU copy over **PCIe**, run the kernel, copy results back. **NVLink** is the faster path.
- **Data centers are about 2% of global energy, heading to 5% by 2030.** They're power-limited, so accelerated computing is the answer.
- Know the system names: **DGX** (turnkey), **HGX** (partner building block), **MGX** (modular), **H100 PCIe**.
