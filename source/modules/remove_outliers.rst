Remove Outliers
===============

Overview:
^^^^^^^^^

The **Remove Outliers Module** allows users to identify and remove
outliers from their dataset using three different statistical methods:
Mean ± k*SD (Standard Deviation), Interquartile Range (IQR), and Median
Absolute Deviation (MAD). Outlier removal helps improve data quality by
eliminating extreme values that could skew the results of analyses.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects the DataFrame to clean by removing
      outliers.
   -  **Use Case**: This ensures that users can target the specific
      dataset they are working with for outlier detection and removal.

2. **Outlier Removal Methods**:

   -  **Mean ± k*SD**:

      -  Outliers are defined as values that fall outside the range of
         the mean ± (k \* standard deviation).
      -  This method is sensitive to extreme outliers because it relies
         on the mean and standard deviation, which can be affected by
         outliers.
      -  **Best for**: Normally distributed data where outliers deviate
         from the general trend.

   -  **Interquartile Range (IQR)**:

      -  Outliers are values less than Q1 - (k \* IQR) or greater than
         Q3 + (k \* IQR), where IQR is the range between the 1st (Q1)
         and 3rd (Q3) quartiles.
      -  This method is robust to extreme values, making it useful for
         non-normally distributed data.
      -  **Best for**: Skewed or non-normal distributions, or when data
         contains many extreme values.

   -  **Median Absolute Deviation (MAD)**:

      -  This method identifies outliers based on deviations from the
         median, making it robust to outliers in the data.
      -  MAD is often considered more robust than using standard
         deviation because it is based on the median rather than the
         mean.
      -  **Best for**: Data with heavy tails, or when robustness to
         outliers is critical.

3. **k Factor**:

   -  **Number Input**: The user specifies the k factor, which
      determines the threshold for outlier detection (e.g., mean ± k \*
      SD).
   -  **Use Case**: Adjusting the k factor allows the user to set the
      sensitivity of outlier detection, with higher values detecting
      fewer outliers and lower values detecting more.

4. **Minimal Number of Replicates**:

   -  **Number Input**: The user specifies the minimum number of
      replicates required for outlier detection. This ensures that only
      groups with sufficient data points are analyzed.
   -  **Use Case**: This is important for ensuring that calculations are
      meaningful, especially in small datasets.

5. **Metadata Column Inference**:

   -  **Checkboxes**: The user can choose whether metadata columns start
      with ``Metadata_`` or whether to remove certain feature columns
      (such as those from CellProfiler) from the metadata options.
   -  **Use Case**: Simplifies the selection of relevant columns by
      filtering out irrelevant or non-metadata columns.

6. **Grouping Columns**:

   -  **Multiselect**: The user selects grouping columns for which
      outlier detection will be performed. This ensures that outliers
      are detected within groups (e.g., by plate, treatment, or
      timepoint).
   -  **Use Case**: Grouping allows users to identify outliers in
      specific experimental conditions or batches.

--------------

Computation Details:
~~~~~~~~~~~~~~~~~~~~

1. **Mean ± k*SD Method**:

   -  Formula: Outliers are defined as any value outside the range: [
      :math:`\text{mean} \pm k \times \text{standard deviation}` ]
   -  **Advantages**: Useful for normally distributed data. Sensitive to
      extreme values.
   -  **Drawback**: Can be skewed by the very outliers it aims to
      remove, as the mean and standard deviation are sensitive to
      extreme values.

2. **Interquartile Range (IQR) Method**:

   -  Formula: Outliers are values outside: [ 
      :math:`Q1 - (k \times IQR) \quad \text{or} \quad Q3 + (k \times IQR)` ] where IQR =
      Q3 - Q1 (the difference between the 75th and 25th percentiles).
   -  **Advantages**: Robust against extreme values, useful for skewed
      data.
   -  **Drawback**: Less effective if the dataset is normally
      distributed with few outliers.

3. **Median Absolute Deviation (MAD) Method**:

   -  Formula: Outliers are values that deviate from the median by more
      than a certain threshold: [ :math:`\text{Outlier if: } \|x -\text{median} | > k \times \text{MAD}` ] where MAD is the
      median of the absolute deviations from the median.
   -  **Advantages**: Very robust to outliers, particularly effective
      for data with non-normal distributions.
   -  **Drawback**: More complex to compute, especially for large
      datasets.

--------------

Recommendations for Method Selection:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Mean ± k*SD**:

   -  **Best for**: Normally distributed data with few outliers.
   -  **When to Use**: Use this method if the dataset has a bell-shaped
      (normal) distribution and the primary concern is extreme
      deviations from the mean.
   -  **Tip**: Start with k=2 or k=3 and adjust based on the number of
      outliers detected.

2. **Interquartile Range (IQR)**:

   -  **Best for**: Skewed or non-normal data, or when outliers are
      expected at the extreme ends.
   -  **When to Use**: Use this method if the dataset contains many
      extreme values or if the distribution is skewed. It’s ideal for
      biological data, which often follows non-normal distributions.
   -  **Tip**: A common choice for k is 1.5, which effectively removes
      moderate outliers.

3. **Median Absolute Deviation (MAD)**:

   -  **Best for**: Data with extreme outliers or non-normal
      distributions.
   -  **When to Use**: This method is best when robustness to extreme
      values is critical, such as in heavy-tailed distributions.
   -  **Tip**: MAD works well with a k-factor of 2-3, depending on the
      extremity of the outliers.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Removing Outliers from Experimental Data**: A biologist is analyzing
cell viability data collected from multiple plates. Some measurements
are far outside the expected range, likely due to experimental error or
data collection issues. To clean the dataset, the biologist selects the
**IQR** method with a k-factor of 1.5, grouping the data by plate and
treatment conditions. This ensures that outliers are removed within each
experimental group, improving the overall data quality for further
analysis.
