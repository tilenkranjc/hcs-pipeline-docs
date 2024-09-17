Interactive Barplot
===================

Overview:
^^^^^^^^^

The **Interactive Barplot Module** allows users to create an interactive
bar plot from a selected dataset. Users can choose metadata columns for
grouping and labeling, and a data column to plot on the y-axis. The
module is highly customizable, offering options for grouping data,
setting labels, and adding color coding, all of which help users
visualize their data more effectively.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects a DataFrame from the available
      datasets to visualize.
   -  **Use Case**: This allows users to choose which dataset they want
      to plot.

2. **Metadata Column Inference**:

   -  **Checkbox**: Users can choose whether metadata columns start with
      ``Metadata_``, simplifying metadata selection.
   -  **Use Case**: Useful when working with large datasets where
      metadata columns follow a specific naming convention.

3. **Remove CellProfiler Features**:

   -  **Checkbox**: This option filters out common CellProfiler feature
      columns (e.g., ``AreaShape``, ``Intensity``) from the metadata
      options, making it easier to focus on relevant metadata.
   -  **Use Case**: Reduces clutter when selecting metadata columns,
      especially in high-content screening data.

4. **Metadata Column Selection**:

   -  **Multiselect**: Users can select which metadata columns to
      include in the plot. These columns can be used as x-axis labels or
      for color grouping.
   -  **Use Case**: Metadata columns may contain information about
      experimental conditions, timepoints, or treatments, which users
      want to visualize.

5. **X-Axis Labels**:

   -  **Multiselect**: The user selects metadata columns to concatenate
      and use as x-axis labels.
   -  **Use Case**: Useful when users want to display detailed labels
      combining multiple metadata columns.

6. **Color Grouping**:

   -  **Multiselect**: The user selects metadata columns to concatenate
      for color grouping.
   -  **Use Case**: Grouping by color helps differentiate samples or
      conditions in the bar plot, enhancing the visual interpretation of
      the data.

7. **Data Column Selection (Y-Axis)**:

   -  **Selectbox**: The user selects a data column to plot on the
      y-axis. This is the quantitative variable to be displayed.
   -  **Use Case**: Data columns often represent numerical values like
      measurements, counts, or averages that the user wants to
      visualize.

8. **Button: Plot Data**:

   -  **Functionality**: Clicking this button generates the bar plot
      based on the selected x-axis, y-axis, and color grouping options.
   -  **Use Case**: This option finalizes the user’s selections and
      renders the interactive plot.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Slicing the Data**:

   -  The selected DataFrame is sliced to include only the columns
      needed for plotting. This includes metadata columns for the x-axis
      and color grouping, as well as the selected data column for the
      y-axis.

2. **Concatenation of Metadata for Labels and Grouping**:

   -  Metadata columns selected for the x-axis labels and color grouping
      are concatenated into strings. This helps display detailed,
      combined information from multiple metadata columns.

3. **Interactive Plotting**:

   -  The plot is generated using **Plotly Express**, an interactive
      plotting library. The plot is responsive, allowing users to zoom,
      hover, and explore the bar plot interactively.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Visualizing Experimental Results by Treatment and Timepoint**: A
biologist has experimental data from multiple conditions, including
different treatments and timepoints. They want to visualize how a
specific measurement (e.g., cell viability) changes across treatments
and time. Using this module, the biologist selects ``Treatment`` and
``Timepoint`` metadata columns for the x-axis labels and
``Cell Viability`` as the y-axis variable. The result is an interactive
bar plot showing cell viability grouped by treatment and time, with
color-coded bars representing different experimental conditions.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Customizable X-Labels and Grouping**: Users can concatenate
   multiple metadata columns to create detailed x-axis labels and group
   data by different metadata for color coding.
-  **Flexible Data Input**: The module automatically infers metadata
   columns and excludes irrelevant ones based on user preferences,
   making it easier to focus on the most important data.
-  **Interactive Plotting**: The use of Plotly allows for interactive
   exploration of the data, giving users the ability to zoom in, hover
   over bars for more details, and explore trends visually.

--------------

Notes:
~~~~~~

-  **Metadata Inference**: The module can automatically detect metadata
   columns based on naming conventions (``Metadata_``). This is
   particularly helpful when working with large datasets that follow
   standard metadata naming conventions.
-  **DataFrame Requirements**: The selected DataFrame must contain both
   metadata columns (for grouping and labeling) and data columns (for
   plotting on the y-axis). Ensure that the correct columns are selected
   for effective visualization.
