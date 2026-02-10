# PU-Mat: Positive-Unlabeled Learning for Materials Discovery

PU-Mat is a specialized machine learning framework designed to identify "hit" candidates (stable/functional materials) from vast, unlabeled chemical spaces. Unlike standard binary classification, this tool addresses the "missing negative" problem inherent in experimental materials science and drug discovery.

Scientific MotivationIn materials discovery, experimental databases (like ICSD or Materials Project) primarily contain "successful" or "stable" entries (Positive labels). However, the "failed" or "unstable" experiments are rarely reported, leaving a massive pool of Unlabeled data.Standard classifiers treat unlabeled data as negatives, which introduces significant bias. PU-Mat implements a "Two-Step" or "Bagging" PU Learning approach to recover the true distribution of potential materials.

Key FeaturesBias Correction: Adjusts for the fact that unlabeled data contains hidden positives.Integration with RDKit: Seamlessly handles SMILES strings and molecular descriptors.Physics-Informed Descriptors: Support for structural descriptors derived from DFT and MD simulations.Bagging PU Classifier: Robust implementation using an ensemble of weak learners to estimate the probability of a sample being positive.

The Mathematical Core 
The framework minimizes the risk functional for PU learning. Given a label $y \in \{1, 0\}$, where only $y=1$ is observed, we estimate the decision boundary by weighting the loss:$$\hat{R}_{pu}(f) = \pi_p \hat{R}_p^+(f) + \max\{0, \hat{R}_u(f) - \pi_p \hat{R}_p^-(f)\}$$Where:$\pi_p$ is the class prior (estimated proportion of positives in the unlabeled set).$\hat{R}_p^+$ is the empirical risk on labeled positives.$\hat{R}_u$ is the risk on the unlabeled set.
