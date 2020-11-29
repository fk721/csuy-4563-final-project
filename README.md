# final-project

This folder is divided into three folders:

- **csv_files**
  - Contains the original and preprocessed data
- **notebooks**
  - Contains four Jupyter notebooks
- **figures**
  - Contains the resulting diagrams generated from the notebooks

### csv_files

#### `Fake.csv` and `True.csv`

- These files are the original CSV files taken from the Kaggle dataset

#### `cleaned_text.csv`

- This file concatenates `Fake.csv` and `True.csv` together
- It also cleans the article text by converting an article's text to lowercase, and removes any *stopwords*

#### `count_vectorized_text.csv`

- Contains the feature vector for each entry in `cleaned_text.csv` 
  - The feature vector corresponds to the 15 most frequent words used (using `CountVectorizer` from `Sklearn`)

#### `inverse_document_freq.csv`

- Similar to `count_vectorized_text.csv`, except it contains the term frequency-inverse document frequency values (Tf-idf) rather than the actual count 
  - Using `TfidVectorizer` from `Sklearn`

### notebooks

#### `preprocessing.ipynb`

- Loads the original CSVs (`Fake.csv` and `True.csv`) and performs some semi-supervised learning
- Generates `count_vectorized_text.csv` and `inverse_document_freq.csv`

#### `logistic-regression.ipynb`

- Playing around with some logistic regression models

#### `svm.ipynb`

- Playing around with some SVM models

#### `neural-network.ipynb`

- Playing around with some neural network models

### Other Notes

- I used external libraries from Sklearn for each of the supervised learning models (logistic regression, SVM, neural networks)
  - Writing these models from scratch was not difficult
  - However, when training my model, it just took *hours* to train (when performing the gradient ascent/descent)
    - Maybe it's because I had more than 40,000 examples with 15 features per example? 
  - As a result, I replaced these written models with their respective `Sklearn` counterpart (`sklearn.linear_model.LogisticRegression`, `sklearn.svm.SVC`, `sklearn.neural_network.MLPClassifier`) in order to save *a lot* of time
    - I hope this is okay