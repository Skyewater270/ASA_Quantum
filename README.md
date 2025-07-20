# QGB_Project
---

# **Quantum Galton Box: Monte Carlo Simulation on Quantum Circuits**

## **1. Overview**

This project demonstrates how **quantum circuits** can simulate complex systems using a **Galton Box (Plinko)-style Monte Carlo approach**, inspired by the **Universal Statistical Simulator**. Monte Carlo simulations are essential for solving **high-dimensional problems** such as **particle transport, quantum systems, and PDEs with complex interactions**.

The **Quantum Galton Box** models the probabilistic motion of a particle (or ball) through layers of pegs, forming a distribution of final positions. Classically, such systems tend to produce a **Gaussian distribution** due to the **Central Limit Theorem**. In a **quantum implementation**, **superposition** and **interference** allow exponentially faster sampling of many trajectories simultaneously, potentially offering significant advantages for **high-dimensional statistical simulations**.

This project builds upon the foundations of the **Quantum Fourier Transform (QFT)** and quantum sampling methods, exploring how quantum devices can be optimized for statistical simulations under both ideal and noisy conditions.

---

## **2. Objectives**

The challenge aims to:

1. **Reproduce Baseline Simulations** – Implement 1- and 2-layer Quantum Galton Boxes.
2. **Generalize to N Layers** – Build a scalable algorithm that generates circuits for any number of layers.
3. **Target Alternate Distributions** – Modify the quantum circuit to simulate:

   * **Exponential Distribution**
   * **Hadamard Quantum Walk**
4. **Noisy Hardware Optimization** – Use realistic noise models to optimize circuit depth and improve fidelity.
5. **Distribution Accuracy** – Compute statistical distances (e.g., KL Divergence, Total Variation Distance) between simulated and target distributions while accounting for stochastic uncertainties.

---

## **3. Theoretical Background**

### **3.1 Galton Box and Monte Carlo Analogy**

* **Classical Galton Box:** A ball drops through several layers of pegs, randomly bouncing left or right, forming a **binomial distribution** that approximates a Gaussian as layers increase.
* **Monte Carlo Relevance:** Such random sampling techniques are key to **particle transport models** and **PDE solutions** in high dimensions.

### **3.2 Quantum Galton Box**

A **quantum circuit** simulates this process by placing qubits in **superposition**, where each qubit represents a branching decision (left or right). The final measurement of all qubits reveals the distribution of outcomes.

* **Gaussian Distribution:** Achieved using **Hadamard gates** at each layer, which give equal probabilities for left/right paths, mimicking unbiased random walks.
* **Exponential Distribution:** Implemented by replacing Hadamards with **biased rotations** (`RY(θ)`), creating a non-uniform branching probability.
* **Hadamard Quantum Walk:** Alternating **Hadamard gates** and **controlled swaps** produce interference patterns characteristic of quantum walks.

### **3.3 Quantum Advantage**

* **Parallel Trajectory Evaluation:** Superposition allows evaluation of all possible paths simultaneously.
* **Interference Control:** Phase shifts can bias probabilities in ways difficult to achieve classically.
* **Potential Exponential Speed-Up:** Particularly relevant when extended to high-dimensional problems or integrated with QFT-based sampling.

---

## **4. Implementation Outline**

### **Step 1: Baseline (1 & 2 Layers)**

Recreate simple Galton Boards with a few qubits to verify correctness against classical distributions.

### **Step 2: Generalized N-Layer Circuit**

Develop a scalable function that dynamically builds circuits for any number of layers. Each layer corresponds to a qubit operation.

### **Step 3: Alternate Distributions**

* **Exponential:** Adjust rotation angles to bias outcomes toward one side.
* **Quantum Walk:** Implement alternating Hadamard and controlled-SWAP sequences.

### **Step 4: Noise Model Integration**

Run simulations using **Qiskit Aer** or any quantum hardware emulator with realistic noise profiles (e.g., `FakeJakarta`, `FakeManila`). Optimize for:

* Reduced gate depth.
* Measurement error mitigation.

### **Step 5: Accuracy Metrics**

Compare observed distributions to theoretical targets using:

* **Total Variation Distance (TVD):** Measures absolute difference in probabilities.
* **KL Divergence:** Quantifies information loss.
  Include uncertainty estimates by averaging across multiple runs (bootstrapping).

---

## **5. Results and Interpretation**

* **Gaussian Simulation:** Should approach the classical binomial/Gaussian distribution as the number of layers increases.
* **Exponential & Quantum Walk:** Display distinct skewed or interference-driven patterns.
* **Noise Impact:** Deeper circuits and more layers are more sensitive to noise; optimization strategies significantly improve fidelity.

Plots and tables summarizing distribution comparisons and statistical distances should be included in the final report.

---

## **6. Usage & Workflow**

1. **Run Ideal Simulations:** Generate and execute circuits on a noiseless simulator to validate distributions.
2. **Change Distributions:** Select between Gaussian, Exponential, and Quantum Walk modes.
3. **Enable Noise Models:** Test hardware-like behavior and compare with ideal results.
4. **Analyze Output:** Visualize histograms and compute distance metrics.

---

## **7. Future Directions**

* Extend to **multi-dimensional quantum Monte Carlo simulations**.
* Investigate **hybrid quantum-classical variance reduction techniques**.
* Explore **real hardware execution** on IBM Quantum or Xanadu devices for benchmarking.

---

## **8. References**

1. *Universal Statistical Simulator* – Original paper introducing quantum statistical simulations.
2. Qiskit & PennyLane documentation for quantum circuit construction and noise modeling.
3. Standard texts on Quantum Monte Carlo and Quantum Walks.

---

