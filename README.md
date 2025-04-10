# spatial-transcriptomics-pipeline
# Author :Muralidharan Mani 
# Affiliation: University of Wisconsin-Madison
An R pipeline for processing and analyzing spatial transcriptomics data, including setup, data loading, QC, preprocessing, visualization, and spatial analysis.
## Overview

This repository contains an R script (`spatial_script_trans.R` - **use any name you wish R file**) that provides a comprehensive workflow for the analysis of spatial transcriptomics data. It covers essential steps from installing necessary packages and loading data (specifically for 10x Visium data) to advanced spatial analysis techniques like identifying spatially variable genes and spatial domains.

The pipeline utilizes popular R packages such as:

* **Seurat:** For single-cell and spatial data analysis.
* **STutility:** Enhances spatial data handling within Seurat.
* **ggplot2:** For creating high-quality plots.
* **patchwork:** For combining multiple plots.
* **dplyr:** For data manipulation.
* **viridis:** For perceptually uniform color maps.
* **spdep:** For spatial dependence analysis.

## Getting Started

### Prerequisites

* **R:** Ensure you have R (version 4.0 or higher is recommended) installed on your system. You can download it from [https://www.r-project.org/](https://www.r-project.org/).
* **BiocManager:** Install BiocManager if you don't have it already:
    ```R
    if (!requireNamespace("BiocManager", quietly = TRUE))
        install.packages("BiocManager")
    ```

### Installation

1.  **Clone the repository (optional):** If you have this script in a GitHub repository, you can clone it to your local machine:
    ```bash
    git clone [https://github.com/your-username/spatial-transcriptomics-pipeline.git](https://github.com/your-username/spatial-transcriptomics-pipeline.git)
    cd spatial-transcriptomics-pipeline
    ```
    (Replace `your-username/spatial-transcriptomics-pipeline` with the actual repository URL.)

2.  **Save the R script:** Make sure the R script (`your_script_name.R`) is in your working directory or a specified location.

### Usage

1.  **Open R or RStudio.**

2.  **Set your working directory** to the location of the R script and your data:
    ```R
    setwd("path/to/your/working/directory") # Replace with your actual path
    ```

3.  **Run the R script:**
    ```R
    source("your_script_name.R") # Replace with the actual name of your R file
    ```

4.  **Follow the prompts and ensure your data paths are correctly specified within the script.** The script is designed to guide you through the analysis steps.

## Data Input

The script supports loading spatial transcriptomics data in two ways:

* **Option A: Loading 10x Visium Data:** Specify the path to the Space Ranger output directory.
* **Option B: Loading Multiple Samples:** Provide a data frame (`infoTable`) with paths to the tissue positions list, low-resolution image, and scale factors JSON file for each sample.

**Make sure to update the `data_dir` variable (for Option A) or the `infoTable` (for Option B) within the script with the correct paths to your data.**

## Output

The script generates various outputs, including:

* **Plots:**
    * QC metric visualizations (violin plots).
    * UMAP and spatial UMAP plots of clusters.
    * Spatial feature plots showing gene expression.
    * Spatial plots of spatially variable genes (Moran's I).
    * Spatial plots of spatially autocorrelated genes (Moran's I).
    * (If enabled) Spatial plots of predicted cell types (from single-cell integration).
    * Spatial plots of identified spatial domains.
    * All spatial plots are saved to a single PDF file (`spatial_plots.pdf`).
* **Data Files:**
    * A processed Seurat object (`processed_spatial_transcriptomics.rds`).
    * A CSV file containing marker genes for identified spatial domains (`spatial_domain_markers.csv`).

## Script Structure

The R script is organized into the following sections:

1.  **Setup and Installation:** Installs and loads necessary R packages.
2.  **Data Loading:** Functions to load 10x Visium data (single or multiple samples).
3.  **Quality Control and Preprocessing:** Filters data based on QC metrics, normalizes, finds variable features, and scales the data.
4.  **Dimensionality Reduction and Clustering:** Performs PCA, UMAP, t-SNE, and clustering.
5.  **Spatial Visualization:** Generates spatial plots of gene expression and clusters.
6.  **Spatial Analysis:** Identifies spatially variable genes and performs spatial autocorrelation analysis using Moran's I.
7.  **(Optional)** **Integration with Single-Cell Data:** Allows integration with a reference single-cell dataset to transfer cell type labels.
8.  **Advanced Analysis: Spatial Domains:** Identifies and visualizes spatially distinct domains within the tissue.
9.  **Saving Results:** Saves the processed Seurat object, marker genes, and spatial plots.

## Customization

You can customize various parameters within the script, including:

* **QC thresholds:** Adjust the filtering criteria for the number of features and mitochondrial percentage.
* **Number of variable features:** Change the number of genes used for dimensionality reduction.
* **Number of principal components (PCs):** Modify the number of PCs used for UMAP, t-SNE, and clustering.
* **Clustering resolution:** Adjust the granularity of the clusters.
* **Genes of interest:** Specify the genes to visualize spatially.
* **Parameters for spatial analysis:** Modify the number of neighbors for Moran's I calculation and the number of top spatially variable genes to display.
* **Integration settings:** If performing single-cell integration, update the path to your reference dataset and adjust integration parameters.
* **Spatial domain analysis parameters:** Change the resolution and dimensionality for spatial domain identification.

**Review the comments within the script to understand the purpose of each parameter and modify them according to your specific dataset and analysis goals.**

## Contributing

Contributions to this pipeline are welcome! If you have suggestions for improvements, bug fixes, or new features, please feel free to submit a pull request or open an issue on this repository.

## License

MIT 

## Contact

mmani3@wisc.edu
