# 🧠 SADP & SCDP: Fast Agreement-Driven Learning Rules for Spiking Neural Networks

This repository provides implementations and benchmarks for **Spike Agreement-Dependent Plasticity (SADP)** and **Spike Correlation-Dependent Plasticity (SCDP)** — biologically grounded, **hardware-compatible learning rules** for Spiking Neural Networks (SNNs).

SADP replaces pairwise spike-timing updates (as in STDP) with **global spike-train agreement** based on *Cohen’s κ*, while SCDP uses the raw *Pearson correlation* to model co-firing intensity. Both achieve **linear-time (O(T))** complexity and are **neuromorphic-hardware friendly**, enabling local, efficient learning without gradient backpropagation.

Additionally, this repository includes **benchmark baselines** for classical STDP, Hebbian learning, and a **supervised surrogate-gradient SNN** to contextualize performance.

---

## 🔬 Core Features

- 📊 **Agreement- or correlation-driven plasticity** instead of pairwise Δt-based STDP.
- 🔁 **Spline-based learning kernels** derived from ideal models or **memtransistor conductance data**.
- ⚡ **Linear-time weight updates**, no spike matching or causal timing required.
- 🧩 **Fully local and biologically plausible** — no global error propagation.
- 💡 **Hardware-friendly formulation**, suitable for event-driven neuromorphic substrates.
- 📈 Benchmarks on **MNIST** and **Fashion-MNIST**, comparing SADP, SCDP, STDP, Hebbian, and Surrogate Gradient methods.

---

## 📂 Repository Structure

| File / Folder | Description |
|----------------|--------------|
| `SADP_functions.ipynb` | Core SADP functions and spline kernel computation. |
| `SCDP_functions.ipynb` | Core SCDP functions based on Pearson correlation. |
| `Benchmarking_SADP.ipynb` | SADP benchmark on MNIST and FMNIST (rate / TTFS coding). |
| `Benchmarking_SCDP.ipynb` | SCDP benchmark for ablation study comparing κ vs ρ. |
| `Benchmarking_STDP.ipynb` | Classical STDP baseline (pairwise causal updates). |
| `Benchmarking_Hebbian.ipynb` | Rate-based Hebbian baseline (Oja-style updates). |
| `Benchmarking_surrogate_gradient.ipynb` | Supervised surrogate-gradient SNN for upper-bound reference. |
| `requirements.txt` | CPU-based Python environment specification. |
| `requirements_gpu.txt` | GPU-accelerated environment (CUDA 11.x). |

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
  - SADP (Cohen’s κ)
  - SCDP (Pearson ρ)
  - STDP (under limited settings)
  - Hebbian (under limited settings)
  - Surrogate Gradient
- **Update Kernels**:
  - SADP/SCDP updates computed using learned spline from measured ΔG/G₀ values
  - STDP based on timing difference between spike pairs
- **Evaluation Metrics**:
  - Runtime
  - Classification accuracy over time
 
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
