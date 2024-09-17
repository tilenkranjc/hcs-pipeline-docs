Upload Data
===========

Overview:
^^^^^^^^^

The **Upload Data Module** allows users to upload CSV or Excel files and
integrate them into the analysis pipeline. Users can upload multiple
files, combine them into a single DataFrame, or process them as separate
datasets. The module also provides options for adding metadata columns,
such as filenames and plate numbers, to the data.

Purpose:
^^^^^^^^

The module enables users to seamlessly load data into the platform for
further analysis. It ensures that the uploaded files contain the
required metadata (such as row/column or well information) and offers
flexibility in how data from multiple files is handled.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **File Uploader**:

   -  **Functionality**: Allows the user to upload multiple CSV or Excel
      files simultaneously.
   -  **Accepted Formats**: ``.csv`` and ``.xlsx``.

2. **Checkbox: Add a column with the filename**:

   -  **Default**: Checked (enabled).
   -  **Functionality**: If enabled, this option appends a new column
      called ``filename`` to the DataFrame, which contains the name of
      the file from which the data originated.
   -  **Use Case**: Useful for tracking which file each row of data
      comes from, especially when working with multiple datasets.

3. **Checkbox: Add a column “Plate” with the file number**:

   -  **Default**: Checked (enabled).
   -  **Functionality**: If enabled, adds a ``plate`` column that
      enumerates the files starting with 1. Each file gets a unique
      number to track its origin.
   -  **Use Case**: Especially relevant for biological experiments
      involving multiple plates, where you may want to track
      plate-specific data.

4. **Checkbox: Import as separate DataFrames**:

   -  **Default**: Unchecked (disabled).
   -  **Functionality**: If enabled, each file is processed as an
      individual DataFrame and stored separately. Otherwise, the files
      are merged into a single DataFrame.
   -  **Use Case**: When files represent distinct datasets that should
      not be combined, this option allows you to keep them separate for
      later analysis.

5. **Dataset Name Input**:

   -  **Default**: Pre-populated with the current module display name.
   -  **Functionality**: The user can provide a custom name for the
      dataset. This name is used to save the concatenated or processed
      DataFrame in the session state.
   -  **Use Case**: Naming datasets helps identify them later in the
      pipeline for further processing or visualization.

6. **Submit Button**:

   -  **Functionality**: Once clicked, the uploaded files are processed
      according to the selected options.

--------------

Data Validation:
~~~~~~~~~~~~~~~~

-  **Column Requirements**:

   -  The module checks that each file contains either a combination of
      ``row`` and ``column`` columns, or a ``well`` column.
   -  If the file contains only a ``well`` column, it is automatically
      converted to ``row`` and ``column`` using the following logic:

      -  **Row**: Extracted from the first character (A → 1, B → 2,
         etc.).
      -  **Column**: Extracted from the numeric part of the well (e.g.,
         well ``A03`` results in row 1, column 3).

   -  If the necessary columns are not present, the module generates an
      error, preventing further processing.

-  **Metadata Check**:

   -  The module ensures that there is at least one additional column
      besides the required ``row``, ``column``, ``well``, and ``plate``
      columns. This additional column typically contains experimental
      metadata (e.g., treatment, time, or condition).

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Appending Metadata**:

   -  Based on user selection, additional columns such as ``filename``
      and ``plate`` are appended to each DataFrame to keep track of the
      data’s origin.

2. **Combining DataFrames**:

   -  If the **Import as Separate DataFrames** option is unchecked, the
      module concatenates all the uploaded files into a single DataFrame
      using ``pd.concat()``. The DataFrames are concatenated row-wise
      (``axis=0``), and the index is ignored (``ignore_index=True``) to
      ensure a continuous index in the combined DataFrame.

3. **Saving Data**:

   -  The processed DataFrames are saved in
      ``st.session_state.pipeline_results`` under the name specified by
      the user. This makes the data available for further analysis in
      subsequent modules.

--------------

Computation Background:
~~~~~~~~~~~~~~~~~~~~~~~

-  **Data Validation**:

   -  The check for ``row`` and ``column`` or ``well`` ensures that the
      uploaded files contain the necessary information to map data to
      specific wells or positions within a plate.
   -  The conversion of well identifiers (e.g., ``A03``) into ``row``
      and ``column`` allows for flexible file formats that may not
      explicitly provide row/column metadata.

-  **Concatenation**:

   -  Data from multiple files can be combined row-wise (if applicable),
      using **pandas** ``pd.concat()`` function, which ensures that the
      data from all files is placed into a single DataFrame for easier
      access and processing.

--------------

Example Usage Scenarios:
~~~~~~~~~~~~~~~~~~~~~~~~

1. **Scenario 1: Multiple Plates with Combined Data**: A biologist
   uploads multiple CSV files representing different plates from an
   experiment. They enable the “Add a column with filename” and “Add a
   column with plate number” options, then upload the files and merge
   them into a single DataFrame. This allows them to analyze the
   combined data across plates while keeping track of which rows came
   from which plate and file.

2. **Scenario 2: Separate DataFrames for Different Plates**: In another
   experiment, the biologist wants to keep each plate’s data separate
   for individual analysis. They upload multiple files and select the
   **Import as separate DataFrames** option. Each file is processed into
   its own DataFrame, which can be accessed individually in later steps.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Add Metadata Columns**: Provides flexibility for keeping track of
   file origins when working with multiple datasets.
-  **Merge or Separate DataFrames**: Offers the user control over how
   the data is processed — either combined into one DataFrame or kept as
   separate datasets.
-  **Custom Naming**: Allows users to easily label and access their
   datasets throughout the analysis pipeline.
