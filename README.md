## 🧹 Data Cleaning Summary

We performed the following steps to clean the dataset before training a machine learning model:

### 1. Standardized Column Names
- Removed leading/trailing spaces from column names.
- Converted all column names to lowercase.
- Replaced spaces with underscores for consistency.
- Removed special characters like `($)` from column names (e.g., `Price($)` → `price`).

### 2. Handled Missing Values
- **bedrooms**: Filled missing values with the median number of bedrooms.
- **bath_rooms**: Filled missing values with the median number of bathrooms.
- **garage_available**: Filled missing values with `0.0` (assumed no garage).
- **furnishing**: Filled missing values with `'Unfurnished'`.
- **has_pool**: Filled missing values with `0.0` (assumed no pool).

### 3. Fixed Inconsistent Categorical Values
- Corrected typos in `furnishing` column:
  - `'furnised'` → `'Furnished'`
- Standardized `house_condition` values:
  - `'gd'` → `'good'`
  - `'Old'`, `'old'` → `'old'`
  - `'new'` → `'new'`

### 4. Verified Data Types
- Ensured all numerical columns (e.g., `size_sqft`, `lot_size`, `price`) were of type `float` or `int`.
- Ensured categorical variables were in string format where necessary.

### 5. Created New Feature
- Added a new feature called `house_age`, calculated as:
- house_age = current_year - year_built
  
## 🤖 Model Summary & Performance

### Model Used

We trained a **Linear Regression** model to predict house prices using the cleaned and engineered dataset. Features included:

- Bedrooms and bathrooms
- Square footage (`size_sqft`)
- Lot size
- House age
- Garage availability
- Presence of a pool
- Categorical features like location, furnishing, and house condition (encoded using one-hot encoding)

### Performance Metrics

The model was evaluated using standard regression metrics:

| Metric        | Value (Example) |
|---------------|-----------------|
| RMSE (Root Mean Squared Error) | 9200.729716753856 |
| MAE (Mean Absolute Error)      | 7072.56714673657 |
| R² Score (Coefficient of Determination) | 0.97 |

These results indicate the model explains approximately **97%** of the variance in house prices, which is a solid performance for a baseline model.

---

## 📈 Visualizations

The following visualizations were used to interpret the model's results:

### 1. 📉 Actual vs Predicted Prices

```python
import matplotlib.pyplot as plt

plt.scatter(y_test, y_pred, alpha=0.6)
plt.xlabel("Actual Prices")
plt.ylabel("Predicted Prices")
plt.title("Actual vs Predicted House Prices")
plt.show(
https://dev.to/sudoruss/balancing-type-i-and-type-ii-errors-a-medical-perspective-e5j

