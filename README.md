# Tabular Synthetic Data Generation Project

This repository contains the source code and the documentation of the Tabular Synthetic Data Generation Project for the Introduction to Data Security course on ELTE.

# Exploring the Motivations for Synthetic Tabular Data
Synthetic data generation has emerged as a critical solution for numerous challenges in data science and analytics, offering organizations innovative ways to overcome limitations they face with real-world data. While synthetic data can take many forms, tabular synthetic data—artificial data structured in rows and columns mimicking real databases—has become particularly valuable across industries.

Privacy concerns represent one of the most compelling reasons to use synthetic data. According to Osorio-Marulanda et al. (2024), synthetic data provides a powerful privacy-preserving mechanism that allows organizations to share and analyze sensitive information without risking exposure of personally identifiable information or protected health information. This is particularly crucial in sectors like healthcare, finance, and government, where data often contains highly sensitive personal information that cannot be shared in its original form.

It is a struggle sometimes to build robust models, when dealing with rare events or new product development scenarios. Figueira and Vaz (2022) highlight how synthetic data can effectively augment existing datasets or even create entirely new ones to support model training and testing. This capability proves particularly valuable in situations where collecting real-world data is expensive or time-consuming. It can help to build more reliable models and gain new insights.

Class imbalance represents a challenge in machine learning application. Pathare et al. (2023) demonstrate how synthetic data generation can address this problem by creating additional samples for minority classes, thereby improving overall model performance and reducing bias. In fields ranging from fraud detection to medical diagnostics, where positive cases may be extremely rare, the ability to generate realistic synthetic examples of these underrepresented classes can dramatically improve model training.

Beyond these primary motivations, synthetic data offers additional benefits that make it increasingly attractive. Galloni et al. (2020, 2023) discuss evaluation metrics that help ensure synthetic data maintains the utility of original data while providing sufficient privacy protection. These metrics help organizations quantify the trade-offs involved in synthetic data generation and select appropriate approaches based on their specific use case requirements. As the field continues to evolve, improved evaluation methodologies are making it easier for organizations to confirm that their synthetic data initiatives are delivering the intended benefits.

## Introducing basic concepts about the topic

### Tabular data
Tabular data, sometimes also called structured data, refers to a data format organized in a table, where data points are represented as rows and features or attributes as columns. In tabular data, each row corresponds to an individual sample or observation, and each column represents a distinct feature or variable that characterizes that sample. These features can be of different types, including continuous (numerical) values and categorical (qualitative) values. Categorical features might include binary variables, ordinal values, or high-cardinality categorical variables, which can take many distinct values (Shwartz-Ziv et al., 2022)

Tabular data is ubiquitous in a variety of fields, including medicine, finance, marketing, climate science, and many others, where relational databases are frequently employed. The most prominent characteristic of tabular data is its structured nature, making it easy to store, analyze, and process using machine learning and statistical methods. The relational database structure, where data is organized into tables with rows and columns, is particularly well-suited for tabular data. This makes it an essential form of data in industries that rely heavily on database-driven applications, such as healthcare, finance and commerce (Shwartz-Ziv et al., 2022).

Unlike homogeneous data types like images, audio, or text, which are often represented by a single type of feature, tabular data is heterogeneous (Shwartz-Ziv et al., 2022). This means it can consist of a variety of feature types, such as numerical, categorical, binary, and ordinal, which makes its analysis more complex but also more powerful. This complexity makes tabular data both challenging and rich for predictive modeling and machine learning applications. Tabular data is particularly important because it is often used in situations where data comes from diverse sources and needs to be integrated for analysis. For instance, in the field of finance, tabular data may represent historical stock prices, financial reports, and economic indicators, with each feature having a different type and meaning. Similarly, in climate science, tabular data can represent temperature, precipitation, and other variables over time, collected across different regions (Shwartz-Ziv et al., 2022).

The use of tabular data has a long history. Before the digital age, tabular data was one of the primary ways data was recorded and analyzed. Early statistical methods were applied to data organized in tabular form, and much of the development of machine learning methods has been built upon this structure. In fact, many of the traditional machine learning techniques still dominate when it comes to analyzing tabular data, such as decision trees, random forests, and gradient-boosted decision trees (GBDT), which are highly effective in handling the variety of data types found in tabular datasets (Borisov et al., 2022).

However, the development of deep learning and neural networks, which were originally designed for homogeneous data types like images or text, has posed challenges when applied to tabular data. Deep learning models, particularly neural networks, have made impressive strides in tasks such as image recognition, natural language processing, and audio analysis, but when applied to tabular data, they often face difficulties due to the lack of locality, mixed feature types, missing values, and limited prior knowledge of dataset structure [1]. Despite these challenges, research continues into improving deep learning models for tabular data, and there have been significant efforts to develop architectures specifically designed for this type of data [2].
As deep learning continues to evolve, new techniques are being developed to better handle tabular data, which remains a critical part of data-driven decision-making in many sectors [2].

