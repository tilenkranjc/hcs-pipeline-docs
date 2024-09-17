Interactive Scatter Plot
========================

Overview:
^^^^^^^^^

The **Interactive Scatter Plot Module** enables users to create a
customizable scatter plot using metadata and data columns from a
selected dataset. Users can select which columns to use for the x-axis,
y-axis, and color grouping, as well as an optional column to size the
scatter points.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      data to plot.
   -  **Use Case**: Allows the user to specify which dataset they want
      to visualize.

2. **Metadata Column Options**:

   -  **Checkbox: Metadata columns start with ``Metadata_``**: Allows
      the user to filter metadata columns based on the “Metadata\_”
      prefix.
   -  **Checkbox: Remove CellProfiler features**: Filters out common
      CellProfiler features from the metadata column options to make it
      easier to focus on relevant metadata.
   -  **Use Case**: Helps users quickly isolate and select relevant
      metadata columns for plotting.

3. **Select Columns for X-axis and Y-axis**:

   -  **Selectbox**: Allows the user to select columns for the x-axis
      and y-axis from any column in the selected DataFrame.
   -  **Use Case**: The x and y axes define the two variables being
      compared in the scatter plot.

4. **Select Columns for Color Grouping**:

   -  **Multiselect**: Users can select one or more metadata columns to
      concatenate and use for color grouping in the scatter plot.
   -  **Use Case**: Color grouping enables users to differentiate data
      points based on specific metadata attributes.

5. **Select a Column for Point Size (Optional)**:

   -  **Selectbox**: Users can select a data column to control the size
      of scatter points.
   -  **Use Case**: This is useful for adding an additional dimension to
      the plot, where the size of each point represents another variable
      in the dataset.

--------------

Plot Generation:
~~~~~~~~~~~~~~~~

1. **X and Y Axes**:

   -  The columns selected for the x-axis and y-axis will be plotted
      against each other. These can be any columns from the dataset, not
      just metadata.

2. **Color Grouping**:

   -  If metadata columns are selected for color grouping, the values
      from these columns are concatenated to form a “color group” that
      is used to color-code the data points. Line breaks are
      automatically inserted into the labels for better readability.

3. **Point Size**:

   -  If a column is selected for point size, the values in this column
      determine the size of each point on the scatter plot. If no column
      is selected, all points are sized equally.

4. **Interactive Plot**:

   -  A scatter plot is generated using Plotly, which allows users to
      zoom, hover, and interact with the plot.
   -  The plot displays the x-axis and y-axis labels based on the
      selected columns, and the points are color-coded based on the
      “color group” metadata.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Comparing Expression Levels of Genes by Treatment Condition**: A
biologist wants to create a scatter plot comparing two gene expression
levels (X and Y) across different treatment conditions. The metadata
columns for “Treatment” and “Timepoint” are selected for color grouping,
and an additional column for “Sample Size” is selected to vary the size
of the points. The scatter plot will visually reveal any relationships
between the two gene expression levels across different treatments and
timepoints, with larger points representing larger sample sizes.
