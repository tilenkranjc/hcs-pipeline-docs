Feature Selection
=================

Overview:
^^^^^^^^^

The **Feature Selection Module** allows users to refine their dataset by
applying various feature selection techniques. Users can reduce the
number of features (columns) based on thresholds for variance,
correlation, and more. The module also provides an option to download a
list of selected features for further analysis.

Purpose:
^^^^^^^^

This module helps users remove redundant or irrelevant features,
improving the efficiency of downstream analysis by reducing the
complexity of the dataset. Feature selection is crucial when working
with high-dimensional datasets, as it helps improve model performance
and reduces overfitting.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects one DataFrame from the available
      datasets. The selected dataset will undergo feature selection.
   -  **Use Case**: This input allows users to choose which dataset they
      want to reduce in size by selecting relevant features.

2. **Select Metadata Columns**:

   -  **Multiselect**: The user selects metadata columns that will not
      be subjected to feature selection. These columns often represent
      non-numeric or categorical data, such as ``Treatment``, ``Plate``,
      or ``Timepoint``.
   -  **Use Case**: Metadata columns are preserved to ensure they remain
      available for grouping or labeling purposes, while feature
      selection is applied to numeric data columns.

3. **Select Feature Selection Operations**:

   -  **Checkboxes**: The user can choose from several feature selection
      techniques:

      -  **Variance Threshold**: Removes features with low variance,
         which don’t vary much across the dataset and therefore
         contribute little information.
      -  **Correlation Threshold**: Removes highly correlated features,
         as they may carry redundant information.
      -  **Blocklist**: Removes predefined unwanted features based on a
         blocklist.
      -  **Drop Columns with NaNs**: Removes columns that contain
         missing values (NaNs).

   -  **Use Case**: These techniques help refine the dataset by focusing
      on features that carry meaningful, non-redundant information.

4. **Button: Run Feature Selection**:

   -  **Functionality**: Clicking this button applies the selected
      feature selection techniques to the dataset. The reduced dataset
      is displayed, and statistics about the feature selection process
      are provided.
   -  **Use Case**: Initiates the feature selection process.

5. **Download List of Selected Features**:

   -  **Button**: After running the feature selection, users can
      download a list of the selected features as a text file.
   -  **Use Case**: Useful for tracking or sharing the selected features
      or for further analysis.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Feature Selection**:

   -  The selected feature selection techniques are applied to the
      numeric data columns (excluding metadata). Techniques such as
      variance and correlation thresholds help eliminate features that
      are either uninformative or redundant.
   -  The module uses the **pycytominer** library for feature selection,
      ensuring high-quality and efficient processing.

2. **Preserving Metadata**:

   -  The module ensures that metadata columns are preserved, so they
      are not affected by feature selection. After the feature selection
      process, the metadata columns are recombined with the selected
      features.

3. **Downloadable Feature List**:

   -  The user can download a list of the selected features as a text
      file. This list can be used for documentation or as input for
      further analysis.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Selecting Relevant Features from High-Dimensional Data**: A biologist
is working with a large dataset containing thousands of features from a
high-content screening experiment. They use this module to remove
features that have low variance or are highly correlated, ensuring the
remaining features provide valuable, non-redundant information for
further analysis. They also download the list of selected features to
use in other machine learning tools.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Multiple Feature Selection Techniques**: Users can select one or
   more feature selection techniques, tailoring the process to their
   specific dataset and goals.
-  **Download Feature List**: The module allows users to save a text
   file with the names of the selected features, which is helpful for
   documentation and future analysis.
-  **Metadata Handling**: Metadata columns are excluded from feature
   selection to ensure important non-numeric data remains intact.

--------------

Notes:
~~~~~~

-  **Feature Selection Impact**: Removing redundant or irrelevant
   features can improve the efficiency and performance of downstream
   analysis, such as machine learning or statistical modeling.
-  **Consistency in Metadata**: Be sure to correctly define metadata
   columns, as these will not be affected by feature selection and will
   remain in the final dataset.
