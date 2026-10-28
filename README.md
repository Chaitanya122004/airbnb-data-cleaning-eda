# Airbnb Data Cleaning and Exploratory Data Analysis

## Project Overview

This project focuses on cleaning and exploring the New York City Airbnb Open Data dataset using Python. The goal is to assess data quality, investigate listing prices, understand accommodation types, and identify patterns across neighbourhoods.

## Dataset

- **Source:** [New York City Airbnb Open Data — Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)
- **Records:** 48,895 listings
- **Features:** 16 columns
- **Unique hosts:** 37,457
- **Neighbourhood groups:** 5

## Tools and Libraries

- Python
- Pandas and NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Data Cleaning

The following checks and transformations were performed:

- Identified missing values in `last_review`, `reviews_per_month`, `host_name`, and `name`.
- Filled missing host and listing names with `"Unknown"`.
- Filled missing `reviews_per_month` values with zero for listings with no reviews.
- Converted `last_review` to a datetime data type.
- Checked for duplicate rows and duplicate listing IDs.
- Used the Interquartile Range (IQR) method to identify potential price outliers.
- Created a separate price-analysis dataset excluding 11 zero-price listings.

Missing `last_review` dates were retained because these listings had no recorded reviews. High-priced listings were not automatically removed because extreme values are not necessarily data errors.

## Exploratory Data Analysis

### 1. Room Type Distribution

- Entire home/apartment: 51.97%
- Private room: 45.66%
- Shared room: 2.37%

Entire homes and apartments form the largest category, closely followed by private rooms.

### 2. Neighbourhood Distribution

- Manhattan: 44.30%
- Brooklyn: 41.12%
- Queens: 11.59%
- Bronx: 2.23%
- Staten Island: 0.76%

Manhattan and Brooklyn together account for 85.42% of listings.

### 3. Price Analysis

- Median price in the original dataset: $106 per night
- Mean price in the original dataset: approximately $152.72
- Highest recorded price: $10,000
- Potential outliers identified using IQR: 2,972

The price distribution is strongly right-skewed. The mean is higher than the median, indicating that expensive listings influence the average.

### 4. Price by Neighbourhood and Room Type

Manhattan has the highest median nightly price among the neighbourhood groups. Entire homes and apartments also have a higher median price than private and shared rooms.

### 5. Reviews and Availability

- Listings with zero reviews: 10,052
- Listings unavailable for all 365 days: 17,533
- Listings available for all 365 days: 1,295
- Median availability: 45 days

The review-count distribution is right-skewed, and many listings have limited recorded review activity.

### 6. Correlation Analysis

The strongest correlation among the selected numerical variables is between `number_of_reviews` and `reviews_per_month`, at approximately 0.59.

Price has very weak linear correlations with the other numerical variables in this analysis.

## Key Takeaways

- Airbnb listings are concentrated in Manhattan and Brooklyn.
- Entire homes and apartments make up just over half of all listings.
- Nightly prices are right-skewed, making the median a useful measure of typical price.
- Missing review information can be handled without discarding thousands of listings.
- Potential outliers should be investigated before being removed.

## Project Status

Data inspection, missing-value handling, duplicate checks, price outlier detection, and exploratory analysis have been performed in a Jupyter Notebook.

Further work could include geographic visualizations, neighbourhood-level price comparisons, and more detailed analysis of listing availability.

## How to Run

1. Clone or download this repository.
2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. Download the dataset from Kaggle.
4. Open the notebook in Jupyter.
5. Update the CSV path if necessary and run the cells sequentially.