### Synthetic Data
Synthetic data refers to data that is artificially generated rather than being collected from real-world events or measurements. This type of data is typically created using algorithms that simulate real-world scenarios, preserving the underlying statistical properties of the original data without using actual sensitive information. Synthetic data is commonly used in fields like machine learning, privacy protection, and data augmentation because it allows researchers and practitioners to generate large datasets without violating privacy concerns or having access to sufficient real-world data.
For example, in healthcare, synthetic data might be generated to simulate patient records without using real patient data. In this way, synthetic data can be used for training machine learning models, conducting research, or testing algorithms, while mitigating the risk of privacy breaches or data scarcity. Similarly, in the financial sector, synthetic datasets might be used to test trading algorithms without using proprietary or sensitive financial data.
There are several advantages to using synthetic data. One of the primary benefits is that it can be tailored to the needs of specific applications, such as generating rare events or specific conditions that may not be present in real-world data. Additionally, synthetic data can be used to supplement real-world data, especially when the available data is sparse or difficult to obtain. Furthermore, synthetic data generation can help avoid the limitations associated with data collection, such as biases, inaccuracies, or ethical concerns related to using real data.

## Synthetic Data Generation Algorithms
The process of generating synthetic data involves algorithms that model the underlying patterns and structures of real-world datasets. These algorithms typically fall into a few categories based on the approach they use:

1.	**Statistical Methods**: These methods rely on statistical models to generate synthetic data that mimics the distribution and relationships found in the original dataset. For example, a Gaussian distribution or other parametric models can be used to generate synthetic samples based on the mean and variance of the data. However, these methods might not capture complex dependencies between features in high-dimensional data.
   
2. **Generative Adversarial Networks (GANs)**: GANs are a class of deep learning models that have gained significant popularity for synthetic data generation. They consist of two neural networks—a generator and a discriminator—that work in tandem. The generator creates synthetic data samples, while the discriminator attempts to distinguish between real and synthetic data. Through this adversarial process, the generator improves over time, producing more realistic synthetic data. GANs have been successfully applied to generate images, text, and other types of data.
   
3.	**Variational Autoencoders (VAEs)**: VAEs are another deep learning-based method for generating synthetic data. A VAE learns a probabilistic representation of the input data and can generate new data samples by sampling from this learned distribution. VAEs are often used for generating synthetic data in complex domains like image and text generation.
   
4.	**Simulation-Based Approaches**: Some synthetic data generation methods rely on domain-specific simulations, where synthetic data is created by mimicking the physical, biological, or economic processes that govern the real-world phenomena being modeled. For instance, synthetic data for autonomous vehicles can be generated by simulating different driving scenarios in a virtual environment.
   
5.	**Rule-Based Generation**: In certain cases, synthetic data can be generated by applying a set of predefined rules or constraints to create data samples. These rules may be based on expert knowledge about the data or the domain of interest. Rule-based approaches are often simpler but can be effective in domains with well-understood relationships between features.

6.	**Data Augmentation**: Data augmentation techniques, such as adding noise or perturbations to existing data, can also be used to generate synthetic data. This is especially useful in machine learning tasks like image classification, where slight alterations to original data points (e.g., rotating images or changing colors) can help increase the size of a dataset and improve the robustness of models.
   
## Evaluation Metrics for Synthetic Data - Galloni
When generating synthetic data, it is important to assess how well it represents the original data, particularly when the synthetic data is used for machine learning or statistical analysis. Evaluation metrics help determine the quality of synthetic data by comparing it to the real data in terms of various characteristics, such as accuracy, diversity, and realism. One framework for evaluating synthetic data is Galloni's metrics, which provide a way to quantitatively measure how well synthetic data approximates real data in several dimensions.

1.	**Statistical Similarity**: This metric measures how closely the statistical properties of synthetic data match those of the original dataset. Common statistical measures include the mean, variance, and higher-order moments (such as skewness and kurtosis). Additionally, measures like the Kolmogorov-Smirnov test can be used to compare distributions of individual features.

2.	**Distributional Fidelity**: This metric evaluates how well the synthetic data preserves the joint distribution of multiple features in the dataset. Since synthetic data can sometimes fail to capture complex dependencies between features, this metric helps ensure that the relationships and correlations between features in the synthetic dataset align with those in the real-world data.

