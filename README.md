# Fibe-Hack the Vibe!2.0 ML Challenge
 The Ultimate AI Challenge with Fibe: Hack the Vibe! 2.0. This challenge invites participants to leverage the power of AI by developing innovative models using a comprehensive dataset of news articles. With over 870,000 samples available, you will address the complexities of text classification and contribute to the advancement of AI technologies.

# Solution
### (1) Source.ipynb file:
    * Data Loading: The train.csv file is loaded into a Pandas DataFrame using the latin1 encoding.
    * Data Preprocessing:
        - Non-UTF8 characters are removed from the "text" column in each row.
        - Rows without text values are removed.
        - Outliers in the target column with a value count less than 10 are removed.
        - A DataFrame train_1 is created containing 18,967 samples of each target.
        - Unwanted patterns are removed from the text data using regular expressions.
    * Target Mapping: Unique target values are mapped to integers, and a dictionary is created.
    * Tokenizer and Model:
        - The "AutoTokenizer" is used to tokenize the input text.
        - A pre-trained "BertForSequenceClassification" model is used.
        - The model is configured to produce a confidence matrix for 26 classes.
    * Model Configuration:
        - model.id2labels is used to provide the model with the mapping between label IDs and label names.
        - model.labels2id is used to provide the model with the mapping between label names and label IDs.
    * Data Split: The train data is split into train, validation, and test sets.
    * Data Conversion: The DataFrames are converted to lists.
    * Tokenizer:  The input text is split into individual tokens using the tokenizer.
    * DataLoader Class: Takes in the encoded data and labels as input and returns a dictionary containing the input IDs, attention masks, and labels.
    * Data Loaders: The data loaders for the training, validation, and testing sets are created using the DataLoader class.
    * Metrics Computation: A function compute_metrics is defined to calculate accuracy, F1-score, precision, and recall.
    * Training Arguments: TrainingArguments for setting args for trainer.
    * Model Training: The model is trained using the trainer.
    * Model Evaluation: The model's performance is evaluated on the train, validation, and test data using the q function.
    * Model Storage: The trained model and tokenizer are stored on a desired path.

### (2) Prediction.ipynb file:
    * Data Loading: The test.csv file is loaded into a Pandas DataFrame using the latin1
    * Data Preprocessing:
        - Non-UTF8 characters are removed from the "text" column in each row.
        - Rows without "index" values are removed.
        - Unwanted patterns are removed from the text data using regular expressions.
        - Two dataframes A containing text column and B containing Index column are made, A is converted to list for prediction.
    * Target Mapping: Integers are mapped to target values, and a dictionary is created.
    * The GPU is set to use CUDA and memory growth is set to 90%
    * Transformers pipeline is used for predicting target values  from the text in "A" list.
    * Predicted confidence matrix is converted to type tensor, then iterating over these tensor we store maximum confidence value's index in "max_index", pred is appended with the corresponding target value from the dictionary.
    * This pred  list is converted to a dataframe and dataframe "B["Index"]" is assigned to this dataframe and stored in a csv file.