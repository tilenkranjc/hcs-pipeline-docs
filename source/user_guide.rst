User Guide for HCS Pipeline App
===============================

This guide will help you understand how to use the HCS Pipeline App, a
modular data analysis platform designed for high-content screening (HCS)
workflows. With this app, you can create custom pipelines, process data
using various modules, and visualize results interactively.

--------------

Step-by-Step Guide
------------------

1. **App Interface Overview**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The app consists of two main sections: - **Sidebar**: Here, you can
manage the pipeline by adding, removing, and reordering analysis
modules. You can also save or load pipelines. - **Main Area**: This is
where the modules you select are displayed. Each module performs a
specific data processing task and may provide visualizations.

--------------

2. **Starting a Pipeline**
~~~~~~~~~~~~~~~~~~~~~~~~~~

Add Modules to the Pipeline:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Add Module**:

   -  In the sidebar, click the **“+” (Add)** button to open a dialog
      for adding modules.
   -  A list of available modules will appear. Select the module you’d
      like to add and confirm.
   -  The selected module will be added to your pipeline, and it will
      appear in the **Main Area**.

Removing a Module:
^^^^^^^^^^^^^^^^^^

1. **Delete Module**:

   -  Select the module you want to remove by clicking its name in the
      sidebar.
   -  Then, click the **“-” (Remove)** button to delete it from the
      pipeline.

Reordering Modules:
^^^^^^^^^^^^^^^^^^^

1. **Move Module Up or Down**:

   -  Select the module you want to move in the pipeline.
   -  Use the **Up** or **Down** arrow buttons in the sidebar to reorder
      the module’s position.

--------------

3. **Working with Modules**
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each module in the app performs a specific data analysis or processing
task. After adding a module to the pipeline, follow these steps:

Configure the Module:
^^^^^^^^^^^^^^^^^^^^^

1. **Module Interface**:

   -  The module interface will appear in the **Main Area** after you
      select it from the sidebar.
   -  Each module has its own set of inputs, such as file upload
      options, data column selectors, or parameter sliders.

2. **Running the Module**:

   -  Once you’ve configured the module’s settings, click the **Run**
      button (or equivalent) to process the data.
   -  The module will display output such as filtered or modified data,
      computed results, or visualizations.

Viewing Processed Data:
^^^^^^^^^^^^^^^^^^^^^^^

-  **Data View Section**: After running the module, you can view the
   resulting DataFrame by navigating to the **Data View** section within
   the module. This shows the processed data for review or further
   processing in subsequent modules.

Viewing Visualizations:
^^^^^^^^^^^^^^^^^^^^^^^

-  **Visualization Section**: If the module provides any visualization
   (e.g., plots or heatmaps), it will be displayed in the
   **Visualization** section of the module.

--------------

4. **Saving and Loading Pipelines**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Save the Pipeline:
^^^^^^^^^^^^^^^^^^

1. **Download Pipeline**:

   -  After configuring the modules and running your analysis, you may
      want to save the pipeline for future use.
   -  Click the **“Save pipeline”** button in the sidebar. This will
      download a JSON file representing the current pipeline
      configuration.

Load a Pipeline:
^^^^^^^^^^^^^^^^

1. **Load from JSON**:

   -  If you have a saved pipeline JSON file, click the **“Load
      pipeline”** button in the sidebar.
   -  This will open a dialog to upload a pipeline file. Once uploaded,
      the app will rebuild the pipeline as it was saved, allowing you to
      continue or rerun your analysis.

--------------

Use Cases:
----------

1. **Creating a New Pipeline**:

   -  Start by adding the necessary modules for your data analysis
      workflow.
   -  For example, you can start with a **data upload** module, followed
      by **data quality filtering**, and finally a **visualization
      module** such as an interactive scatter plot or heatmap.

2. **Saving and Sharing Pipelines**:

   -  Once you create a pipeline, you can save it and share the JSON
      file with colleagues. They can load the pipeline and run the same
      analysis on their own data.

3. **Loading a Pipeline for Reproducibility**:

   -  If you need to reproduce an analysis or resume a workflow, simply
      load the saved pipeline file. The app will restore the entire
      pipeline configuration, including the selected modules and
      parameters.

--------------

Recommendations:
----------------

-  **Modular Design**: The modular design of the app allows you to
   combine any number of different processing steps. You can mix and
   match modules according to your needs.

-  **Run Intermediate Steps**: You can run individual modules as part of
   the pipeline and view intermediate data results. This is useful for
   debugging or refining analysis before proceeding to later steps.

-  **Reorder Modules**: Depending on the complexity of your analysis,
   you may need to reorder modules for the desired result. For example,
   normalization might need to occur before feature selection.

--------------

Common Operations:
------------------

1. **Data Upload**:

   -  Start by adding a module that allows you to upload your dataset.

2. **Data Processing**:

   -  Add modules such as **Data Quality Filtering**, **Normalization**,
      **Remove Outliers**, etc., to clean and process your data.

3. **Visualization**:

   -  Add visualization modules like **Interactive Scatter Plot**,
      **UMAP Projection**, or **Heatmaps** to explore patterns in your
      data.

--------------

This guide outlines how to create, manage, and execute analysis
pipelines using the HCS Pipeline App. The flexible and modular design
allows users to easily build, modify, and save complex data processing
workflows tailored to specific datasets and analysis needs.
