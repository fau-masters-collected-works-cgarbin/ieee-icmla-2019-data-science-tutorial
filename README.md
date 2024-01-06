# IEEE ICMLA 2019 Data Science Tutorial

Code for the
[IEEE ICMLA (International Conference on Machine Learning and Applications)](https://www.icmla-conference.org/icmla19/)
[_The Data Science landscape: foundations, tools, and practical applications_](https://www.icmla-conference.org/icmla19/links/tutorialAM.htm)
session.

Quick "get started" guide:

1. Clone this repository
1. `cd` to the repository's directory
1. Optional: create a [Python virtual environment](https://docs.python.org/3/tutorial/venv.html)
    1. `python3 -m venv env`
    1. `source env/bin/activate` (Windows: `env\Scripts\activate.bat`)
    1. `python -m pip install --upgrade pip`
1. `pip install -r requirements.txt`
1. `jupyter lab` (or use Visual Studio Code's Jupyter extension)

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

- seaborn [`histplot()`](https://seaborn.pydata.org/generated/seaborn.histplot.html) to review the distribution of dataset attributes.
- [Box plots](https://en.wikipedia.org/wiki/Box_plot), with seaborn [`boxplot()`](https://seaborn.pydata.org/generated/seaborn.boxplot.html), to inspect details of an attribute's distribution: its quartiles and outliers.
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
- Established that there is a correlation visually (with a [scatter plot](https://seaborn.pydata.org/generated/seaborn.scatterplot.html)) and formally (with the [Pearson correlation coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)).
- Once we confirmed that there is a correlation, we performed a large number of experiments to check if the correlation exists by chance (with `np.random.permutation()`).
- To make our experiments reproducible, we set a seed for the pseudorandom generator (`np.random.seed(42)`).

## 4. Machine learning and data science

[Notebook 4](4-machine-learning-and-data-science.ipynb) uses machine learning to build a model that achieved over 80% accuracy with a few lines of code and without resorting to feature engineering or other transformations.

Along the way we also:

- Verified that the dataset is imbalanced and adjusted the code accordingly (`value_counts()`).
- Used stratified sampling to split the dataset and preserve the class ratios (`train_test_split(..., stratify=...)`).
- Used precision and recall to understand where the model makes mistakes (`classification_report()`).
- Visualized the mistakes with a [confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix) ([`confusion_matrix()`](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)).
- Established a baseline with a simple model.
- Switched to a more complex model, improving the baseline results.
- Found an even better model with grid search ([`GridSearchCV()`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)).

## More on this topic

If you found this repository useful, you may also want to checkout these repositories:

- [Introduction to data science](https://github.com/fau-masters-collected-works-cgarbin/cap5768-introduction-to-data-science): the first formal training I had in data science, as part of my master's work. A series of assignments from the class, covering different aspects of data science.
- [How to write well-structured, understandable, reliable, flexible Jupyter notebooks](https://github.com/fau-masters-collected-works-cgarbin/writing-good-jupyter-notebooks).
