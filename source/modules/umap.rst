UMAP Projection
===============

Module Overview:
^^^^^^^^^^^^^^^^

The **UMAP Projection Module** provides a way to reduce high-dimensional
data into a lower-dimensional space (typically 2D or 3D) using the
**UMAP** (Uniform Manifold Approximation and Projection) algorithm. This
dimensionality reduction technique is particularly useful for
visualizing the structure of high-dimensional data while retaining the
important relationships between data points.

This module allows users to project complex datasets, such as biological
or imaging data, into two dimensions, making it easier to identify
clusters, patterns, and relationships in the data.

--------------

Inputs:
^^^^^^^

1. **Data DataFrame Selection**:

   -  Users must select a DataFrame from the available pipeline results.
      This DataFrame contains the high-dimensional data that will be
      projected into lower dimensions using UMAP.

2. **Metadata Columns Selection**:

   -  Metadata columns help identify non-data-related information (e.g.,
      sample labels, experimental conditions). You can select the
      metadata columns that you do not want to include in the UMAP
      projection. These columns will remain available after UMAP
      processing and will be useful for labeling and interpreting the
      results.
   -  The remaining columns (data columns) will be used as input for
      UMAP.

3. **UMAP Parameters**:

   -  **Number of Neighbors (``n_neighbors``)**:

      -  This parameter controls how UMAP balances between preserving
         local and global structure.
      -  A lower value focuses on local relationships, capturing small
         clusters of similar points.
      -  A higher value emphasizes global structure, maintaining
         relationships between more distant points.
      -  Default: 15

   -  **Minimum Distance (``min_dist``)**:

      -  This parameter influences how tightly UMAP clusters points in
         the reduced space.
      -  A smaller value results in denser clusters (more compact),
         while a larger value leads to more spread-out clusters.
      -  Default: 0.1

4. **Run UMAP**:

   -  Once the desired settings are chosen, clicking the **Run UMAP**
      button will apply the UMAP algorithm to the selected data columns,
      producing a 2D projection.

--------------

Computation:
^^^^^^^^^^^^

**UMAP** works by constructing a graph of the high-dimensional data
based on distances between points, then mapping that graph to a
lower-dimensional space.

The primary UMAP parameters are: - **``n_neighbors``**: Determines how
UMAP weighs local vs. global structure. Small values capture local
neighborhood relationships, while larger values capture broader
structure across the dataset. - **``min_dist``**: Controls how far apart
points can be in the low-dimensional space. Small values create more
compact clusters, while large values lead to more evenly distributed
data points.

After running UMAP, the result is a 2D (or 3D) projection of the data,
preserving much of the local structure from the original dataset while
reducing its complexity.

--------------

Outputs:
^^^^^^^^

1. **UMAP Embeddings**:

   -  After running the UMAP algorithm, the module produces a DataFrame
      containing the UMAP coordinates (``UMAP-1``, ``UMAP-2``) for each
      data point.
   -  This DataFrame also includes the metadata columns selected
      earlier, making it easier to interpret and label the points based
      on metadata.

2. **Pipeline Results**:

   -  The final UMAP DataFrame (containing both the UMAP embeddings and
      the metadata columns) is saved in the session state, allowing the
      user to visualize or process the embeddings in subsequent modules.

--------------

Recommendations for Use:
^^^^^^^^^^^^^^^^^^^^^^^^

-  **Small clusters or distinct groups**: Set a **lower
   ``n_neighbors``** value (e.g., 5-10) and a **lower ``min_dist``**
   (e.g., 0.1). This will emphasize capturing tight, small groups of
   similar data points.
-  **Smoother, broader distributions**: Set a **higher ``n_neighbors``**
   value (e.g., 30-50) and a **higher ``min_dist``** (e.g., 0.5). This
   will prioritize capturing a broader structure of the data, spreading
   out the clusters.
-  **Exploring structure**: Start with the default values and adjust
   based on the dataset’s complexity and the observed patterns in the
   projection.

--------------

Interpretation of UMAP Results:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. **Local vs. Global Relationships**:

   -  UMAP is designed to prioritize local relationships, so nearby
      points in the original high-dimensional space should remain close
      in the UMAP projection.
   -  However, global relationships (points that are far apart in the
      original space) may not always be preserved accurately in the UMAP
      projection.

2. **Cluster Identification**:

   -  The UMAP projection often highlights natural groupings in the
      data. These clusters can correspond to meaningful biological
      phenomena, such as different cell types, treatment groups, or
      experimental conditions.

3. **Limitations**:

   -  Although UMAP preserves local structure well, distances between
      points in the projection do not always correspond to their true
      distances in the original space. The projection is mainly intended
      for visualization and understanding patterns, not for exact
      distance-based analysis.

By using UMAP, you can gain a better understanding of how your data is
structured, detect hidden patterns, and explore relationships between
points in a way that’s easy to visualize and interpret.
