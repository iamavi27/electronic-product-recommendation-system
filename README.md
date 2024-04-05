
# Electronics Recommendation System

## Overview

Welcome to the Electronics Recommendation System project! This system provides personalized recommendations for electronic products based on user preferences. It is built using a content-based filtering approach, leveraging a dataset from Kaggle.

## Features

-Personalized recommendations for electronic products.
-Utilizes machine learning techniques to understand user preferences.
-Easy-to-use Python script for obtaining recommendations.

## Getting Started

### Prerequisites

Ensure you have the following installed:

- Python (version >= 3.6)
- Required Python packages: Streamlit

### Installation

Clone the repository:

```bash
git clone https://github.com/iamavi27/electronics-recommendation-system.git
cd electronics-recommendation-system
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

### Usage

Run the recommendation system:

```python
from helper.recommender_system import recommender,matrix_display

```

Load the pickled files:

```python
import pickle
import streamlit as st

# Load pickled files
product_details = pkl.load(open('Product-details.pkl', 'rb'))
similarity_metrix = pkl.load(open('top10 Similar Products.pkl', 'rb'))
# Load product details
try:
    product_details = pd.read_pickle('Product-details.pkl')
except Exception as e:
    st.error(f"Error occurred while loading 'Product-details.pkl': {e}")
    product_details = pd.DataFrame()  # Provide an empty DataFrame in case of error

# Load similarity matrix
try:
    similarity_matrix = pkl.load(open('top10 Similar Products.pkl', 'rb'))
except Exception as e:
    st.error(f"Error occurred while loading 'top10 Similar Products.pkl': {e}")
    similarity_matrix = None  # Set to None in case of error

# Load top products index with error handling
try:
    top_products_index = pd.read_pickle('top100_product.pkl')
except Exception as e:
    st.error(f"Error occurred while loading 'top100_product.pkl': {e}")
    top_products_index = pd.DataFrame()  # Provide an empty DataFrame in case of error

# Create a recommender instance
product, details = st.columns([0.7, 0.3])
selected_product_index = product_details[product_details['name'] == selected_option].index[0]
recommended_ids = recommender(selected_product_index, similarity_metrix)
```

## Dataset

The dataset used for training and testing the recommendation system is available on Kaggle. You can find it [here](https://www.kaggle.com/datasets/lokeshparab/amazon-products-dataset).

## Model

The recommendation system uses a content-based filtering approach, analyzing product features to suggest similar items. The model is trained on the provided dataset to understand user preferences and generate personalized recommendations.

## Contributing

If you'd like to contribute to this project, please follow the [Contributing Guidelines](CONTRIBUTING.md).

## Issues

If you encounter any issues or have suggestions, please [open an issue](https://github.com/iamavi27/electronics-recommendation-system/issues).

## Acknowledgments

- Thanks to Kaggle for providing the dataset.

