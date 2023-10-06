Causal Analysis of Time Series for Anomaly Detection in SWAT Dataset

The code is designed to conduct a causal discovery analysis on time series data using the PCMCI algorithm with Tigramite library in python. The purpose of the analysis is to identify and compare the causal relationships within two datasets, one representing "normal" conditions and the other representing "attack" conditions and carry on an anomaly detection for identify the anomalies in the attack dataset. The dataset we take in consideration is the SWAT dataset: https://itrust.sutd.edu.sg/itrust-labs_datasets/dataset_info/

Here's an overview of how the code works:

1. **Import and Preprocessing:** The code starts by defining a function, `read_preprocess_data`, to import and preprocess data. This function reads a CSV file, selects a subset of the data, removes near-constant and entirely `NaN` columns, and sets the timestamp as the index. We define the function we will use in the code and import the libraries that we need and we also set the Constants variables.

2. **Feature Importance:** In this section we execute an optional feature importance for speeding up the code by selecting before the analysis the variables (sensors) that are more significant

3. **Causal Discovery with PCMCI:** In this section we perform the causal analyis. The `run_pcmci` function runs the PCMCI algorithm on the preprocessed data (NORMAL Dataset) and prints out the time it took to run the process. The `plot_and_extract_links` function creates a visual representation of the causal links discovered by PCMCI and extracts these links into pandas dataframes. We merge the links together and we plot the correlations values in the normal dataset

3. **Anomaly Detection and Alarms logging**: In this section we launch the algorithm on the attack dateset using a rolling windows and we detect the anomalies printing the alarms once we cross a threshold (`CHANGE_LINK_CORRELATION`).

4. **Ground Truth confrontation and score printing:** we confront the code with the ground truth and we print the score for understanding the analyisis

5. **Printing Anomalies and graphs**: in the finaly section we print the detected anomalies and the graphs releated to them for figuring out which sensors where involved in the anomalies and act accordingly by taking appropriate measures
