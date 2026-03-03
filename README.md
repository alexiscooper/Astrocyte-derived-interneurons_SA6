# Dlx2 reprograms the transcriptome of astrocyte-derived interneurons and enforces canonical laminar positioning

## Project Description
This repository contains the full computational analysis pipeline for the study:
"Dlx2 reprograms the transcriptome of astrocyte-derived interneurons and enforces canonical laminar positioning."

Includes preprocessing, analysis, and figure generation for scRNA-seq and snRNA-seq datasets.

## Software Requirements
- Python 3.14.2
- R 4.4.1
- pip 23.3
- Required R and Python packages listed in requirements.txt, environment.yml, and R_packages.csv
- Tested on macOS 14 and Ubuntu 22.04

## Installation Instructions

### Clone repository
git clone https://github.com/alexiscooper/Astrocyte-derived-interneurons_SA6.git
cd stemcell_project

### Python virtualenv
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt

### Optional Conda environment
conda env create -f environment.yml
conda activate stemcell_project

### R packages
# See R_packages.csv for exact versions

## Sample and Library Preparation

### scRNA-seq
Brains collected at 4 dpi. Tissue dissociation using Miltenyi Adult Brain Dissociation Kit. Processed on gentleMACS Octo Dissociator.

### snRNA-seq
Brains collected at 2 and 4 wpi. Nuclei isolated following 10x Genomics "Nuclei Isolation from Adult Mouse Brain Tissue".

### FACS
Fluorophore-positive cells/nuclei sorted using BD FACSAria III.  
- 100 µm nozzle for cells  
- 70 µm nozzle for nuclei  

### Library Preparation
10x Chromium Controller/Chromium X using GEM-X Single Cell 3′ kits (v3/v4). Sequenced on Illumina NovaSeq X Plus / NovaSeq 6000. Cell Ranger v7–9.0.0 for alignment.

### Public datasets
Integrated P10/P28 interneuron datasets (GEO: GSE165233; GSM5014305, GSM501430739).

## Bioinformatic Analyses
- QC: Seurat, miQC, scDblFinder, mitochondrial & doublet filtering
- Data processing: PCA, clustering, UMAP embeddings, FindAllMarkers
- Module scores: AddModuleScore
- RNA velocity: Seurat → AnnData → Velocyto → scVelo
- Lineage analysis: Slingshot
- GO analysis: clusterProfiler

## Step-by-Step Reproduction
1. Download raw data to data/raw/
2. Preprocess: python scripts/01_preprocessing.py
3. Analysis: python scripts/02_analysis.py
4. Generate figures: python scripts/03_generate_figures.py

## Expected Outputs
- data/processed/ → normalized count matrices
- results/ → statistical tables
- figures/ → figures for manuscript

## R Packages
See R_packages.csv for exact versions used.

## License
MIT License (see LICENSE)

## Citation
See CITATION.cff for details.

## Code of Conduct
See CODE_OF_CONDUCT.md
