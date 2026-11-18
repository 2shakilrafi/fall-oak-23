# Self-Organizing Maps of Chicago Ride-Share Trips

Code and slides for a talk given at the Fall 2023 OAK Supercomputing Conference in Little Rock, Arkansas, titled "SOM-where in Chicago." The talk applies self-organizing maps (SOMs) to ride-share pickup data to find groups of Chicago census tracts with similar travel patterns.

## Background

A self-organizing map, or Kohonen map, is a small neural network used for dimensionality reduction and clustering. A lattice of nodes, each carrying a weight vector, is trained by repeatedly picking a data point, finding the closest node, and pulling that node and its lattice neighbors toward the point. The result is a low-dimensional map that preserves neighborhood structure in the data. The slides (`oak-presentation.pdf`) cover the algorithm, the choice of lattice, weight initialization, and the quantization and topographic error measures.

## Data

- Uber and Lyft trip records for Chicago, aggregated to census tracts: pickup counts, trip miles, and trip seconds.
- Demographic and built-environment variables per tract, including median income, the share of households without a car, and distance to the nearest transit stop. The built-environment variables come from the EPA Smart Location Database.
- Census tract boundaries (`shapes.geojson`).

The processed tract-level tables are included as CSV files (`main-data.csv`, `main-df.csv`, `built-environment-demographics.csv`, `trip-info.csv`, `X-with-cluster.csv`). The raw trip file is not.

## Contents

| File | Purpose |
|---|---|
| `ARNA_SHAKIL_FINAL_CODE.ipynb` | Reduces the raw trip file (`tdata.csv`) to pickup tract, trip miles, and trip seconds (`geoid-miles-seconds.csv`) |
| `OAK-Fall-2023.ipynb`, `OAK-Fall-2023-2.ipynb` | Pickup choropleth maps, the merged tract-level table, and the SOM analysis |
| `mapping.ipynb` | Maps the cluster assignments back onto Chicago |
| `oak-presentation.tex`, `oak-presentation.pdf` | Slides (LaTeX/Beamer) |
| `OralsPresentation.tex`, `OAK_FALL_23_themed.pdf` | Earlier themed version of the talk |
| `*.png` | Figures used in the slides |

## Running it

Use Python with `pandas`, `geopandas`, `folium`, `numpy`, `scikit-learn`, `matplotlib`, and `pyarrow`. The notebooks expect the CSV files to be in the working directory. `ARNA_SHAKIL_FINAL_CODE.ipynb` starts from the full raw trip file (`tdata.csv`), which is large and not included. `OAK-Fall-2023.ipynb` reads its output, `geoid-miles-seconds.csv`, which is also not included, so rerunning the full analysis requires the raw Chicago trip data.

## Authors

Shakil Rafi and Arna Nishita Nithila, University of Arkansas.