3.	**Diversity**: Synthetic data should exhibit sufficient diversity, meaning that it should not merely reproduce a narrow subset of the real data. Diversity is especially important when generating synthetic data for machine learning, as a lack of diversity can lead to overfitting or biased models. This metric assesses the spread of the synthetic data across the feature space, ensuring it is representative of the variability found in the real data.
   
4.	**Utility**: One of the most important metrics for evaluating synthetic data is how useful it is for downstream tasks such as machine learning. The synthetic data should perform similarly to real data when used for training models. Metrics such as model accuracy, precision, recall, and F1 score can be used to measure how well models trained on synthetic data generalize to real data.
   
5.	**Privacy Preservation**: In many applications, synthetic data is used to protect sensitive information. Therefore, an important metric is the ability of the synthetic data to maintain privacy by ensuring that individual records in the original dataset cannot be identified or reconstructed from the synthetic data. Techniques such as differential privacy are often used to evaluate how much information about individuals is retained in the synthetic data.
    
6.	**Visual Quality**: For image or visual data, evaluation can also include visual fidelity, assessing how realistic the generated images or video appear to human observers. This can be done using human ratings or more automated techniques, such as perceptual similarity metrics (e.g., Structural Similarity Index or SSIM).
    
In summary, synthetic data plays a critical role in a variety of applications, especially when real-world data is scarce, sensitive, or difficult to obtain. The generation of synthetic data can be achieved through various algorithms, each suited to different types of data and applications. Evaluating synthetic data is equally important, and metrics like those proposed by Galloni help ensure that the generated data maintains statistical, distributional, and utility characteristics similar to real data, while also addressing privacy concerns and preserving diversity.


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

## Real-World Applications of Tabular Synthetic Data

### Finance and Banking
Financial institutions leverage synthetic tabular data for numerous critical applications. They create realistic transaction datasets for fraud detection model training and test credit scoring algorithms without exposing sensitive customer data (Assefa, 2020). Additionally, these institutions develop and validate anti-money laundering systems using synthetic suspicious activity patterns, while also generating synthetic market data for algorithm trading strategy development and testing.

### Healthcare and Clinical Research
In healthcare settings, tabular synthetic data generation effectively addresses privacy concerns while enabling crucial research initiatives. Healthcare organizations generate synthetic electronic health records for medical research and education purposes, while creating synthetic patient cohorts for clinical trial simulation. As demonstrated by Chen et al. (2021), building realistic insurance claims data supports healthcare analytics without privacy risks. This approach particularly benefits rare disease research where real patient data is often limited.

### Retail and E-commerce
Retailers enhance their operations through synthetic tabular data in multiple ways. They create synthetic customer profiles for personalization algorithm development and generate realistic purchase histories to improve recommendation systems. According to Hernandez and Greenwald (2021), developing inventory management models with synthetic sales data provides significant advantages. Retailers also test pricing strategies using synthetic market response data to optimize revenue without risking actual market disruption.

## Ethical Considerations and Bias Mitigation in Tabular Data
Real-world tabular data often contains biases reflecting historical inequalities or flawed collection processes. These biases are particularly concerning in tabular contexts as they directly impact critical decisions in domains like lending, insurance, and healthcare. Implementing tabular synthetic data generation requires addressing these concerns through multiple approaches.

Pre-processing techniques for fairness include identifying and measuring bias across protected attributes such as gender, age, and race. Re-sampling or re-weighting training data ensures balanced demographic representation, while removing proxy variables that correlate with protected attributes but lack business criticality helps prevent bias propagation. Applying transformations that reduce discrimination while preserving utility completes this initial phase.

During model training, parameters can be adjusted to prioritize fairness through adding constraints to the generator's objective function. Implementing adversarial debiasing techniques allows discriminators to penalize biased synthetic records, while conditional generation ensures balanced subgroup representation. Regularizing the learning process prevents models from capturing discriminatory patterns in the original data.

After generation, verification and correction steps help ensure fairness through measuring statistical parity across protected groups and adjusting conditional distributions to enforce fairness metrics. Applying post-hoc corrections to problematic variables or records and verifying downstream model behavior across demographic groups completes a comprehensive approach to ethical synthetic data generation.

## Future Directions in Tabular Synthetic Data
As tabular synthetic data generation technologies continue to evolve, several specific trends are emerging:

