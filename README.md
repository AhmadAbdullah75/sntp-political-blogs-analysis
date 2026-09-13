# SE4095 Assignment 1 - Political Blogs Network Analysis

## Overview
This project analyzes the Political Blogs Network (Adamic & Glance, 2005) using
centrality measures (PageRank, Betweenness Centrality) and community detection
(Louvain modularity maximization) to investigate whether hyperlink structure
recovers known political orientations.

## Requirements
- Python 3.12+
- See requirements.txt for exact package versions

## Setup Instructions
1. Create a virtual environment:

python -m venv .venv

2. Activate it:
   - Windows: `.venv\Scripts\activate`
   - Mac/Linux: `source .venv/bin/activate`
3. Install dependencies:

pip install -r requirements.txt

4. Register the Jupyter kernel:

python -m ipykernel install --user --name=sntp-assignment1

5. Place the dataset file `polblogs.gml` in `data/raw/` (already included in this
   submission if required by the course; otherwise download from
   https://public.websites.umich.edu/~mejn/netdata/)

## Running the Analysis
Open `notebooks/01_analysis.ipynb` in Jupyter and select the `sntp-assignment1` kernel,
then run all cells top to bottom:

jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.kernel_name=sntp-assignment1 notebooks/01_analysis.ipynb


Or open interactively:

jupyter notebook notebooks/01_analysis.ipynb


## Project Structure

./
.gitignore
progress.md
README.md
requirements.txt
data/
processed/
analysis_graph.graphml
targeted_graph.graphml
random_graph.graphml
raw/
polblogs.gml
notebooks/
01_analysis.ipynb
reports/
figures/
community_size_distribution.png
community_visualization.png
degree_distribution.png
network_visualization.png


## Outputs
- `reports/figures/degree_distribution.png` — In-degree and out-degree distribution plots for the original analysis graph
- `reports/figures/network_visualization.png` — Top 150 blogs by degree colored by political orientation (0=liberal/blue, 1=conservative/red)
- `reports/figures/community_visualization.png` — Top blogs colored by Louvain-detected community (seed 42)
- `reports/figures/community_size_distribution.png` — Full community size distribution (all detected communities, log scale) for the original, targeted-removal, and random-removal graphs
- `data/processed/analysis_graph.graphml`, `targeted_graph.graphml`, `random_graph.graphml` — Cleaned/derived graphs exported for reproducibility, since preprocessing and node removal change the supplied dataset
- All numerical results (centrality rankings, experiment comparisons, community metrics, evaluation metrics) are printed inline in the notebook outputs

## Random Seeds
A fixed `RANDOM_SEED = 42` is used throughout for reproducibility, with seeds
`[42, 43, 44, 45, 46]` used for the 5-run Louvain community detection stability check.