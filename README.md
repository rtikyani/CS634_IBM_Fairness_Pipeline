# CS634_IBM_Fairness_Pipeline
Team 3	
ba327@njit.edu - Benjamin Amoah	
ec396@njit.edu - Eric Cho
rmt29@njit.edu - Rohit Tikyani
Detecting and mitigating age bias on credit decisions

Summary of AI Fairness 360

As machine learning models become more widely used in domains such as mortgage lending, hiring and prison sentencing, fairness and bias are becoming central foci of the algorithms used in these models. To address issues related to fairness, AI Fairness 360 (AIF360) was developed to help better understand fairness metrics and mitigation techniques.

Favorable label: value corresponds to an advantageous outcome protected attribute: partitions a population into groups with different amounts of benefits, ie) race, gender, caste, religion privileged: group that has historically been at a systematic advantage group fairness: groups defined by protected attributes receive similar treatments or outcomes individual fairness: similar individuals receiving similar treatments or outcomes bias: systematic error that gives privileged groups advantages and vice versa for unprivileged groups fairness metric: quantification of unwanted bias in training data or models bias mitigation algorithm: used to reduce unwanted bias in training data or models

Many other toolkits exist, although they are not as comprehensive as AIF360 in that AIF 360 provides bisa metrics, mitigation algorithms, bias metric explanations, and industrial usability.

AIF 360 is an end-to-end workflow that allows users to transform raw data to a model, adding in functionality throughout. The general pipeline for bias mitigation works as follows: outputs are new datasets sharing the same protected attributes as other datasets, transitions are transformations that modify features and/or labels, and trapezoids are learned models. One can reach a fair prediction through one of three bias mitigation algorithms: fair pre-processing, fair in-processing, fair post-processing. The three methods each have their nuances, so one must decide which they would like to use based on its respective features.

The Dataset class handles all forms of data (like training data and testing data), and organizes the data by associating each instance of data with protected attributes. It also contains subclasses that are more specific and further organize the data. These classes serve to provide a common structure for the entire pipeline to use and also allow different utility functions and capabilities (from Python) to be applied to the data.

The Metrics class and its subclasses calculate fairness metrics and check for biases in datasets and models. Because fairness can be defined in many ways and is dependent on the context, many different fairness metrics are included in the toolkit, which gives the user the option to select the best metrics given the data.

The Explainer class is intended to be associated with the Metrics class. It is used to provide further insights on computed fairness metrics. The Explainer class stresses the need for explanations. Future methodologies may include actionable recourse analysis, counterfactual fairness, and fine-grained localization
