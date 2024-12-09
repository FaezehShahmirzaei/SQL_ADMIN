Here’s a professional `README.md` file for your project, including the reason behind filtering and relevant resources.

---

# Cell Type Annotation in PBMCs Using scRNA-Seq Data

This project involves analyzing single-cell RNA sequencing (scRNA-seq) data from peripheral blood mononuclear cells (PBMCs) to identify and annotate distinct cell types. The pipeline includes data preprocessing, dimensionality reduction, clustering, and marker gene analysis to explore immune cell diversity.

---

## **Pipeline Overview**
1. **Data Preprocessing**: 
   - Load the dataset.
   - Perform quality control (QC) to filter out low-quality cells and genes based on specific thresholds.
   - Normalize and scale the data to prepare for further analysis.

2. **Dimensionality Reduction**:
   - Apply PCA to capture primary sources of variation.
   - Use UMAP and t-SNE for visualizing clusters.

3. **Clustering**:
   - Perform Leiden clustering to identify groups of similar cells.

4. **Marker Gene Analysis**:
   - Identify marker genes for each cluster using statistical tests.
   - Annotate clusters based on known immune cell markers.

5. **Visualization**:
   - Generate UMAP and t-SNE plots for cluster visualization.
   - Visualize QC metrics and marker genes.

---

## **Why Do We Filter Data?**

### **1. Removing Low-Quality Cells**
- **Reason**: Cells with low gene counts or abnormally high mitochondrial gene content often represent damaged or dying cells.
- **Thresholds**:
  - **Number of genes per cell**: Remove cells expressing fewer than 200 genes or more than 2500 genes. This removes debris and multiplets (doublets or triplets of cells).
  - **Percentage of mitochondrial reads**: Remove cells with >5% mitochondrial content as they may indicate dying cells.
- **Resource**: Luecken and Theis (2019). *Current best practices in single-cell RNA-seq analysis: A tutorial*. **Nature Protocols**.  
  ([Read Article](https://pubmed.ncbi.nlm.nih.gov/31217225/#:~:text=Mol%20Syst%20Biol.,doi%3A%2010.15252%2Fmsb.))  

### **2. Filtering Out Lowly Expressed Genes**
- **Reason**: Genes expressed in very few cells are often uninformative or represent noise in the data. These genes add computational overhead without contributing to biological insights.
- **Threshold**: Keep genes expressed in more than one cell.

---

## **Tools and Libraries Used**
- **Scanpy**: Python package for analyzing scRNA-seq data.
- **Matplotlib** and **Seaborn**: Visualization libraries.
- **YAML**: Configuration management.
- **Python**: Main programming language.

---

## **Pipeline Setup**

### **1. Requirements**
- Python (>=3.8)
- Scanpy
- Matplotlib
- Seaborn
- YAML

### **2. Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/username/pbmc-cell-type-annotation.git
   cd pbmc-cell-type-annotation
   ```
2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### **3. Run the Pipeline**
Execute the pipeline using the following command:
```bash
python main_pipeline.py
```

---

## **Directory Structure**

```
pbmc-cell-type-annotation/
├── main_pipeline.py             # Main script to run the pipeline
├── data_preprocessing.py        # Data preprocessing functions
├── dimensionality_reduction.py  # Dimensionality reduction functions
├── clustering_analysis.py       # Clustering functions
├── marker_gene_analysis.py      # Marker gene analysis functions
├── config.yaml                  # Configuration file
├── plots/                       # Directory for saving plots
└── README.md                    # Project documentation
```

---

## **Output**

### **Plots**
- **UMAP with Metrics**: Visualizes QC metrics on UMAP.
- **t-SNE with Metrics**: Visualizes QC metrics on t-SNE.
- **UMAP of Clusters**: Shows Leiden clusters.
- **Marker Gene Visualization**: Highlights top marker genes per cluster.

### **Annotated Clusters**
The final output includes an annotated dataset (`cell_type` field in `adata.obs`) with likely cell type identities for each cluster.

---

## **References**

1. Luecken, M. D., & Theis, F. J. (2019). *Current best practices in single-cell RNA-seq analysis: A tutorial*. **Nature Protocols**.  
   [DOI: 10.15252/msb.20188746](https://pubmed.ncbi.nlm.nih.gov/31217225/#:~:text=Mol%20Syst%20Biol.,doi%3A%2010.15252%2Fmsb.)

2. Wolf, F. A., Angerer, P., & Theis, F. J. (2018). *SCANPY: large-scale single-cell gene expression data analysis*. **Genome Biology**.  
   [DOI: 10.1186/s13059-017-1382-0](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-017-1382-0)

3. Stuart, T., et al. (2019). *Comprehensive integration of single-cell data*. **Cell**.  
   [DOI: 10.1016/j.cell.2019.05.031](https://doi.org/10.1016/j.cell.2019.05.031)

---

author : f.shahmirzaei@st.hanze.nl
