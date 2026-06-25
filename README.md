# Retail Sales Impact Analysis

This project looks at what actually moves weekly sales in a large retail chain. Working from
about 374,000 weekly records across many stores and departments, I clean the data, explore it,
and then fit a few regression models to see how holidays, promotions, and the wider economy
(fuel prices, CPI, unemployment) relate to sales.

It was done as a term project for Data Analysis for Economics, together with Aurad Asif.

## Questions I wanted to answer

- Do holidays and promotional discounts noticeably lift weekly sales?
- Are macro factors like fuel price, CPI, and unemployment connected to how stores perform?
- Is there a clear seasonal pattern across the year?
- Can a straightforward model predict weekly sales from these features, and which features matter most?

## The data

The dataset has roughly 374,000 rows and 15 columns, with each row being one department in one
store for one week. The main columns are weekly sales, store and department identifiers, store
type and size, temperature, fuel price, CPI, unemployment, a holiday flag, and a promotional
discount figure, plus year, month, and week.

The full files are large, so they are not stored in this repository (the raw Excel is about
49 MB and the cleaned version about 24 MB; GitHub also blocks files over 100 MB). Instead, a
1,000-row sample of the cleaned data lives in
[`data/amazon_sales_cleaned_sample.csv`](data/amazon_sales_cleaned_sample.csv), which is enough
to read the notebook and follow the logic. See [`data/README.md`](data/README.md) for how to get
the complete dataset.

## How the analysis is organised

1. Cleaning: fixing data types, handling duplicates and missing values, and dealing with outliers.
2. Feature work: splitting out dates and grouping continuous variables into readable bins.
3. Single-variable exploration: distributions and density plots for every field.
4. Two- and three-variable views: weekly sales broken down by combinations of drivers.
5. Correlations: a heatmap of how the numeric fields relate.
6. Seasonality: how sales shift across weeks, months, and holidays.
7. Modelling: linear, ridge, lasso, and elastic net regressions, compared on R squared, RMSE, and MAE.

## The report

The full write-up (34 pages) and the slides are in the `reports` folder:

- [Amazon_Retail_Sales_Report.pdf](reports/Amazon_Retail_Sales_Report.pdf)
- [Retail_Sales_Impact_Analysis.pptx](reports/Retail_Sales_Impact_Analysis.pptx)

## Tools

Python, with pandas and NumPy for the data work, Plotly, seaborn, and matplotlib for the charts,
and scikit-learn for the models.

## Running it yourself

```bash
git clone https://github.com/umairahmedazizi/amazon-retail-sales-eda.git
cd amazon-retail-sales-eda
pip install pandas numpy matplotlib seaborn plotly scikit-learn jupyter openpyxl
jupyter notebook notebook/amazon_retail_sales_eda.ipynb
```

The notebook in the repo has its outputs cleared to keep the file small (the original was about
127 MB of saved charts), so run the cells to regenerate the visuals.

## Repository layout

```
amazon-retail-sales-eda/
  notebook/   the full analysis
  data/       a sample of the cleaned data, plus notes on the full dataset
  reports/    the written report and the slides
```

## Licence

The code is under the MIT licence. The report and slides are coursework, shared here as part of
my portfolio.
