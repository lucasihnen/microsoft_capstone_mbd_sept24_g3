# IE University MBD 2025 Capstone - Microsoft Planetary Computer

## 👥 Group 3:  
**Group Members:** Nitin R Jangir | Massimo Tassinari | Louis-Esmel Kodo | Clara Sobejano | Yousef MohammadNoor J Joukhdar | Lucas Ihnen 

**Mentor**: Idafen Santana

## 🌍 Overview

This repository contains the deliverables and development work for the 2025 Capstone Project at IE University, in collaboration with Microsoft. The central challenge involves **monetizing US climate data**, specifically leveraging the gridMET dataset provided through the [Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/dataset/gridmet). 

Our task was to ideate and develop a **scalable, revenue-generating data product or service** based on open-access US meteorological data. The dataset includes over 12 billion data points from 800,000+ sensors, recording 12 variables like precipitation, temperature, and wind speed since 1979. 

The project emphasizes the development of solutions that are:

- **Technically sound** through data analysis and modeling  
- **Business-oriented** with monetization potential and clear ROI  
- **Scalable and maintainable**, suitable for real-world deployment  

We approached this challenge by exploring different hypotheses, analyzing the technical potential of the dataset, building a proof-of-concept model, and envisioning a production-level solution aligned with business impact goals.

## 🔭 Implementation Approach
We selected **Rochester, New York** as our initial focus to develop a proof of concept, thanks to its diverse climate conditions and city-level data granularity. This allowed us to validate our approach in a realistic and operationally relevant setting. Unless stated otherwise, all analyses, models, and results in this repository are based on the Rochester dataset. The code and methodology were designed to be scalable and reproducible for other regions, as further discussed in the report.

## 📊 Data Used on this project
### 🪐 Dataset: gridMET
- **Source**: [Microsoft Planetary Computer – gridMET](https://planetarycomputer.microsoft.com/dataset/gridmet)
- **Data**: Surface meteorological data (1979–2020)
- **Variables**: 12 (e.g., wind speed, precipitation, temperature)
- **Dimensions**:  
  - 15,341 time points  
  - 585 latitudes × 1,386 longitudes
- **Access**: STAC API via `planetary_computer` Python library

### 🦠 Dataset: FluView (FluSurv-NET)
- **Source**: [CDC FluView Interactive](https://gis.cdc.gov/GRASP/Fluview/FluHospRates.html)
- **Data**: Weekly, lab-confirmed influenza hospitalization rates
- **Variables**: Age group, virus type, population rates, location, week, race, gender, etc.
- **Dimensions**:  
  - Weekly data  
  - Multiple U.S. cities and states (city-level focus on Rochester, NY)
- **Access**: Manual download via FluView Interactive platform (CSV format)

## 🔧 Initial Setup
There are many libraries used for this project, from Machine Learning frameworks to libraries required for properly handling the Planetary Data gridMET dataset. You can install them directly from the [`requirements.txt`](requirements.txt) file using the command:
```bash
pip install -r requirements.txt
```

## 📁 Repository Structure
```bash
microsoft_capstone_mbd_sept24_g3/ 
├── deliverables/ # Folder with all the formal deliverables for the Capstone Project!
├── data/ # Supporting data for the main notebooks
│ ├── gridmet.csv
│ ├── rochester.csv
│ ├── california gridmet.csv
│ ├── california.csv
│ └── others/ # Deprecated dataset extractions 
├── 1_gridmet_polygon_extraction.ipynb
├── 2_eda.ipynb
├── 3_model.ipynb
├── other_regions/ # To showcase reusability of the notebook on another region
│ ├── 1_gridmet_polygon_extraction_california.ipynb
│ ├── 2_eda_california.ipynb
│ └── 3_model_california.ipynb
├── README.md 
└── requirements.txt
```

## 🚢 How to Navigate the Files

This repository is designed as a **modular and reproducible workflow**, enabling users to adapt the pipeline to different regions, time periods, or modeling targets with minimal adjustments.

The core workflow is organized into **three sequential Jupyter Notebooks**, which should be executed in the following order:

1. `gridmet_polygon_extraction.ipynb`
2. `eda.ipynb`  
3. `model.ipynb`

These notebooks walk you through the full process of working with the **gridMET climate data**, from spatial extraction and preprocessing, through exploratory data analysis, to model training and evaluation.

Each of these files and notebooks were created as **self-contained files**, meaning that each of them have multiple visualizations/graphs as well as detailed explanations of the various insights we obtained through this project.

In the next section, we break down the purpose and content of each notebook.

---

### 📍 `gridmet_polygon_extraction.ipynb`
🔗 [`/1_gridmet_polygon_extraction.ipynb`](./1_gridmet_polygon_extraction.ipynb)

This notebook is the entry point for working with the gridMET dataset. It focuses on extracting climate data for a specified geographic region by selecting a polygon (e.g., a city or state) and slicing the corresponding spatiotemporal data from the full dataset. It leverages the STAC API from Microsoft Planetary Computer and makes use of libraries like `xarray`, `zarr`, and `pystac-client`.

The extracted data is stored in the folder [`data/`](./data/) as a standardized CSV/Parquet format, ready for downstream analysis. This modular approach allows the same pipeline to be reused for different regions with minimal changes.  

**Note: For the FluView dataset, there is no programmatic integration, so the extraction must be done manually from the [CDC FluView Interactive](https://gis.cdc.gov/GRASP/Fluview/FluHospRates.html) webpage.**

### 📊 `2_eda.ipynb`
🔗 [`/2_eda.ipynb`](./2_eda.ipynb)

This notebook performs exploratory data analysis (EDA) on the climate and health dataset extracted in the previous step. It generates descriptive statistics, visualizations, and correlation checks to uncover patterns and relationships between environmental variables and hospitalization rates.

By default, it uses the output from the Rochester extraction, but with a simple change to the dataset name or file path, the same EDA can be reproduced for any other region or timeframe. This flexibility ensures consistency in exploration while supporting scalable experimentation.  

### 🤖 `3_model.ipynb`
🔗 [`/3_model.ipynb`](./3_model.ipynb)

This notebook builds and evaluates a predictive model that estimates virus-related hospitalization rates based on environmental factors. It uses the same dataset from the EDA step, applies feature engineering, and fits a regression model to forecast weekly hospitalization trends.

The pipeline is structured to support quick swaps of input data, enabling the same modeling approach to be applied across different regions or time periods. Evaluation metrics and visual outputs are included to assess performance and guide further iterations.  

## ♻️ Scalability & Reusability

While all primary findings, evaluations, and insights presented in the core notebooks are based on the **Rochester** dataset, this pipeline was intentionally designed to be scalable and reusable across other regions. To demonstrate this, we replicated the full workflow for the **California** region by simply changing the input data.

Supporting notebooks for the California use case can be found in the [`/other_regions/`](./other_regions/) folder, while the associated datasets are stored in the [`/data/`](./data/) directory. This modular design allows for rapid adaptation to new geographies with minimal configuration effort.

## ⚖️ Ethics Statement

This project is the result of original work conducted in full alignment with **IE University’s academic integrity guidelines**. We prioritized transparency, fairness, and reproducibility at every stage of the process. All data used is **publicly available**, primarily sourced from the **Microsoft Planetary Computer (gridMET)** and the **CDC FluView platform**, and all collaborators and sources have been duly acknowledged.

