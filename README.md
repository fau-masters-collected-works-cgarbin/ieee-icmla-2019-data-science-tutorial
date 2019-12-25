# IEEE ICMLA 2019 Data Science Tutorial

Code for the 
[IEEE ICMLA (International Conference on Machine Learning and Applications)](https://www.icmla-conference.org/icmla19/)
[_The Data Science landscape: foundations, tools, and practical applications_](https://www.icmla-conference.org/icmla19/links/tutorialAM.htm)
session.

Quick "get started" guide:

1. Clone this repository
1. `cd` to the repository's directory
1. `pip install -r requirements.txt`
1. `jupyter lab`

## 1. Exploratory data analysis (EDA)

[Notebook 1](1-exploratory-data-analysis.ipynb) is about understanding the pieces of information we have in the dataset, and being confident it is not missing values and that each column has, in general, usable values (a few of them may need to be cleaned up - we will deal with that later).

To get to this point, we used:

- [Pandas](https://pandas.pydata.org/) to read the data into well-structure [`DataFrame`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).
- [`shape`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html), [`columns`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.columns.html), [`dtypes`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dtypes.html), and [`head()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.head.html) to investigate the basic structure of the dataset.
- [`isnull()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isnull.html) to check for missing values.
- [`describe()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html) and [`unique()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.unique.html) to verify that columns are consistent with what we expect them to be.