- Advanced relationship modeling: New techniques will better capture complex relationships between variables, including non-linear dependencies, temporal patterns, and hierarchical structures that are common in real-world tabular data.
- Industry-specific generators: Development of specialized tabular data generators optimized for particular domains like healthcare claims, financial transactions, or retail purchase histories, with built-in domain constraints and validation rules.
- Regulatory clarity: As synthetic tabular data becomes more prevalent in regulated industries, we can expect specific regulatory guidance on its use for compliance, testing, and analytics purposes.
- Synthetic data marketplaces: Emergence of platforms where organizations can access high-quality, privacy-preserving synthetic datasets representing industry-specific tabular data structures for model development and benchmarking.
- Integrated evaluation frameworks: Development of standardized metrics and tools to comprehensively assess synthetic tabular data quality across multiple dimensions: statistical fidelity, privacy protection, fairness guarantees, and utility for specific downstream tasks.

## Conclusion
Tabular synthetic data generation represents a transformative technology with significant potential to address data privacy, availability, and bias challenges across numerous industries. While implementation challenges specific to tabular data exist—including mixed data types, complex relationships between variables, and quality evaluation—strategies such as specialized platforms, hybrid generation approaches, and comprehensive fairness frameworks can facilitate successful adoption.

As these technologies mature, organizations that effectively deploy tabular synthetic data will gain significant competitive advantages. They'll be able to accelerate development cycles, enhance data science capabilities, and unlock insights that would otherwise be constrained by data privacy concerns, particularly in highly regulated industries like finance and healthcare.

For optimal results, organizations should approach tabular synthetic data generation as a strategic capability requiring both technical expertise and domain knowledge. By maintaining focus on data quality, privacy preservation, and bias mitigation, synthetic tabular data can become a valuable asset in the modern data ecosystem, enabling innovation while respecting ethical and regulatory boundaries.


## References

Shwartz-Ziv, R., & Armon, A. (2022). Tabular data: Deep learning is not all you need. Information Fusion, 81, 84-90.

Borisov, V., Leemann, T., Seßler, K., Haug, J., Pawelczyk, M., & Kasneci, G. (2022). Deep neural networks and tabular data: A survey. IEEE transactions on neural networks and learning systems.

Figueira, A., & Vaz, B. (2022). Survey on synthetic data generation, evaluation methods and GANs. Mathematics, 10(15), 2733.

Endres, M., Mannarapotta Venugopal, A., & Tran, T. S. (2022, August). Synthetic data generation: A comparative study. In Proceedings of the 26th international database engineered applications symposium (pp. 94-102).

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

Assefa, S. (2020). Generating synthetic data in finance: opportunities, challenges and pitfalls. Challenges and Pitfalls (July 22, 2020)

Chen, R. J., Lu, M. Y., Chen, T. Y., Williamson, D. F., & Mahmood, F. (2021). Synthetic data in machine learning for medicine and healthcare. Nature Biomedical Engineering.

The article writes about the growing role of synthetic data in healthcare artificial intelligence systems, highlighting both opportunities and challenges. Synthetic data, generated through AI models like **Generative Adversarial Networks (GANs)**, offers solutions to healthcare's lack of valuable data problems by creating realistic medical images, electronic health records, and disease trajectories that can improve algorithm performance and protect patient privacy. However, the authors raise important concerns about potential vulnerabilities, including information leakage risks, quality assessment difficulties, and regulatory uncertainties around synthetic data implementation in medical AI systems. They advocate for developing robust evaluation metrics, grounding algorithms in accurate physical models, implementing regulatory "stress tests," and maintaining human oversight to ensure synthetic data enhances rather than compromises healthcare.

Hernandez, D., & Greenwald, H. (2021). Synthetic data generation for retail forecasting: Challenges and opportunities. Retail AI Lab Technical Report.
 
Li, S. C., Jiang, X# Tabular Synthetic Data Generation: Applications, Techniques and Implementation

Patki, N., Wedge, R., & Veeramachaneni, K. (2016). The Synthetic Data Vault: Generative modeling for relational databases. 2016 IEEE International Conference on Data Science and Advanced Analytics (DSAA), 399-410.

The **Synthetic Data Vault** (SDV) is a system that automatically creates synthetic relational database data while preserving both statistical properties and structural relationships between tables. Developed to enable data science work without sharing sensitive information, SDV uses **Recursive Conditional Parameter Aggregation** to model parent-child relationships between tables. It uses Gaussian Copula for modeling distributions and covariances within tables. The system handles various data types including numerical values, categorical data, datetime values, and missing entries through specialized preprocessing techniques.
Research validation involving 34 data scientists across five different datasets demonstrated that synthetic data generated by SDV can effectively replace original data for data science tasks. The study found no significant difference in predictive accuracy between features developed using real versus synthetic data. The data scientists who utilized synthetic data with these machine learning models, found that synthetic data can perform the same or better than original data in over 70% of comparisons. This suggests that SDV offers a viable effective for organizations seeking to expand their data science capabilities while addressing privacy concerns related to sensitive information.
