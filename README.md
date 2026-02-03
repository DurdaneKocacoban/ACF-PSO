# Advanced Composite Fitness Particle Swarm Optimization for S-box Design

> Achieving theoretical maximum nonlinearity (112) for 8-bit S-boxes through a novel composite fitness PSO framework with guided swaps, triple swap operations, and adaptive perturbation strategies.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Repository Structure](#repository-structure)
- [Experiments](#experiments)
  - [1. Main Experiments](#1-main-experiments-main_experiments)
  - [2. Weight Sensitivity Analysis](#2-weight-sensitivity-analysis-weight_sensitivity)
  - [3. Ablation Study](#3-ablation-study-ablation)
  - [4. Multiple Run Tests](#4-multiple-run-tests-multiple_runs)
- [File Format Reference](#file-format-reference)
- [Requirements](#requirements)
- [Contact](#contact)

---

## 🔍 Overview

This repository provides the complete experimental data accompanying our research on **S-box optimization via Particle Swarm Optimization (PSO)**. The proposed algorithm employs a **composite fitness function** that simultaneously optimizes nonlinearity (NL), Strict Avalanche Criterion (SAC), and Differential Distribution Table (DDT) properties to construct cryptographically strong S-boxes.

The optimization framework introduces several novel components — including **guided swap (local best & global best)**, **triple swap**, and **perturbation** mechanisms — that work together to escape local optima and consistently reach the **theoretical maximum nonlinearity of 112** for 8 bit S-boxes. An early stopping criterion based on the NL threshold further ensures computational efficiency.

All experiments are fully reproducible and organized into four complementary categories: main experiments validating the approach across diverse configurations, weight sensitivity analysis quantifying the impact of fitness component weights, ablation studies isolating each algorithmic component's contribution, and multiple-run tests confirming stability and reproducibility.

## ✨ Key Features

- **Composite Fitness Function** — Joint optimization of NL, SAC, DDT, and Entropy
- **Guided & Triple Swap Operators** — Domain-specific mutation strategies for S-box permutations
- **Adaptive Perturbation** — Escape mechanism for stagnation in local optima
- **Early Stopping** — NL-threshold-based termination for computational efficiency
- **Scalable PSO** — Tested with population sizes of 100, 200, and 1000 particles

 experiments/                                                                                                                                                                                  └─────┴──────┴────────┴─────────┴──────┴──────┴────────┴────────────────┴──────┘                                                                                                                                   
                                                                                                                                                                                                                     
## 📁 Repository Structure                                                                                                                                                                                         
                                                                                                                                                                                                                     
  ```                                                                                                                                                                                                                
                                                                                                                                                                                                                     
  experiments/

  ├── TABLE III-OPTIMISATION RESULTS ACROSS ALL TESTED EXPERIMENTAL RUNS/          # 30 independent optimization runs                                                                                                                                                  
                                                                                                                                                                                                                     
  │   ├── Case_1_#P100_99.00_to_112/                                                                                                                                                                                 
                                                                                                                                                                                                                     
  │   │   ├── initial_sbox.txt                                                                                                                                                                                       
                                                                                                                                                                                                                     
  │   │   ├── final_sbox.txt                                                                                                                                                                                         
                                                                                                                                                                                                                     
  │   │   └── global_best_swaps_only.log                                                                                                                                                                             
                                                                                                                                                                                                                     
  │   ├── Case_2_#P100_99.00_to_112/                                                                                                                                                                                 
                                                                                                                                                                                                                     
  │   └── ...                                                                                                                                                                                                        
                                                                                                                                                                                                                     
  │  


  ├── TABLE VI-STATISTICAL ANALYSIS ACROSS 10 INDEPENDENT RUNS/             # Stability & reproducibility tests

  │   ├── 1_Case28_100.00_TenRuns/                                                                                                                                                                                 
  │   │   ├── run01/ ... run05/                                                                                                                                                                                                                    
  │   │   │   ├── initial_sbox.txt                                                                                                                                                                                       
                                                                                                                                                                                                                     
  │   │   │   ├── final_sbox.txt                                                                                                                                                                                         
                                                                                                                                                                                                                     
  │   │   │   └── global_best_swaps_only.log  
                                                                                                                                                                                                                     
                                                                                                                                                                                                                    
  ├── TABLE VII-WEIGHT SENSITIVITY ANALYSIS RESULTS/        # 9 configurations × 5 runs = 45 runs                                                                                                                                               
                                                                                                                                                                                                                     
  │   ├── A_.70/.20/.10_97.25/           # Weight set 01, Initial A, NL start 97.25                                                                                                                                           
                                                                                                                                                                                                                     
  │   │   ├── run01/ ... run05/                                                                                                                                                                                      
                                                                                                                                                                                                                     
  │   ├── B_.15/.70/.15_101.75/                                                                                                                                                                                               
                                                                                                                                                                                                                     
  │   └── ...                                                                                                                                                                                                        
                                                                                                                                                                                                                     
  │                                                                                                                                                                                                                                                                                                                                                                                                                                     
  ├── TABLE IX-ABLATION STUDY RESULTS/                  # 3 variants × 5 initials × 5 runs = 75 runs                                                                                                                                        
                                                                                                                                                                                                                     
  │   ├── V3_ w/o Triple Swap   /                   # Without Triple Swap                                                                                                                                                                
                                                                                                                                                                                                                     
  │   │   ├── 97.25/ ... 103.25/                                                                                                                                                                                     
                                                                                                                                                                                                                     
  │   │   │   ├── RUN 1/ ... RUN 5/                                                                                                                                                                                  
                                                                                                                                                                                                                     
  │   ├── V4_ w/o Perturbation /                   # Without Perturbation                                                                                                                                                               
                                                                                                                                                                                                                     
  │   ├── V5_ w/o Guided Swap /                   # Without Guided Swap                                                                                                                                                                
                                                                                                                                                                                                                     
  │   └── ...                                                                                                                                                                                                        
                                                                                                                                                                                                                     
  │                                                                                                                                                                                                                                                                                                                                                                                                                                    
  └── readme.md    
## 🧪 Experiments

### 1. Main Experiments (`TABLE III-OPTIMISATION RESULTS ACROSS ALL TESTED EXPERIMENTAL RUNS/`)

| Detail | Value |
|---|---|
| **Total Runs** | 30 |
| **Population Sizes** | 100, 200, 1000 |
| **Target NL** | 112 (theoretical maximum) |
| **Starting NL Range** | 97.25 – 111.75 |

The main experiments evaluate the full proposed algorithm across varying particle counts and initial S-box qualities. Each `Case_X` folder represents an independent optimization trial. The folder naming convention encodes the configuration: `Case_{id}_#P{particles}_{startNL}_to_{targetNL}`.

Each case directory contains three files: the starting S-box permutation (`initial_sbox.txt`), the optimized result (`final_sbox.txt`), and a detailed log of every global best improvement (`global_best_swaps_only.log`).

### 2. Multiple Run Tests (`TABLE VI-STATISTICAL ANALYSIS ACROSS 10 INDEPENDENT RUNS/`)

| Detail | Value |
|---|---|
| **Configurations** | 4 |
| **Consecutive Runs** | 10 per configuration |

These experiments assess algorithmic **stability and reproducibility** by executing each configuration 10 consecutive times under identical conditions.

### 3. Weight Sensitivity Analysis (`TABLE VII-WEIGHT SENSITIVITY ANALYSIS RESULTS/`)

| Detail | Value |
|---|---|
| **Weight Configurations** | 3 |
| **Initials per Config** | 3 (A, B, C) |
| **Runs per Initial** | 5 |
| **Total Runs** | 45 |

This experiment investigates how different weightings of the composite fitness components affect optimization performance. Three distinct weight profiles are tested:

| ID |    Profile   | w_NL | w_SAC | w_DDT |
|----|--------------|------|-------|------|
|  A | NL-Dominant  | 0.70 | 0.20  | 0.10 |
|  B | SAC-Dominant | 0.15 | 0.70  | 0.15 |
|  C | DDT-Dominant | 0.10 | 0.20  | 0.70 |

Folder naming follows the pattern `{weightID}-{w_NL/w_SAC/w_DDT}-{initial}` (e.g., `A_.70/.20/.10_97.25` uses the NL-dominant weights with initial `A` starting at NL = 97.25). Each configuration is repeated 5 times (`run01`–`run05`) with the same three output files per run.

### 3. Ablation Study (`TABLE IX-ABLATION STUDY RESULTS/`)

| Detail | Value |
|---|---|
| **Variants** | 3 (V3, V4, V5) |
| **Initial NL Values** | 5 (97.25, 99, 100, 101.75, 103.25) |
| **Runs per Setting** | 5 |
| **Total Runs** | 75 |

The ablation study systematically removes individual algorithmic components to quantify their contribution. Each variant disables a single mechanism while keeping all others active:

| Variant | Description | Removed Component |
|---|---|---|
| V1 | Full model (baseline) | — |
| V2 | Without Composite Fitness | Composite fitness function |
| **V3** | Without Triple Swap | Triple swap operator |
| **V4** | Without Perturbation | Perturbation mechanism |
| **V5** | Without Guided Swap | Guided swap operator |

> **Note:** V1 and V2 results are captured through the main experiments. This directory contains V3, V4, and V5 data, each tested across 5 different starting NL values with 5 independent runs per setting.

---

## 📄 File Format Reference

Every experiment run produces three files:

| File | Description |
|---|---|
| `initial_sbox.txt` | The starting 16x16 S-box permutation (256 `UInt8` values, 16 per line) |
| `final_sbox.txt` | The optimized S-box after PSO convergence or early stopping |
| `global_best_swaps_only.log` | Timestamped log of every global best improvement, including step number, particle ID, swap type, indices, and fitness deltas |

The log file records each global best event with its full context: the swap operations applied (e.g., `RANDOM_SWAP`, `GUIDED_SWAP`), local and global fitness improvements, and the timestamp at which the improvement occurred.

## 🔧 Requirements

```
Julia v1.11.2

ProgressMeter v1.11.0
Random        v1.11.0
Statistics    v1.11.1
Distributed   v1.11.0
Dates         v1.11.0
Printf        v1.11.0
Base.Threads  (Julia core)
```

## 📧 Contact

**Durdane (Kocacoban) Caglar** — [dk796@alumni.york.ac.uk](mailto:dk796@alumni.york.ac.uk)

**Ibrahim Caglar** — [ibrahimcaglar@alumni.york.ac.uk](mailto:ibrahimcaglar@alumni.york.ac.uk)
