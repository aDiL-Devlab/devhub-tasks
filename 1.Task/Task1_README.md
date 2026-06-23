# Task 1: Exploring and Visualizing the Iris Dataset

## Objective
Understand how to read, summarize, and visualize a dataset using the classic Iris flower dataset.

## Approach

**Data Loading and Inspection**
- Loaded the Iris dataset using seaborn
- Checked shape, columns, data types, missing values, and duplicates
- Found 1 duplicate row and removed it
- Final dataset: 149 rows and 5 columns

**Visualization**
- Scatter plot to analyze relationships between petal length and petal width
- Histogram to examine distribution of sepal length across species
- Box plot to detect outliers and spread across all 4 numerical features

## Results and Insights

- Dataset has 4 numerical features (sepal length, sepal width, petal length, petal width) and 1 categorical target (species: Setosa, Versicolor, Virginica)
- Petal length and petal width have a very strong positive correlation (0.96), as petal length increases, petal width increases too
- Setosa is clearly separated from the other two species based on petal size
- Versicolor and Virginica show slight overlap in the scatter plot
- Sepal width is the only feature where Setosa has the highest values compared to other species
- Box plot revealed sepal width has visible outliers
- Petal length shows the most variation across species, making it the most useful feature for distinguishing them
