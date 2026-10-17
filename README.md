# Berlin Rental Prices Analysis

This project analyzes which property and location characteristics are associated
with rental prices in Berlin. The analysis is implemented in the Jupyter
notebook [`Berlin_rental_prices_project2.0.ipynb`](./Berlin_rental_prices_project2.0.ipynb)
and uses the accompanying [`rentals.csv`](./rentals.csv) dataset.

## Project contents

- **`Berlin_rental_prices_project2.0.ipynb`** - Complete exploratory,
  descriptive, inferential, and regression-based analysis.
- **`rentals.csv`** - 30,000 Berlin rental listings with 30 variables,
  including location, property characteristics, amenities, listing date, and
  rental prices.

The main response variable is `rent_per_m2_kalt_eur`, the monthly cold rent per
square metre. The dataset also contains variables such as district
(`bezirk`), area, number of rooms, building era, property condition, lift,
balcony, furnishing, public transport distance, and distance to the
Brandenburg Gate.

## Setting up the virtual environment

From the repository root, create and activate a local virtual environment using
Windows PowerShell:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install the notebook runtime and analysis dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install `
  jupyter ipykernel `
  pandas numpy matplotlib seaborn scipy statsmodels kagglehub
```

Register the environment as a user-level Jupyter kernel and launch Jupyter:

```powershell
python -m ipykernel install --user `
  --name berlin-rental-prices `
  --display-name "Python (Berlin Rental Prices)"
jupyter notebook
```

Use the `Python (Berlin Rental Prices)` kernel for
`Berlin_rental_prices_project2.0.ipynb`. Deactivate the environment with
`deactivate` when finished.

### Data loading note

The notebook currently loads `rentals.csv` from the Kaggle dataset
`sergionefedov/berlin-real-estate-sales-and-rentals-2020-2026` through
`kagglehub`. Depending on the Kaggle configuration, the first execution may
require Kaggle authentication or access to the dataset. A local copy of
`rentals.csv` is included in this project for reference and reproducibility.

## Analysis overview

The notebook covers the following steps:

1. **Data overview and quality checks** - inspect the dataset structure,
   numeric and categorical variables, missing values, duplicates, skewness,
   and potential outliers.
2. **Descriptive analysis** - examine the distribution of cold rent per square
   metre and compare rental prices across Berlin districts, amenities, and
   property conditions.
3. **Relationships between variables** - use correlations and visualizations
   to investigate the associations of rental prices with area, distance to
   central Berlin, public transport distance, and building age.
4. **Time analysis** - examine changes in rental prices between 2020 and 2026.
5. **Inferential analysis** - apply t-tests for amenities, one-way ANOVA for
   districts and property condition, and bootstrap confidence intervals for
   district medians.
6. **Regression analysis** - fit simple and multiple linear regression models
   to evaluate the combined association of location, amenities, building age,
   and area with rental prices.

## Conclusion

The analysis indicates that location is one of the strongest factors associated
with Berlin rental prices. Rental prices differ substantially between
districts, and properties closer to the Brandenburg Gate or public transport
stations tend to have higher cold rents per square metre. Lift and balcony
availability are associated with statistically significant differences in mean
rent, while furnishing does not show a statistically significant difference.
Property condition alone does not provide sufficient statistical evidence of
different mean rental prices.

Rental prices also show an upward trend over the observed period from 2020 to
2026. These results describe associations in the available listings; they
should not be interpreted as proof of causal relationships or as a complete
forecast of the Berlin rental market.
