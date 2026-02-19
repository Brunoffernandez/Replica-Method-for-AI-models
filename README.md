# Replica Method Applied to a Neuronal System

## Overview
This repository contains the writeup and simulation code for the MMT project **"Replica method applied to a neuronal system"**. The project explores the statistical mechanics of neural networks, specifically focusing on the **Hopfield Network** and the **Continuous Spherical Perceptron**. It aims to validate theoretical predictions derived from the Gardner analysis and the Replica trick regarding phase transitions and critical storage capacities.

## Repository Contents

### 1. `Replica_theory_MMT (1).pdf`
The main theoretical write-up of the project. It provides in-depth mathematical derivations and discusses the experimental results. The structure includes:
* **Hopfield Network:** Theoretical foundations and experimental validations.
* **Perceptron:** Theoretical analysis and experimental results.
* **Appendix:** Detailed mathematical proofs, including the Replica Trick Proof, derivations of Theorem 1 and Theorem 2, calculus of integrals, the "flip" trick, and the Symmetry Ansatz for both the Hopfield network and the perceptron.

### 2. `Perceptron.ipynb`
A Jupyter Notebook simulating the critical storage capacity of a continuous Spherical Perceptron.
* **Goal:** Validate theoretical predictions from the Gardner analysis regarding the phase transition between solvable and unsolvable memory regimes.
* **Methodology:** * **Data Generation:** Creates $P$ random input patterns drawn from a standard normal distribution and assigns binary labels ($y \in \{-1, 1\}$).
  * **Training:** Uses `LogisticRegression` with a high inverse regularization parameter ($C=100$) to approximate a Hard Margin classifier, forcing the algorithm to find a constraint-satisfying solution.
  * **Validation:** Normalizes the learned weights to lie on a unit sphere ($||w||=1$) and checks the Gardner Stability Condition: $y^\mu \frac{w \cdot x^\mu}{\sqrt{N}} \ge \kappa$.
  * **Phase Space Exploration:** Repeats the experiment across a grid of memory loads ($\alpha = P/N$) and confidence margins ($\kappa$) to map out the phase diagram and identify the critical capacity $\alpha_c(\kappa)$.

### 3. `Replica_method.ipynb`
A Jupyter Notebook simulating the dynamics, recall robustness, and storage capacity of a Hopfield Network.
* **Methodology:**
  * **Network Setup:** Generates random patterns and constructs the weight matrix using the standard Hebbian learning rule (ignoring self-inputs).
  * **Dynamics:** Simulates asynchronous network dynamics over a specified number of time steps.
  * **Evaluation:** Evaluates pattern recall success using both Hamming distance and overlap criteria (e.g., checking if the overlap $m(t) \ge \theta$, with thresholds like $0.95$ or $0.98$).
  * **Noise Testing:** Introduces noise by randomly flipping a fraction of bits (ratio) in the initial state to test the network's recall robustness.
  * **Capacity Measurement:** Measures the network capacity by mapping the recall performance as a function of the memory load ($\alpha = P/N$) simulating different numbers of patterns ($P$) for a fixed number of neurons ($N$).

## Requirements
To run the Jupyter Notebooks locally, you will need **Python 3** and the following libraries installed:
* `numpy`
* `matplotlib`
* `scikit-learn`
* `scipy`

You can install the dependencies using pip:
```bash
pip install numpy matplotlib scikit-learn scipy
