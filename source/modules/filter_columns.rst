Select Columns from DataFrame
=============================

Overview:
^^^^^^^^^

The **Select Columns from DataFrame Module** allows users to choose
specific columns from a dataset to create a new DataFrame. Users can
manually select columns or upload a file containing column names to
pre-select columns. The module provides flexibility for narrowing down
the dataset to only the most relevant columns.

Purpose:
^^^^^^^^

This module is designed to help users focus on specific columns of
interest within a dataset. By filtering the columns, users can
streamline their analysis by reducing the size of the dataset and
retaining only the relevant data.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects one DataFrame from the available
      datasets. The selected DataFrame will be used for column
      selection.
   -  **Use Case**: This input allows users to choose which dataset they
      want to refine by selecting specific columns.

2. **File Uploader for Pre-Selecting Columns**:

   -  **File Upload**: Users can upload a text file (e.g., ``.txt`` or
      ``.csv``) containing column names. The uploaded file should
      contain one column name per line. The uploaded column names will
      automatically be selected in the list of columns.
   -  **Use Case**: This option helps users pre-select columns from an
      external file, making it easier to narrow down the columns
      quickly.

3. **Scrollable Container for Column Selection**:

   -  **Checkboxes**: A scrollable list of checkboxes is displayed,
      allowing users to manually select or deselect columns from the
      DataFrame.
   -  **Use Case**: Allows users to browse through all available columns
      and select the ones relevant to their analysis.

4. **Select All / Deselect All**:

   -  **Buttons**: Two buttons allow users to either select all columns
      or deselect all columns at once.
   -  **Use Case**: This is useful when users want to quickly select or
      deselect all columns without manually toggling each checkbox.

5. **Button: Create DataFrame with Selected Columns**:

   -  **Functionality**: Clicking this button creates a new DataFrame
      based on the selected columns. The resulting DataFrame is
      displayed for the user to review and is also saved for future use.
   -  **Use Case**: This option allows users to finalize their selection
      and generate a new dataset that includes only the chosen columns.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Column Selection**:

   -  Users can manually select columns from a list or upload a file
      containing column names to pre-select the columns.
   -  If the user chooses to select all or deselect all columns, the
      selection is updated accordingly.

2. **File Upload for Pre-Selection**:

   -  If a file is uploaded, the module reads the column names from the
      file and automatically checks the corresponding columns in the
      scrollable list, making it easier to select specific columns
      quickly.

3. **New DataFrame Creation**:

   -  After column selection, a new DataFrame is created with only the
      selected columns. This DataFrame is displayed for user review and
      saved for further use in the data pipeline.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Selecting Relevant Columns for Analysis**: A biologist has a dataset
containing hundreds of columns but only needs to analyze a few specific
columns related to experimental conditions and results. Using this
module, they can either upload a file containing the relevant column
names or manually select the columns from the scrollable list. Once the
columns are selected, the module generates a new DataFrame that includes
only the columns of interest, allowing the biologist to focus on the
necessary data.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Manual or File-Based Column Selection**: Users can choose columns
   manually or upload a file with column names to streamline the
   selection process.
-  **Select All/Deselect All**: Quickly select or deselect all columns
   with a single click.
-  **Scrollable Container**: The module provides a scrollable container,
   making it easier to browse and select columns in large datasets.

--------------

Notes:
~~~~~~

-  **Pre-Selection File Format**: The uploaded file should contain one
   column name per line (either ``.txt`` or ``.csv`` formats are
   supported) to ensure proper pre-selection.
-  **Column Availability**: Ensure that the column names in the uploaded
   file match the actual column names in the dataset to avoid errors.
