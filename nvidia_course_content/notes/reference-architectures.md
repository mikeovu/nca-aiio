# Unit 11: Reference Architectures

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

---

## 1. What a Reference Architecture Is
- Dense computing environments have many parts: **compute servers, network fabrics, storage and management servers**. **Designing them for maximum performance is hard.**
- A **reference architecture** is a **design document** that shows a **recommended, best-practice implementation** of a system. You use it as a **foundation** to build from.

### Benefits
1. Shows **how a specific design solves problems**.
2. Gives a **foundation you can tailor** to your organization.
3. **Cuts design and planning cost and time**, so you get to a solution faster.
4. **Improves quality and reliability** by **reducing complexity**.

### NVIDIA reference architectures
- **DGX BasePOD**
- **DGX SuperPOD**
- **DGX GH200**
- **NVIDIA AI Enterprise**
- **Cloudera Data Platform**

The last two **aren't tied to specific NVIDIA servers**. They cover **node configurations, network topology and deployment topology**.

---

## 2. DGX BasePOD
- **The integrated infrastructure and software to deploy and run AI workloads.** It combines:
  - **NVIDIA DGX systems** (compute)
  - **NVIDIA networking**
  - **NVIDIA Base Command** software, the "glue"
  - **NVIDIA AI Enterprise** software and MLOps offerings
  - **partner storage**
- Scale: **up to 8 DGX systems** (**B200, H200 or H100**).
- **The idea:** it turns world-leading components into a **cohesive, full-stack solution**.

### DGX systems in BasePOD

| System | GPUs | FP8 performance |
|---|---|---|
| **DGX B200** | **8× Blackwell** | **72 petaFLOPS** |
| **DGX H200 / DGX H100** | **8× Hopper** | **32 petaFLOPS** |

- Every DGX has a **1 GbE port for out-of-band management** through the **BMC (baseboard management controller)**. The BMC allows **remote management even when the system is powered off**.
- **Network adapters:**
  - **H200 and H100** use **ConnectX-7**.
  - **B200** uses **ConnectX-7 and BlueField-3**.
  - Adapters can run as **InfiniBand or Ethernet**.
- **Usual split:** **InfiniBand for the compute network**. **Ethernet for storage, in-band management and out-of-band management.**

### Switches

| Switch | Type | Speed | Role in BasePOD |
|---|---|---|---|
| **QM9700** | InfiniBand | **NDR = 400 Gb/s** (or 200 Gb/s) | Compute fabric for DGX H100 (400G) or DGX A100 (200G) |
| **QM8700** | InfiniBand | **HDR = 200 Gb/s** | Compute fabric with **DGX A100** |
| **SN5600** | Ethernet | **10–800 GbE** | **GPU-to-GPU** fabrics |
| **SN4600** | Ethernet | **1–200 GbE** | **In-band management**, and can carry **storage** |
| **SN2201** | Ethernet | **1–100 GbE** | **Out-of-band management** |

**Remember:** **NDR stands for "Next Data Rate" (400 Gb/s). HDR stands for "High Data Rate" (200 Gb/s).**

### Example: BasePOD with up to 8 nodes on NDR400 InfiniBand
Applies to **DGX H100, H200 and B200**. It has **three networks**:
1. An **InfiniBand compute network**, using ConnectX-7.
2. An **Ethernet fabric for storage and in-band management**, using **SN4600C** switches.
3. An **out-of-band management network**.

---

## 3. DGX SuperPOD
- **Next-generation AI supercomputing infrastructure for AI factories**, built on **DGX H100, H200, B200, B300 and GB200**.
- Combines DGX systems, **InfiniBand and Ethernet** networking, **management nodes**, storage and optimized software.
- **Built from scalable units (SUs):** each SU is a set number of DGX systems, depending on model and configuration. You add SUs to grow **up to thousands of GPUs**. It's **modular and scalable**.
- **Deployed in customer data centers and at cloud service providers** worldwide.

---

## Key Terms
- **Reference architecture**: a documented, best-practice system design to build from.
- **DGX BasePOD**: up to 8 DGX systems + NVIDIA networking + Base Command + AI Enterprise + partner storage.
- **DGX SuperPOD**: AI-factory-scale infrastructure built from **scalable units**.
- **Scalable unit (SU)**: the modular building block of a SuperPOD.
- **Base Command**: NVIDIA's software that ties BasePOD together and manages it.
- **BMC**: baseboard management controller, out-of-band management that works even when the system is off.
- **NDR / HDR**: InfiniBand speeds, 400 / 200 Gb/s.

## Exam Tips
- **Reference architecture benefits:** solves problems, can be tailored, saves time and cost, improves quality by reducing complexity.
- **BasePOD = up to 8 DGX (B200, H200, H100) + networking + Base Command + AI Enterprise + partner storage.**
- **SuperPOD = AI factory scale, built from scalable units, up to thousands of GPUs.**
- **DGX B200 does 72 PF FP8. DGX H100 and H200 do 32 PF FP8.** Each has **8 GPUs**.
- **InfiniBand carries compute traffic. Ethernet carries storage and management.** Out-of-band management goes through the **BMC's 1 GbE port**.
- **Match switch to role:** QM9700 (NDR IB compute), QM8700 (HDR IB, A100), SN5600 (GPU fabric Ethernet), SN4600 (in-band and storage), SN2201 (out-of-band).
