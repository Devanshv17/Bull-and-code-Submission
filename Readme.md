# Alpha Strategy: Trend Detection and Trade Strategy Builder

## Overview
This project builds and evaluates a trading strategy using historical price data and a Long Short-Term Memory (LSTM) model. The model is trained on a dataset consisting of historical market data and is used to predict future price movements to generate buy or sell signals. The strategy's performance is evaluated using the Sharpe Ratio.

## Code Structure

The code is divided into four main sections:

1. **Dataset Download and Preparation**
   - The dataset is downloaded from Google Drive using the `gdown` command.
   - Data from multiple CSV files (representing different instruments) is loaded into a combined DataFrame.
   - The 'Volume' column is cleaned, and missing values are handled.
   - Features are scaled using `MinMaxScaler`.

2. **Model Creation and Training**
   - The LSTM model is built and trained on the entire dataset.
   - The data is split into features and target variables. The target variable is the "% Change" column, which the model will predict.
   - The model is a Sequential Keras model with two LSTM layers and dropout for regularization.
   - The model is trained on the data, and after training, it is saved as a `.h5` file.

3. **Model Testing**
   - After the model is trained, it can be tested on new data.
   - A test folder (folder path specified) is loaded in the same way as the training data.
   - The model predicts the "% Change" for the test data.
   - A backtest of the strategy is performed, where buy/sell signals are generated based on predicted percentage changes.
   - The performance is evaluated using the Sharpe Ratio, and cumulative returns are plotted.

4. **Testing on New Data**
   - A folder containing new test data (in CSV format) is specified.
   - The test data is processed in the same way as the training data.
   - Predictions are made using the trained model, and the strategy's performance is evaluated and plotted.
   - The user needs to update the path to their new test folder in the code, and the script will process the data and perform predictions.

## How to Use the Code

### 1. Preparing the Dataset
- First, ensure that the dataset is downloaded by running the command:
  ```bash
  !gdown --folder <id>(from google drive i.e. https://drive.google.com/drive/folders/<id>  )
