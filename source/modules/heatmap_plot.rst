Interactive Heatmap
===================

Overview:
^^^^^^^^^

The **Interactive Heatmap Module** allows users to visualize a distance
matrix as a heatmap. This module leverages the interactivity of Plotly
to create a heatmap where users can easily explore and interpret
distance values between samples. The heatmap provides a visual
representation of the similarity or dissimilarity between rows and
columns of a distance matrix, making it ideal for identifying patterns
or clusters within the data.

Purpose:
^^^^^^^^

This module is designed for visualizing distance matrices, often used in
data analysis workflows to understand relationships between samples. The
heatmap visualization helps users quickly assess data patterns and
identify clusters or outliers within the dataset.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      datasets. This DataFrame should contain the distance matrix to be
      visualized as a heatmap.
   -  **Use Case**: Users can visualize the results of a previously
      calculated distance matrix from the pipeline.

2. **Button: Plot Heatmap**:

   -  **Functionality**: Clicking this button generates an interactive
      heatmap based on the selected distance matrix. The heatmap is
      rendered using Plotly and provides interactive features such as
      zooming and hovering over individual cells to see distance values.
   -  **Use Case**: This option allows users to create and explore the
      heatmap in an interactive environment.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Distance Matrix as Input**:

   -  The selected DataFrame should be a distance matrix, with rows and
      columns representing samples, and the matrix values representing
      distances (or dissimilarities) between those samples.

2. **Plotting the Heatmap**:

   -  The module uses **Plotly Express** to create the heatmap. Row and
      column labels are extracted from the DataFrame’s index and
      columns, ensuring that the heatmap accurately reflects the matrix
      structure.

3. **Customization**:

   -  The heatmap uses the ``Viridis`` color scale by default, providing
      a smooth gradient for visualizing distance values. Users can hover
      over the heatmap to see the exact distance values for each cell.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Visualizing Relationships Between Samples in a Distance Matrix**: A
biologist has calculated a distance matrix from experimental data,
representing the dissimilarities between various treatment groups based
on gene expression profiles. Using this module, they can visualize the
distance matrix as an interactive heatmap, allowing them to easily spot
clusters of similar treatments or outliers. The heatmap provides a quick
way to assess the relationships between different samples and identify
potential patterns.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Interactive Heatmap**: The Plotly-based heatmap provides
   interactivity, allowing users to zoom, hover over cells for detailed
   information, and explore the data visually.
-  **Custom Labels**: Row and column labels are extracted from the
   distance matrix, ensuring that the heatmap is easy to interpret in
   the context of the data.

--------------

Notes:
~~~~~~

-  **Input Requirements**: Ensure that the selected DataFrame is a
   distance matrix, with both row and column labels, and numerical
   values representing distances between samples.
-  **Interactive Features**: The heatmap is highly interactive,
   providing users with a dynamic tool to explore and analyze their
   distance matrix.
