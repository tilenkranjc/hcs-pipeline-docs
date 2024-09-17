Distance Matrix
===============

Overview:
^^^^^^^^^

The **Distance Matrix Module** enables users to compute and visualize a
distance matrix based on the selected data columns of a dataset. It
provides the option to compute either the Euclidean or Cosine distance
between the rows of the dataset. The matrix is labeled using metadata
columns, and the user can choose which metadata to include for labeling.

Purpose:
^^^^^^^^

This module allows users to calculate a distance matrix, which is useful
for understanding the similarity or dissimilarity between samples in the
dataset. The distance matrix can be used in various downstream analyses,
such as clustering, dimensionality reduction, or visualizations like
heatmaps.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      datasets. The selected DataFrame will be used to compute the
      distance matrix.
   -  **Use Case**: This input allows users to choose the dataset they
      want to analyze.

2. **Select Metadata Columns**:

   -  **Multiselect**: The user selects metadata columns that will be
      used to label the distance matrix. These columns represent
      non-numeric data that can help distinguish different samples
      (e.g., ``Treatment``, ``Timepoint``).
   -  **Use Case**: Helps in identifying samples in the distance matrix
      by their metadata.

3. **Select Distance Metric**:

   -  **Radio Button**: The user chooses the distance metric to
      calculate:

      -  **Euclidean Distance**: Measures the straight-line distance
         between samples.
      -  **Cosine Distance**: Measures the cosine of the angle between
         samples, often used when magnitude doesn’t matter but direction
         does.

   -  **Use Case**: Provides flexibility in selecting the appropriate
      metric depending on the nature of the data.

4. **Button: Calculate Distance Matrix**:

   -  **Functionality**: Clicking this button triggers the computation
      of the distance matrix based on the selected distance metric and
      columns. The matrix is then displayed and saved for further use.
   -  **Use Case**: Initiates the calculation process for the distance
      matrix.

--------------

Data Handling and Computation:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Distance Matrix Calculation**:

   -  **Euclidean Distance**: Measures the direct distance between two
      points in a multidimensional space. It’s appropriate for datasets
      where absolute differences between values matter.
   -  **Cosine Distance**: Measures the cosine of the angle between two
      vectors in a multidimensional space. It’s useful when the
      magnitude of the vectors is not as important as their orientation.

2. **Labeling the Distance Matrix**:

   -  Metadata columns selected by the user are used to generate labels
      for the distance matrix. Columns with constant values across all
      samples are excluded from the labels to ensure they are
      informative.
   -  If no metadata columns are selected or all selected columns have
      constant values, a default sample labeling is applied (e.g.,
      ``Sample 1``, ``Sample 2``, etc.).

3. **Saving the Distance Matrix**:

   -  The resulting distance matrix is saved so it can be accessed and
      used in future steps of the data pipeline, such as clustering or
      visualization.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Evaluating Similarity Between Experimental Samples**: A biologist
wants to understand how similar or different various treatment groups
are based on their experimental results. Using this module, they select
their dataset, choose metadata columns such as ``Treatment`` and
``Timepoint`` for labeling, and then compute the Cosine distance matrix.
The resulting matrix helps them identify which treatment groups are most
similar based on their experimental outcomes.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Distance Metric Choice**: Users can choose between Euclidean and
   Cosine distances, giving flexibility depending on whether the
   magnitude of the values or their relative orientation is more
   important.
-  **Metadata Labeling**: The user can select metadata columns for
   labeling, allowing for easy identification of samples in the distance
   matrix.
-  **Versatile Application**: The distance matrix can be used for
   clustering, dimensionality reduction, or as an input for further
   analyses in the data pipeline.

--------------

Notes:
~~~~~~

-  **Metadata Selection**: Only metadata columns with varying values
   across the dataset will be included in the labels. Constant metadata
   columns will be automatically excluded to ensure the labels are
   informative.
-  **Distance Metrics**: Use Euclidean distance when you care about
   absolute differences between samples, and Cosine distance when you
   care more about the direction or orientation of data points.

When to Use **Euclidean Distance**:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Euclidean distance** is the straight-line distance between two points
in a multidimensional space. It is appropriate when the magnitude of the
differences between values is important. This metric works well in cases
where you want to assess absolute differences across all dimensions (or
features) of your data.

.. _when-to-use-euclidean-distance-1:

When to use Euclidean distance:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Magnitude Matters**: When the absolute values or scales of the
   features are important. For example, if you are comparing gene
   expression levels, and the absolute difference in expression is
   meaningful, Euclidean distance is a good choice.
2. **Uniform Scale**: It works well if your data is on the same scale
   across features, meaning that differences across dimensions are
   comparable.
3. **Physical Distance Interpretation**: When your data represents
   physical measurements (e.g., distances, lengths, concentrations) and
   the actual magnitude of the differences between values matters.

Example Use Case:
^^^^^^^^^^^^^^^^^

If you are comparing the results of different treatment groups based on
measured cell growth rates, where you care about how much larger or
smaller the rates are, **Euclidean distance** is more suitable because
it measures the overall magnitude of difference between treatments.

--------------

When to Use **Cosine Distance**:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Cosine distance** (or more specifically, 1 - cosine similarity)
measures the cosine of the angle between two vectors. It focuses on the
orientation or direction of the vectors rather than their magnitude.
This metric is useful when the relationship between variables (i.e.,
direction) is more important than their absolute values.

.. _when-to-use-cosine-distance-1:

When to use Cosine distance:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Magnitude Doesn’t Matter**: When the relative difference (i.e., the
   shape or pattern) between the values is important, but the absolute
   magnitude is not. For example, if you’re analyzing high-dimensional
   data like gene expression profiles, and you’re more interested in the
   pattern of expression (whether two genes are up- or downregulated
   together) than the exact expression levels.
2. **Normalized or Sparse Data**: It works well when your data has been
   normalized (e.g., all vectors are of the same length) or when
   comparing sparse vectors, where the focus is on the similarity of the
   directions rather than the magnitudes.
3. **Direction-Based Similarity**: When comparing patterns of features
   or behaviors where the angle (direction) between data points is more
   meaningful than the actual distance.

.. _example-use-case-1:

Example Use Case:
^^^^^^^^^^^^^^^^^

If you are comparing gene expression profiles from different samples
where the relative upregulation and downregulation of genes are of
interest, **Cosine distance** is more appropriate. In this case, even if
two profiles have different absolute expression levels, they may still
be considered similar if the pattern of upregulation and downregulation
is the same across genes.

--------------

Summary:
~~~~~~~~

-  **Euclidean Distance**: Use when the **magnitude** of differences is
   important, such as when comparing physical measurements or absolute
   values.
-  **Cosine Distance**: Use when you care more about the **direction**
   or **pattern** of the data rather than the magnitude, such as when
   analyzing normalized or sparse data, or when assessing similarity in
   patterns.

Both metrics can be valuable depending on the structure of your data and
the goals of your analysis.
