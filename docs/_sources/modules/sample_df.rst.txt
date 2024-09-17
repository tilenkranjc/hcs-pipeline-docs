Sampling
========

Overview:
^^^^^^^^^

The **Sampling Module** enables users to randomly sample a subset of
rows from a dataset. Sampling can be performed either as a fraction of
the total data or as a fixed number of rows. Additionally, users can opt
to sample within specific groups, making it a useful tool for stratified
or grouped data sampling.

--------------

Inputs and Options:
~~~~~~~~~~~~~~~~~~~

1. **DataFrame Selection**:

   -  **Selectbox**: The user selects the DataFrame they want to sample
      from.
   -  **Use Case**: This allows the user to specify which dataset to
      apply sampling to.

2. **Sampling Type**:

   -  **Radio Button**: The user chooses between:

      -  **Sample a Fraction**: A fraction of the total rows is sampled
         (e.g., 10% of the data).
      -  **Sample a Fixed Number of Rows**: A specific number of rows is
         sampled (e.g., 100 rows).

   -  **Use Case**: This gives the user flexibility to either get a
      percentage-based sample or a fixed sample size.

3. **Fraction of Rows to Sample**:

   -  **Slider**: When sampling a fraction of the data, the user selects
      the fraction to sample (between 1% and 100%).
   -  **Use Case**: This allows the user to choose the exact fraction of
      the dataset to sample.

4. **Number of Rows to Sample**:

   -  **Number Input**: When sampling a fixed number of rows, the user
      specifies how many rows they want to sample.
   -  **Use Case**: This allows for fixed-size sampling from the
      dataset.

5. **Group Sampling**:

   -  **Multiselect**: The user can select one or more columns to group
      by. When group sampling is enabled, rows are sampled independently
      within each group.
   -  **Use Case**: Group sampling ensures that samples are taken
      proportionally from each group, making it useful for stratified
      sampling or for maintaining a balanced representation of
      categories.

6. **Run Sampling**:

   -  **Button**: The user clicks this button to perform the sampling
      operation based on the selected options.

--------------

Computation Details:
~~~~~~~~~~~~~~~~~~~~

1. **Fraction Sampling**:

   -  When the user selects “Sample a Fraction,” the module randomly
      selects a subset of rows corresponding to the chosen fraction of
      the total dataset.

2. **Fixed Number Sampling**:

   -  When the user selects “Sample a Fixed Number of Rows,” the module
      randomly selects the specified number of rows from the dataset.

3. **Group Sampling**:

   -  If the user opts to sample within groups, the data is first split
      into groups based on the selected columns. Sampling is then
      performed independently within each group. If the group size is
      smaller than the number of rows requested, the module adjusts to
      sample the maximum available rows.

--------------

Recommendations for Use:
~~~~~~~~~~~~~~~~~~~~~~~~

-  **When to Use Fraction Sampling**:

   -  Use when you want to obtain a percentage of the dataset. This is
      useful when working with large datasets where analyzing the entire
      data would be time-consuming or unnecessary.
   -  For example, to quickly inspect 10% of a dataset, set the fraction
      to 0.1.

-  **When to Use Fixed Number Sampling**:

   -  Use when you need a fixed number of rows, regardless of the
      dataset’s size. This is useful when preparing datasets of
      consistent size for machine learning models or other analytical
      tools.

-  **When to Use Group Sampling**:

   -  Use when your data contains distinct groups (e.g., different
      experimental conditions or categories), and you want to ensure
      that each group is proportionally represented in the sample. This
      is particularly useful for maintaining the balance between classes
      in classification tasks or when analyzing specific subgroups in
      biological experiments.

--------------

Example Usage Scenario:
~~~~~~~~~~~~~~~~~~~~~~~

**Sampling from Grouped Experimental Data**: A biologist has collected
data from multiple plates in an experiment and wants to sample 20% of
the rows for a preliminary analysis. To ensure that each plate is
represented in the sample, they choose to group by the “Plate” column.
The module then samples 20% of rows from each plate, ensuring that the
sample includes a proportional representation of each plate’s data.
