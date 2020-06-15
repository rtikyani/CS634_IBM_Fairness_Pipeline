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

The Explainer class is intended to be associated with the Metrics class.  It is used to provide further insights on computed fairness metrics.  The Explainer class stresses the need for explanations.  TextExplainer is a subclass that returns plain string text with a numeric value. This can be invoked for both privileged and unprivileged instances by passing arguments.  
 
Bias Mitigation algorithms attempt to improve the fairness metrics by modifying the training data, learning algorithm, or predictions.  The categories are based on the location where the algorithms can intervene in a complete machine learning pipeline.  These algorithms are pre-processing algorithms, in-processing algorithms, and post-processing algorithms. 
 
Maintaining Code Quality is critical for an evolving open source system.  AIF360 is directly integrated with Travis CI which invokes pytest to run unit tests.  Pull requests trigger the tests.  Results of the test are made available to the reviewer of the request to ensure introductions to the code base do not break the code.  Unit Tests cases ensure classes and functions defined in the different libraries do not break the flow of the pipeline and are functionally correct.  A test suite was developed to compute the metrics. The repository has two types of test: unit tests and integration tests.  The former tests individual helper functions.  The latter test a complete flow of bias mitigation algorithms in the Juptyer notebook. 
 
Evaluation of algorithm fairness cannot be captured in a one-size-fits-all solution. The goals of evaluation are to demonstrating the capabilities of the toolkit in terms of the various fairness metrics and bias mitigation algorithms and to show how a user can understand the behavior of various metrics and bias mitigation algorithms on her dataset and make appropriate choices according to needs. 
The dataset is randomly divided into training (50%), validation(20%), and test partitions (30%).  Each point consists of a mean and spread ± 1 Standard Deviation using 25 random splits for random forest classifier, number of trees are set to 100 and minimum samples at a leaf node to be 20.  
 
The Web Application is designed to provide useful information for diverse consumers, providing utility for business users, new developers, and more advanced developers. For business users, the interactive demonstration of the toolkit's capabilities does not require any programming knowledge.  For new developers, the resources available provide multiple ways to enhance their current level of understanding into the details of the code.  For more advanced developers, detailed documentation and code are easily accessible.
 
On the back-end, Python's Flask framework is used for building the service and a REST API is exposed to generate a bias report based on input parameters from the user.  
With those inputs, the back end runs a series of steps:
1.  Splits the dataset into the three sets: Training, Development, and Validation.
2.  Trains a logistic regression classifier on the training set.  
3.  Runs the bias-checking metrics on the classifier against the test dataset.
4.  If a mitigation algorithm is chosen, it runs the mitigation algorithm with the appropriate pipeline.  
 
The result is then cached so that if the exact same inputs are provided, the result can be directly be retrieved from the cache and no additional computation is needed. 

