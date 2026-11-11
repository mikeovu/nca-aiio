# Unit 10: Energy-Efficient Computing

**Exam mapping:** Topic 2, *AI Infrastructure*
**Source:** AI Infrastructure and Operations Fundamentals course, unit transcript

## What you should be able to do after this unit
1. Explain how **space, power and cooling** shape data center design and planning.
2. Discuss how NVIDIA's methods and servers **improve energy efficiency**.
3. Describe **cooling architectures** for GPUs.
4. Understand how **colocation** improves efficiency.

---

## 1. Planning a Data Center

### Five process domains to balance
1. **Data center operations**
2. **IT operations**
3. **NOC support** (network operations center)
4. **Application owner**
5. **Network operations**

These have to be **coordinated continuously**.

### Three finite resources: **power, cooling and space**
- **Changing one affects the other two**, so resource use has to be optimized.
- AI's massive data, complex models and heavy processing have caused an **explosion in data center energy demand**.

---

## 2. Why GPUs Save Energy
- **A GPU draws more power at any moment, but finishes much faster**, so it **uses less energy overall**.
- GPUs handle large compute jobs with **less hardware and less space**.
- **MIG** runs **several partitions at once without raising the GPU's power use**.

### Headline numbers

| Claim | Number |
|---|---|
| Hyperscale data center on NVIDIA GPUs vs. the CPU systems it replaces | **1/47th the rack space**, **93% lower energy cost** for AI models |
| Software gains on the **same hardware** (CUDA-X tuning) | AI on **Ampere improved 2.5×** in two years |
| Following NGC performance suggestions | About **20% energy savings** |
| **DPUs** offloading communication tasks from CPUs | Relieve **30%+** of CPU load. Some workloads run **50× faster**, cutting a modest data center's power by **4 MW** |
| DPU-enabled **zero-trust** security | Up to **600× faster** than servers without NVIDIA acceleration |
| **Spectrum-4** Ethernet switch | **40% lower power** than the previous generation |
| **HGX H100 (4-GPU) vs. dual-socket Sapphire Rapids CPU servers** on HPC apps | **22.9× geomean** speedup, so you'd need **about 23× as many CPU servers**. A 50-node HGX system uses **2.6 GWh/yr** vs. **12.1 GWh/yr** for 1,150 CPU servers |
| **H100 vs. A100** (same workload) | 64 H100s: **1/3 the TCO**, **1/5 the server nodes**, **3.5× more energy efficient** |
| **Ampere TF32** math mode | Same accuracy as FP32 training, with **10× faster tensor math** than single precision on **Volta** |

- **The key efficiency metric is application throughput per kilowatt-hour.**
- **Generation over generation** (e.g. Ampere → Hopper), GPUs get more efficient, and **finishing jobs faster cuts GPU time**. NVIDIA is aiming for a **net-zero data center**.

### How NVIDIA designs for efficiency
- **Computational fluid dynamics** models improve cooling for data centers and racks.
- **Physics-informed neural networks (PINNs)** in **NVIDIA Modulus** are used to **design DGX heat sinks**.
- **Cooling is closely coupled with racks** to localize heat transfer.
- NVIDIA **shares best practices** and publishes **reference architectures** with storage and networking partners.

---

## 3. DGX H100 Environmental Needs
- The DGX H100 is the **compute building block of DGX SuperPOD**.
- It's **air-cooled** and needs intake air at **5–30 °C (41–86 °F)**.
- It draws **up to 10.2 kW** per system.

---

## 4. Heat and Cooling

### Why GPUs are "the hottest thing in computing"
- **99.99% of a chip's power becomes heat.**

| | Per chip | Per rack |
|---|---|---|
| **CPU** | 8 W → **150 W** over time | **4–12 kW** |
| **GPU** | **250–500 W** | **12–45 kW** today, about **60 kW** for the next generation, **100–120 kW** in the future |

- **Liquid-cooled GPUs** use **less power and less rack space**, helping meet NVIDIA's target of **PUE below 1.2**.

### Cooling options

