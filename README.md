# 🧠 SADP: Spike Agreement-Dependent Plasticity

**SADP** (Spike Agreement-Dependent Plasticity) is a biologically grounded, hardware-compatible synaptic learning rule for spiking neural networks (SNNs). It replaces pairwise spike-timing updates (STDP) with agreement-based plasticity driven by global spike-train similarity (e.g., Cohen’s κ). 

SADP is especially designed for neuromorphic substrates like **memtransistors**, using spline-fitted update kernels derived from real device conductance traces.

---

## 🔬 Core Features

- 📊 Global **spike-train agreement** instead of pairwise Δt.
- 🔁 **Spline-based learning kernels** derived from memtransistor data.
- ⚡ **Linear-time weight updates**, no spike matching needed.
- 🧠 **Neuromorphic-hardware friendly** and fully on-chip implementable.
- 📈 **Benchmarks against STDP and Hebbian** learning on spiking MNIST.

---

## 📂 Repository Structure

| File / Folder                   | Description                                         |
|--------------------------------|-----------------------------------------------------|
| SADP_functions.ipynb         | Core SADP functions, spline kernel computation.     |
| Benhmarking_SADP.ipynb       | SADP benchmark on MNIST with spike-coded inputs.    |
| Benhmarking_STDP_other.ipynb | STDP and Hebbian benchmarks (comparison baselines). |
| requirements.txt             | CPU-based Python environment.                       |
| requirements_gpu.txt         | GPU-accelerated version with CUDA dependencies.     |

---

## ⚙️ Installation

Install using pip for either CPU or GPU version:

### ✅ CPU version


pip install -r requirements.txt

###⚡ GPU version (CUDA 11.1 compatible):

pip install -r requirements_gpu.txt

### 🚀 Quick Start
After installing, launch the benchmark notebooks:
jupyter notebook Benhmarking_SADP.ipynb

---

## 📊 Benchmarking Settings

All benchmarks were conducted using a biologically plausible spiking network trained on:

- **Dataset**: Rate-coded MNIST (10 time steps per sample)
- **Network Architecture**:
  - Input layer: 784 units (28×28 flattened pixels)
  - Hidden layer: 400 spiking neurons
  - Output layer: 10 spiking neurons
- **Encoding**: Poisson spike encoding over 10 discrete time steps
- **Learning Rules Compared**:
  - SADP (agreement-based, spline-calibrated from memtransistor data)
  - STDP (classical causal/asymmetric exponential kernel)
  - Hebbian (unsupervised, correlation-based)
- **Update Kernels**:
  - SADP updates computed using learned spline from measured ΔG/G₀ values
  - STDP based on timing difference between spike pairs
- **Evaluation Metrics**:
  - Classification accuracy over time
  - Synaptic weight evolution
  - Robustness to spike-timing noise
- **Simulation Platform**: NumPy-based implementation with batch simulation

---

## 📌 License & Citation

This repository is released under the MIT License.

If you use this code or ideas from this project, please consider citing our upcoming preprint. Citation entry will be added upon publication.

---

## 🔑 Keywords

Spiking Neural Networks · SADP · Memtransistor Plasticity · Neuromorphic Learning · Spline-Based Learning Kernels

---

## 👥 Contributors

- Saptarshi Bej (Lead Developer)

We welcome issues, suggestions, and pull requests!
