Load Platemap
=============

Overview:
^^^^^^^^^

The **Load Platemap Module** allows users to upload and process Excel
files containing plate maps, where each sheet in the Excel file
represents a different type of metadata. This module extracts the plate
metadata, including well locations, and combines it into a single
DataFrame, which can be used for downstream analysis.

Purpose:
^^^^^^^^

This module is designed to handle metadata from multiple Excel sheets,
often used in high-throughput screening experiments where plate maps
define the location of treatments, controls, or other metadata across
wells. The resulting DataFrame consolidates all metadata from the
uploaded files, making it easier to merge with experimental data.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **File Upload**:

   -  **File Uploader**: The user can upload one or more Excel files
      (``.xlsx``). Each file represents one plate, and the sheets within
      each file contain different types of metadata.
   -  **Use Case**: Useful for uploading and processing metadata
      associated with plates in high-content screening or similar
      experiments.

2. **Dataset Name**:

   -  **Text Input**: The user provides a name for the dataset, which is
      used to label and store the processed DataFrame for later use in
      the data pipeline.
   -  **Use Case**: The dataset name helps in identifying the results of
      the plate map processing within the workflow.

3. **Button: Process Files**:

   -  **Functionality**: Clicking this button processes the uploaded
      Excel files and generates a combined metadata DataFrame that
      includes information from all plates and sheets.
   -  **Use Case**: This option triggers the extraction and merging of
      metadata from the uploaded Excel files.

--------------

Data Handling:
~~~~~~~~~~~~~~

1. **Processing Each Excel File**:

   -  For each uploaded Excel file, the module processes all sheets,
      assuming each sheet contains metadata for the corresponding plate.
   -  The first column in each sheet represents the row numbers, while
      the remaining columns represent the metadata values for each well.

2. **Row and Column Extraction**:

   -  The module extracts the row and column information from each sheet
      and uses them to determine the well locations in the format
      ``Well``, such as ``A01`` or ``B05``.
   -  It also combines this well information with the metadata provided
      in each sheet, allowing the module to track which metadata belongs
      to which well.

3. **Merging Data from Multiple Sheets**:

   -  The metadata from each sheet in an Excel file is merged together
      on the columns ``Row``, ``Column``, and ``Well``. This ensures
      that metadata from different sheets is linked to the correct well
      for each plate.

4. **Plate and Filename Information**:

   -  The module adds a ``plate`` column to distinguish data from
      different plates, and a ``filename`` column to track the source of
      each plate’s metadata.

5. **Final Metadata DataFrame**:

   -  After processing all the uploaded files, the module concatenates
      the metadata from each plate into a single DataFrame, which is
      then saved for further analysis in the pipeline.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Uploading and Processing Plate Maps for High-Content Screening**: A
biologist has conducted an experiment using multiple plates, each
containing different treatments and controls. The metadata for these
plates, such as treatment type, concentration, and well locations, is
stored in multiple Excel files where each sheet represents different
types of metadata. Using this module, the biologist uploads the Excel
files, processes the plate maps, and generates a consolidated metadata
DataFrame. This DataFrame is then used to analyze the experimental data
based on the treatment and well information.

--------------

Options and Flexibility:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **Multiple Files and Sheets**: The module handles multiple Excel
   files, each containing several metadata sheets, making it ideal for
   large experiments involving multiple plates.
-  **Customizable Well Mapping**: The module automatically generates
   well identifiers (``Well``) in the format of letter-number
   combinations (e.g., ``A01``, ``B02``), providing a clear mapping of
   rows and columns to the well locations.
-  **Merging Metadata from Multiple Sheets**: Metadata from different
   sheets is merged on ``Row``, ``Column``, and ``Well``, ensuring that
   all relevant information for each well is combined.

--------------

Notes:
~~~~~~

-  **Excel File Structure**: The module assumes that each sheet in the
   Excel file contains well-specific metadata, with rows representing
   the well positions and columns containing metadata values.
-  **Consistent Well Naming**: The row and column labels must be
   consistent across sheets to ensure accurate merging of metadata.
