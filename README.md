# Hyperspectral Analysis Pipeline (EMIT)
A Python pipeline for exploring, reducing, and clustering an EMIT hyperspectral image cube (Southern India). The workflow covers spectral visualization, scatter plots, PCA, t-SNE, and K-Means classification.

# Setup & Requirements
Environment: Kaggle Notebook

Dataset: Add EMIT_60233 via Add Input on Kaggle.

Dependency: Run !pip install -q anywidget (for interactive plots).

# Pipeline Steps
Data Loading: Reads EMIT NetCDF reflectance files and extracts wavelength metadata (~381–2493 nm).

Image Composites:

TCC (True Color): Red (650nm), Green (560nm), Blue (470nm).

FCC (Vegetation): NIR (860nm), Red (650nm), Green (560nm).

Scatter Plots: 2D and 3D spectral feature spaces (e.g., Red vs. NIR vs. SWIR) to identify material clusters.

Dimensionality Reduction:

PCA: Reduces 255 bands to essential components (elbow).

t-SNE: Compares perplexity = 10, 30, 50 on a 20,000-pixel subset to prevent memory crashes. Final T is calculated on the full dataset using perplexity = 30.

Unsupervised Classification: Applies K-Means clustering to the PCA-reduced data and reshapes the labels back into a 2D spatial classification map.
