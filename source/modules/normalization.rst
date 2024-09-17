Normalization
=============

Overview:
^^^^^^^^^

The **Normalization Module** allows users to normalize their datasets
using various normalization methods provided by **pycytominer**, a tool
used for processing high-content screening data. The module supports
grouping by metadata columns and the selection of different
normalization techniques, helping to prepare the dataset for downstream
analysis by making features more comparable across samples or
conditions.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      datasets to normalize.
   -  **Use Case**: This input allows users to choose which dataset they
      want to normalize.

2. **Normalization Method**:

   -  **Selectbox**: The user selects one of the available normalization
      methods:

      -  **Z-score (standardize)**: Standardizes features by subtracting
         the mean and dividing by the standard deviation.
      -  **Robustize**: Normalizes features using median and median
         absolute deviation (MAD).
      -  **MAD Robustize (mad_robustize)**: A robust normalization
         method using MAD for scaling.
      -  **Spherize**: Reduces correlation between features by
         transforming the data into a spherical shape.

   -  **Use Case**: Each method is suited for different normalization
      needs, and the user can select the method most appropriate for
      their dataset.

3. **Metadata Column Selection**:

   -  **Checkbox**: Users can choose whether metadata columns start with
      “Metadata\_” to simplify column selection.
   -  **Multiselect**: Allows the user to select the metadata columns.
      These columns are not affected by normalization.
   -  **Use Case**: Metadata columns are used to group the data,
      ensuring normalization is applied correctly within groups.

4. **Grouping Columns**:

   -  **Multiselect**: The user can select metadata columns to group by
      during normalization. For example, data can be grouped by
      treatment or timepoint before normalization.
   -  **Use Case**: Grouping allows normalization to be applied
      independently within specific experimental groups.

5. **Subset Query**:

   -  **Text Input**: Users can enter a query string to select negative
      controls or other subsets of the data to use as references during
      normalization.
   -  **Use Case**: Useful for normalizing based on a specific subset of
      the data, such as untreated or control samples.

6. **Button: Run Normalization**:

   -  **Functionality**: Clicking this button runs the selected
      normalization method on the dataset, using the selected metadata
      and grouping columns.
   -  **Use Case**: This initiates the normalization process based on
      the user’s selections.

--------------

Data Handling and Computation:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Normalization Methods**:

   -  **Z-score (standardize)**:

      -  This method transforms each feature (column) by subtracting the
         mean and dividing by the standard deviation: [ Z =
         :math:`\frac{X - \mu}{\sigma}` ]
      -  **Use Case**: Best used when features have different units or
         scales and need to be standardized to have zero mean and unit
         variance. Common in machine learning and statistical analyses.

   -  **Robustize**:

      -  Uses the median and MAD (median absolute deviation) to scale
         the data: [ Robustized Value =
         :math:`\frac{X - \text{median}(X)}{\text{MAD}(X)}` ]
      -  **Use Case**: Recommended for datasets with many outliers, as
         this method is less sensitive to extreme values than
         standardization.

   -  **MAD Robustize**:

      -  A more robust scaling technique using the MAD instead of
         standard deviation to reduce the impact of outliers.
      -  **Use Case**: Use this method when there are heavy-tailed
         distributions or outliers that could affect standard
         deviation-based normalization.

   -  **Spherize**:

      -  Reduces correlations between features by transforming the data
         into a spherical shape.
      -  **Use Case**: Useful when features are highly correlated, as
         this method can help to remove dependencies between features.

2. **Group-based Normalization**:

   -  The module allows users to normalize data within groups defined by
      the selected metadata columns. For example, users can normalize
      data for each experimental condition (e.g., treatment or
      timepoint) separately, ensuring that the normalization respects
      the structure of the experiment.

3. **Subset Query**:

   -  The subset query allows the user to specify a group of control
      samples or another subset to be used as a reference during
      normalization. This query can filter the data to apply
      normalization based only on specific samples, which is
      particularly useful when working with controls.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Normalization of High-Content Screening Data**: A biologist is working
with high-content screening data from multiple plates. They need to
normalize the features across different plates and experimental
conditions to ensure comparability. The biologist uses this module to
group the data by experimental conditions (e.g., treatment, plate) and
applies **Z-score normalization** to standardize the data across these
groups. This ensures that any differences in measurement scale between
plates are removed, and the features are comparable across all samples.

--------------

Recommendations for Normalization Method:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  **Z-score (standardize)**:

   -  Use when you want to standardize features to have the same scale
      (zero mean and unit variance), which is common in most machine
      learning algorithms and statistical analyses.

-  **Robustize**:

   -  Ideal when dealing with datasets that contain many outliers, as
      this method is more resilient to extreme values than traditional
      Z-score normalization.

-  **MAD Robustize**:

   -  Similar to Robustize but with even greater resistance to outliers.
      Suitable for data with highly skewed distributions or when
      outliers heavily influence the dataset.

-  **Spherize**:

   -  Use when the dataset has correlated features that may introduce
      noise in subsequent analyses. This method decorrelates features,
      making them more independent.

--------------

Notes:
~~~~~~

-  **Group-Based Normalization**: Always ensure that appropriate
   metadata columns are selected for grouping so that normalization is
   applied correctly within relevant experimental groups.
-  **Subset Query**: For datasets with control samples, specifying a
   subset query (e.g., negative controls) ensures that normalization is
   applied with respect to this subset, which is useful in controlled
   experiments.
-  **Data Distribution**: Be mindful of the distribution of your data
   when choosing a normalization method. For instance, **Z-score** works
   well for normally distributed data, while **Robustize** is better
   suited for data with outliers.
