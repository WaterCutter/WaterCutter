# Haoyang He · CPU & Memory Subsystem Validation

Embedded Software Engineer → **SoC System Validation Engineer**

Focusing on **server-class SoC validation**, with deep expertise in CPU core microarchitecture, memory consistency, and reliability features. Currently validating **ARM Neoverse-based** systems, bridging pre-silicon architecture concepts with post-silicon hardware reality.

### Core Validation Domains
- **CPU Core & Microarchitecture**
  - ARMv8/v9 execution pipeline analysis, PMU-based performance profiling, and HPC kernel optimization using **ARM ACL**.
  - Instruction semantics validation and barrier instruction behavior (DMB/DSB) under multi-core workloads.

- **Cache Coherency & Interconnect**
  - CHI/CMN interconnect protocol validation using **Litmus tests** and **Cache Maintenance Operations (CMOs)**.
  - Coherency stress testing across multi-cluster topologies; root-causing cache-line contention and memory ordering violations.

- **DDR Subsystem & RAS**
  - DDRC initialization, training, and high-throughput memory stress validation.
  - **Reliability, Availability, and Serviceability (RAS)**: ECC injection, memory scrubbing, poison consumption handling, and error logging per ARM RAS extensions.

- **System-Level Debug**
  - Low-level debug using JTAG, logic analyzers, and trace infrastructure.
  - Root-cause analysis of subtle HW/SW interaction bugs: timing races, coherency protocol edge cases, and RAS corner cases.

### Background
Previously built full-stack embedded software stacks (Bootloader → RTOS → Linux) and led silicon bring-up for ARM/RISC-V platforms. That foundation now supports rigorous system-level validation of high-performance, safety-critical SoCs.

**Tech Stack**: ARM Neoverse, ARMv8/v9, CHI/CMN, DDRC, RAS (ECC/Scrub/Poison), Litmus, CMO, PMU, ARM ACL, U-Boot, FreeRTOS, Linux, C/C++, Assembly, JTAG.

📫 **Contact**: hehaoyang315@163.com

**Dlog**

```markdown
├── 📁 notes/
│   ├── 📁 methdology/
│   │   └── 📁 memory_system_consistency_validation/
│   │       └── [arm_soc_cmn_consistency_validation.md](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/notes/methdology/memory_system_consistency_validation/arm_soc_cmn_consistency_validation.md)
│   └── 📁 microarchitecture/
│       └── 📁 cmn/
│           └── 📁 why_rnf_no_cmo/
│               └── [why_rnf_no_cmo.md](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/notes/microarchitecture/cmn/why_rnf_no_cmo/why_rnf_no_cmo.md)
├── 📁 reports/
│   └── 📁 rca/
│       ├── 📁 cmn700_ap_scp_cache_coherency_issue/
│       │   └── [cmn700_ap_scp_cache_coherency_issue.md](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/reports/rca/cmn700_ap_scp_cache_coherency_issue/cmn700_ap_scp_cache_coherency_issue.md)
│       └── 📁 ldrd_non_atomic_cause_issue/
│           └── [ldrd_non_atomic_cause_issue_en.md](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/reports/rca/ldrd_non_atomic_cause_issue/ldrd_non_atomic_cause_issue_en.md)
└── [template_en.md](https://github.com/WaterCutter/arm-soc-validation-notes/blob/master/template_en.md)
```