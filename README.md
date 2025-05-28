# Microsoft x IE University AI Capstone 2025

## 📌 Overview

This repository contains our submission for the **Microsoft Challenge for IE students**, part of the **AI Capstone 2025**. The challenge is framed around climate data innovation and monetization using a new dataset released via the Microsoft Planetary Computer.

We represent the innovation team of a renowned US-based climate laboratory tasked with exploring ways to generate business value from large-scale US climate data.

## 👥 Group Members
Nitin R Jangir | Massimo Tassinari | Louis-Esmel Kodo | Clara Sobejano | Yousef MohammadNoor J Joukhdar | Lucas Ihnen 

## 🌍 The Context

We were challenged to explore how to extract and utilize insights from a massive dataset of US climate measurements (since 1979, with over 12 billion data points from 800,000+ sensors). The dataset, curated by Microsoft, is designed for ease of access and use and provides a foundation for creating solutions, products, or services aimed at both public and private stakeholders.

> “You are the experts — define your own hypotheses, models, and customer focus.”  
> _– Microsoft & IE University Capstone Brief_:contentReference[oaicite:0]{index=0}

## 📊 Dataset: gridMET

- **Source**: [Microsoft Planetary Computer – gridMET](https://planetarycomputer.microsoft.com)
- **Data**: Surface meteorological data (1979–present)
- **Variables**: 12 (e.g., wind speed, precipitation, temperature)
- **Dimensions**:  
  - 15,341 time points  
  - 585 latitudes × 1,386 longitudes
- **Access**: STAC API via `planetary_computer` Python library

### 🔧 Suggested Libraries
```bash
pip install pystac-client planetary_computer numpy pandas xarray zarr adlfs
```

Or another alternative is installing directly from the `requirements.txt` file using the command:
```bash
pip install -r requirements.txt
```