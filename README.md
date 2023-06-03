# Machine-Learning-Model-to-predict-attack-in-IOT-Devices
# IoT Attack Prediction

This repository contains the code and data for building a machine learning model to predict SHA, DFA, SFA, SYA, and VNA attacks on IoT devices. The model is trained using raw data obtained from simulations conducted with the Contiki Cooja IoT simulator.

## Step 1: Raw Data

The raw data used for training the model was obtained through the following steps:

1. Install the Contiki Cooja IoT simulator on a computer with the Ubuntu 18.04 operating system.
2. Install the RPL Attacks Framework created by D'Hondt and others on another computer with Ubuntu 18.04.
3. Simulate IoT devices using Contiki Cooja, creating both vulnerable and normal nodes.
4. Capture raw data during the simulations and convert it into a CSV file format.

Five different datasets were created from the simulation using Contiki Cooja.

## Python Codes for Data Preprocessing

To prepare the raw data for machine learning, the following steps were performed:

1. The CSV files containing the raw data were analyzed. Each column in the CSV files represents the following information: No, Time, Source, Destination, Protocol Length, and Info.
2. Since the raw data obtained from simulations with weak nodes is different from the data obtained from simulations with normal motes, a preprocessing step was required to detect these anomalies.
3. The raw data was divided into 1-second frames, and within each frame, various values were calculated to create a new dataset. These calculated values include Source Mote, Destination Mote, Packet Count, Source Mote Ratio, Destination Mote Ratio, Source Mote Duration, Destination Mote Duration, Total Packet Duration, Total Packet Length, Source Packet Ratio, Destination Packet Ratio, DIO Message Count, DIS Message Count, DAO Message Count, Other Message Count, and Label.
4. The Label column was assigned values as follows: 1 for SHA, 2 for DFA, 3 for SFA, 4 for SYA, and 5 for VNA.

## Combining All Files

The Jupyter Notebook file `Combining_all_files.ipynb` contains the Python code to combine all the separate CSV files into a single dataset for further processing.

## Building the Model

To build the machine learning model, the following steps were performed:

1. Initially, without converting the raw data into meaningful features, the accuracy was observed to be around 30% to 35%.
2. Preprocessing steps were applied to convert the raw data into meaningful features, resulting in an improved accuracy of around 80%.
3. Feature engineering techniques were applied, including handling zero-division errors, filling null values, removing duplicates, checking attribute correlations, and determining feature importance rankings.
4. Several experiments were conducted by dropping columns and combining columns, but the efficiency did not improve significantly.
5. The final accuracy achieved after feature engineering was 87%.
6. Hyperparameter tuning was performed to optimize the model's performance.
7. Different models, including Logistic Regression, K-Nearest Neighbors (KNN), Decision Tree, and Artificial Neural Network (ANN), were evaluated. The Random Forest Classification model yielded the highest accuracy of 91.59%.

Feel free to explore the code and data provided in this repository to understand the process and replicate the results.
