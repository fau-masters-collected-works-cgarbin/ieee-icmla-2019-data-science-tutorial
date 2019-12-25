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

We used:

- [Pandas](https://pandas.pydata.org/) to read the data into well-structure [`DataFrame`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).
- [`shape`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html), [`columns`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.columns.html), [`dtypes`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dtypes.html), and [`head()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.head.html) to investigate the basic structure of the dataset.
- [`isnull()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isnull.html) to check for missing values.
- [`describe()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html) and [`unique()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.unique.html) to verify that columns are consistent with what we expect them to be.

## 2. Statistics and data science

[Notebook 2](2-statistics-and-data-science.ipynb) describes how to clean up a dataset, removing outliers that are not relevant for the analysis. To do that we have to first understand the domain of the data we were using (working-age population). We also remove attributes (columns) that were not relevant for the analysis.

Once we had a clean dataset, we collected enough evidence to call for action on possible gender discrimination by using:

- seaborn [`distplot()`](https://seaborn.pydata.org/generated/seaborn.distplot.html) to review the distribution of dataset attributes.
- [Box plots](https://en.wikipedia.org/wiki/Box_plot), with seaborn [`distplot()`](https://seaborn.pydata.org/generated/seaborn.boxplot.html), to inspect details of an attribute's distribution: its quartiles and outliers.
- Pandas `DataFrame` [masks](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.mask.html) to filter out rows. For example, to remove employes over a certain age, or below an education level.
- seaborn [`pairplot()`](https://seaborn.pydata.org/generated/seaborn.pairplot.html) to view the relationship of all attributes of a dataset at a glance.
- Pandas' [`cut()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html) to bin (group) attributes into larger categories.

## 3. Using data to answer questions

[Notebook 3](3-using-data-to-answer-questions.ipynb) uses permutations of a dataset with `np.random.permutation()` to test hypotheses

To prove (or disprove) a hypothesis, we:

- Inspected the dataset with `shape`, `columns`, `describe()`, and `info()`
- Checked for possible duplicated entries with `nunique()`.
- Performed a domain check (a suspiciously low literacy rates), to verify if the data make sense. We found out that it matches a reliable source.
- To make the code clearer, we split out of the dataset only the pieces of information we need and transformed some pieces of data into a more convenient format (`fertility` and `illiteracy`).
- Established that there is a correlation visually (with a scatter plot) and formally (with the [Pearson correlation coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)).
- Once we confirmed that there is a correlation, we performed a large number of experiments to check if the correlation exists by chance (with `np.random.permutation()`).
- To make our experiments reproducible, we set a seed for the pseudorandom generator (`np.random.seed(42)`).
