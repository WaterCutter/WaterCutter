# WaterCutter · CPU & Memory Subsystem Validation

**Embedded Software Engineer & SoC System Validation Expert**

Focusing on **server-class SoC validation**, with deep expertise in CPU core microarchitecture, memory consistency, and RAS features. Currently validating **ARM Neoverse-based** systems, bridging pre-silicon architecture concepts with post-silicon hardware reality.

---

### Core Validation Domains

- **CPU Core & Microarchitecture**
  - ARMv8/v9 execution pipeline analysis, PMU-based performance profiling, and HPC kernel optimization using **ARM ACL**.
  - Instruction semantics validation and barrier instruction behavior (DMB/DSB) under multi-core workloads.

- **Cache Coherency & Interconnect**
  - CHI/CMN interconnect protocol validation using **Litmus tests** and **Cache Maintenance Operations (CMOs)**.
  - Coherency stress testing across multi-cluster topologies; root-causing cache-line contention and memory ordering violations.

- **DDR Subsystem & RAS**
  - **Reliability, Availability, and Serviceability (RAS)**: ECC injection, memory scrubbing, poison consumption handling, and error logging per ARM RAS extensions.

- **System-Level Debug**
  - Low-level debug using JTAG, logic analyzers, and trace infrastructure.
  - Root-cause analysis of subtle HW/SW interaction bugs: timing races, coherency protocol edge cases, and RAS corner cases.

---

### Background

Previously built full-stack embedded software stacks (Bootloader → RTOS → Linux) and led silicon bring-up for ARM/RISC-V platforms. That foundation now supports rigorous system-level validation of high-performance, safety-critical SoCs.

**Tech Stack**: ARM Neoverse, ARMv8/v9, CHI/CMN, DDRC, RAS (ECC/Scrub/Poison), Litmus, CMO, PMU, ARM ACL, U-Boot, FreeRTOS, Linux, C/C++, Assembly, JTAG.

📫 **Contact**: watercutterx@gmail.com

---

## Dlog · Technical Repository

> Practical documentation distilled from real silicon bugs and architectural validation challenges.  
> **Repo**: [arm-soc-validation-notes](https://github.com/WaterCutter/arm-soc-validation-notes)

---

### Issue Template

- [SoC Validation Issue Report Template (EN)](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/template_en.md)  
  Standardized template for reporting and tracking SoC validation issues — covers symptom description, repro steps, logs, root cause, and fix verification.

---

### Notes · Methodology & Microarchitecture

#### `notes/methdology/` — Validation Methodology

- **[Arm Soc Consistency Validation Methodology](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/notes/methdology/memory_system_consistency_validation/arm_soc_consistency_validation_method.md)**  
   Systematically presents a methodology for sequential consistency verification, covering memory model definitions, formal execution modeling, graph-based violation detection, and engineering implementation through litmus tests and CMO validation.

#### `notes/microarchitecture/cmn/` — CMN Interconnect Deep Dives

- **[Why No Manual CMO Is Required Between Two RN-F (AP Cores)](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/notes/microarchitecture/cmn/why_rnf_no_cmo/why_rnf_no_cmo.md)**  
  Explains automatic coherency maintenance between RN-F nodes through MOESI state machines, CHI protocols, and CMN SAM configurations — correcting the misconception that "DDR always holds the latest data."

---

### Reports · Root Cause Analysis (Real Silicon Bugs)

#### `reports/rca/` — Production Bug Postmortems

- **[CMN-700 AP → SCP Cache Coherency Issue](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/reports/rca/cmn700_ap_scp_cache_coherency_issue/cmn700_ap_scp_cache_coherency_issue.md)**  
  **Symptom**: SCP (Cortex-M7 via SNI) reads stale data after AP (Neoverse NX) writes to DDR.  
  **Root Cause**: Cross-domain access bypassing the Snoop Filter; resolved via explicit CMOs or Non-Cacheable memory attributes.

- **[LDRD Non-Atomic Read Causes Interrupt Storm (Cortex-M7)](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/reports/rca/ldrd_non_atomic_cause_issue/ldrd_non_atomic_cause_issue_en.md)**  
  **Symptom**: Repeated interrupt triggering due to non-atomic `LDRD` on Device MMIO with read-to-clear side effects.  
  **Fix**: Split 64-bit access into two 32-bit loads combined with compiler barriers.
