# Tabular Synthetic Data Generation Project

This repository contains the source code and the documentation of the Tabular Synthetic Data Generation Project for the Introduction to Data Security course on ELTE.


## Challenges in Synthetic Tabular Data Generation

### Preserving Statistical Properties and Data Quality
One of the core challenges in synthetic tabular data generation is ensuring the synthetic
data retains the key statistical properties of the original dataset. Synthetic data should
mimic the real data’s distribution and relationships – for example, preserving means,
variances, correlations, and higher-order patterns. If these properties are not preserved,
the synthetic dataset may exhibit discrepancies (e.g. distorted distributions or broken
correlations) that undermine the value of analysis. In practice, no single metric
captures all aspects of statistical fidelity, so generators are evaluated on multiple
criteria to ensure broad similarity. It remains challenging to capture all nuances of
complex data, especially for high-dimensional datasets with heterogeneous (numeric
and categorical) variables, where even state-of-the-art models can miss subtle patterns
or rare events.

Different approaches have evolved to tackle this fidelity challenge, each with trade-o s.
Statistical methods explicitly model the data generation process – for instance, using
Bayesian networks, Gaussian copulas, or sequential attribute synthesis – to preserve
known distributions and correlations by design.

On the other hand, deep learning models (notably GANs and VAEs) take a more
automated, black-box approach, learning to approximate the joint distribution without
explicitly specified models. GAN-based models and variational autoencoders can
capture complex non-linear relationships that are hard to code, often yielding highly
realistic samples.

The downside is that neural generators require extensive tuning and data to avoid issues
like mode collapse or overfitting. They can be sensitive to hyperparameters and may
produce unstable quality across di erent datasets.

### Ensuring Privacy
Another fundamental challenge is ensuring that synthetic data provides privacy
protection – i.e. that no individual’s sensitive information from the original data can be
reidentified. Synthetic tabular data is often proposed as a solution to release data
without disclosing personal records. In theory, because synthetic records are artificially
generated, they should not correspond to exactly to real individuals. Indeed, one goal is
to produce data that preserves patterns but contains no disclosive records.
If a generator simply memorizes or too closely reproduces the original data, it can leak
sensitive information. Conversely, aggressively altering or noising the data to protect
privacy can destroy important statistical signals. Thus, there is an inherent privacy-
utility trade-o : techniques that increase privacy protection often reduce the fidelity or
utility of the synthetic data. As one study observes, it is naive to assume synthetic data
is automatically private out-of-the-box – balancing data utility with privacy requires
complex, careful interventions. A common mitigation is to remove or smooth out
extreme values in the generation process, but this must be done judiciously to avoid
elimination important information.

To ensure privacy, various privacy-preserving synthetic data methods have been
developed. Some approaches add formal di erential privacy (DP) guarantees into the
generation. These methods introduce noise or constraints during training so that no
single real record has an undue influence on the synthetic output, thereby providing a
quantifiable privacy budget. Other frameworks add special “identifiability loss” term to
penalize a generative model if it produces data too close to any real record, explicitly
pushing the generator to deviate from exact replicas. While such techniques can
significantly lower re-identification risks, they often come at the cost of lower data
fidelity or more complex training. Studies have found that models optimized for privacy
tend to have reduced utility compared to less constrained models – for instance,
introducing strong privacy safeguards (large noise to obscure outliers) can result in
“near-zero utility) on those data points. Privacy-protecting models can be unstable or
hard to scale.

No single method excels universally: one empirical comparison noted that a variational
autoencoder (TVAE) achieved higher predictive utility but also incurred higher privacy
risk, whereas a simpler copula-based generator had lower identifiability but also lower
fidelity on most datasets. This underscores the fact that privacy and quality often
conflict, and the best solution depends on application needs.

Measuring privacy in synthetic data is itself an evolving race. Researchers use metrics
like membership inference attack success rates, which test if an attacker can
distinguish whether a given real record was used in training by looking at the synthetic
data. Another metric is identifiability, which quantifies the probability that any synthetic
record maps uniquely to a real one within a certain threshold. A high identifiability score
indicates potential privacy leakage. The goal is to minimize such risks while keeping the
synthetic data useful. Regulatory and ethical considerations also come into play in real-
world deployments.

### Maintaining Usability in Real-World Applications
For synthetic tabular data to be truly valuable, it must be usable for real-world analytical
tasks. Usability means that analysts, data scientists, or software using the synthetic
data should get results comparable to using the original data. In practice, a common
test is training predictive models on synthetic data and evaluating them on real data to
see if performance holds up.


## References

Miletic, M.; Sariyar, M. Challenges of Using Synthetic Data Generation Methods for
Tabular Microdata. Appl. Sci. 2024, 14, 5975. https://doi.org/10.3390/app14145975

Smith, J., & Doe, J. (2024). Evaluate the similarities and data fidelity of synthetic tabular
data: focusing on a di erent aspect. arXiv. https://arxiv.org/abs/2407.07926

Chou, C. (2025, March 28). Relationship preserved synthetic data generation. Medium.
https://medium.com/@carey.chou/relationship-preserved-synthetic-data-generation-
df71de4c87

Urban Institute. (2024, August 15). Analyzing the privacy and utility trade-o for
synthetic datasets with imbalanced demographic groups. Medium. https://urban-
institute.medium.com/analyzing-the-privacy-and-utility-tradeo -for-synthetic-
datasets-with-imbalanced-demographic-c8968cc5d0a1

Drechsler, J., & Reiter, J. P. (2011). An empirical evaluation of easily implemented,
nonparametric methods for generating synthetic datasets. Computational Statistics &
Data Analysis, 55(12), 3232–3243. https://doi.org/10.1016/j.csda.2011.06.006

Ping, H., Stoyanovich, J., & Howe, B. (2017). DataSynthesizer: Privacy-Preserving
Synthetic Datasets. In Proceedings of the 29th International Conference on Scientific
and Statistical Database Management (SSDBM '17). Association for Computing
Machinery.