| Option | Capacity per rack | Trade-off |
|---|---|---|
| **Cold air** | **Up to about 30 kW** | **Cheap**, but hits a limit |
| **Water-cooled heat exchangers** | **20–60 kW** (some vendors claim **100+ kW**) | **More efficient but more expensive.** Now the **accepted standard for high-density cooling** |

### How direct air cooling works (CRAH and raised floor)
1. **CRAH units** (computer room air handlers) blow air across **chilled-water coils**.
2. CRAH fans **pressurize cold air under the raised floor**.
3. **Floor grates** in contained aisles let cold air reach the **front of the racks**.
4. Server fans **pull the cold air in** and **exhaust hot air out the back**.
5. Hot air **returns to the CRAH through the ceiling**, and its heat moves into the chilled water.

- **The hot aisle / cold aisle** layout optimizes airflow. **Fit blanking panels** wherever possible.

### Rear-door heat exchangers
- **Chilled-water coils in the rack's rear door**, about **6 inches from the servers**, capture the heat and carry it outside.
- **Rear-door exchangers suit solid or slab floors. Cold-aisle containment with air cooling suits raised floors.**

### Power provisioning
- **Finish power provisioning before** connecting rack **PDUs** and deploying systems.
- NVIDIA recommends **redundant power sources for every component**. **Validate AC redundancy at each rack.**
- An **electrician or facility rep must verify AC voltage and total kW** at every floor PDU and circuit (power drop).
- **Label the equipment on every breaker.**

---

## 5. Colocation: the DGX-Ready Data Center Program
- **The problem:** a **DGX H100 draws up to 10.2 kW**, and a **DGX SuperPOD needs more than 40 kW per rack**. **Many enterprise data centers support only 8–15 kW per rack**, or less.
- **The answer:** the **DGX-Ready Data Center program**. NVIDIA partners host DGX systems in their colocation facilities.
  - A **pairing function** matches you with the right partner. It's available in Asia, Australia, Europe, North America and South America.
  - Some partners also offer a **test drive** and **GPU-as-a-service**.
  - You **avoid facilities planning** and the **cost and latency of the public cloud**, with an affordable **OpEx** model.
  - It supports DGX reference architectures with **DDN, IBM Storage, NetApp, Pure Storage and Dell EMC**.

---

## Key Terms
- **Power, cooling, space**: the three finite data center resources. They trade off against each other.
- **PUE**: power usage effectiveness, total facility power divided by IT power. NVIDIA targets **below 1.2** with liquid cooling.
- **TDP**: thermal design power, the maximum sustained power and heat of a chip.
- **CRAH**: computer room air handler, which cools air with chilled-water coils.
- **Hot aisle / cold aisle**: rack layout that separates intake from exhaust air.
- **Blanking panels**: fill empty rack slots so hot exhaust doesn't recirculate.
- **Rear-door heat exchanger**: chilled-water coil on the back of the rack.
- **PDU**: power distribution unit inside the rack.
- **TF32**: Ampere's math mode with FP32 accuracy at tensor-core speed.
- **DGX-Ready Data Center**: a colocation program for hosting DGX systems.

## Exam Tips
- **GPUs draw more power but finish sooner, so they use less energy in total.** The metric is **throughput per kWh**.
- **The three resources are power, cooling and space. Changing one affects the other two.**
- **Air cooling tops out around 30 kW per rack. Water-cooled heat exchangers handle 20–60 kW and are the standard for high density.**
- **GPU racks run 12–45 kW today, heading to 100–120 kW.** **99.99% of chip power becomes heat.**
- **DGX H100 is air-cooled at 5–30 °C and draws up to 10.2 kW. SuperPOD needs more than 40 kW per rack. Typical enterprise racks give 8–15 kW**, which is why **colocation** exists.
- **Rear-door exchangers go with slab floors. Cold-aisle containment goes with raised floors.**
- **Power: provision before deploying, use redundant feeds, validate per rack, label breakers.**
- **Liquid cooling targets PUE below 1.2.**
