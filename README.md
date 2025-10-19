# 🌍 Air Pollution Modeling in Mashhad using Google Earth Engine (GEE)

This repository contains a **Google Earth Engine (GEE)** JavaScript script for modeling the **spatial distribution** of key air pollutants—**CO**, **SO₂**, **NO₂**, and **HCHO**—in **Mashhad County, Iran**.

The workflow integrates **multi-source satellite data** from **Sentinel-2**, **Landsat-9**, **MODIS**, and **Sentinel-5P**, along with auxiliary datasets such as elevation, weather variables, population density, and proximity to industrial centers.

The script uses a **Random Forest algorithm** to:

* Preprocess and filter cloud cover in satellite images
* Compute spectral indices such as **NDVI** and **SAVI**
* Downscale **land surface temperature (LST)** using regression methods
* Train separate Random Forest models for each pollutant

Models are validated using a **70/30 train-test split**, achieving R² values between 0.81 to 0.98, along with **MAE** and **RMSE** metrics, demonstrating robust performance in estimating spatial pollutant patterns.

The workflow **exports maps and predictor layers to Google Drive**, offering a **scalable and cost-effective solution** for **air quality assessment** in regions with limited ground-based monitoring.

---

## 🔍 Overview

This script provides an **end-to-end workflow** for air quality modeling, addressing gaps in ground-based measurements by leveraging satellite-derived data.
By combining **data preprocessing**, **machine learning**, and **validation techniques**, the workflow produces **high-resolution pollutant distribution maps** to support **environmental policy** and **urban planning** in Mashhad—a city with ~3.4 million residents (2024) and significant industrial activity.

---

## 🛠 Requirements

* **Google Earth Engine Account**
  Register at [earthengine.google.com](https://earthengine.google.com) and authenticate:

  ```js
  ee.Authenticate();
  ```

* **JavaScript Basics** – familiarity with GEE scripting is recommended

* **Assets** – upload or import:

  * AOI geometry (Mashhad boundary)
  * Training datasets (`FeatureCollections` V, W, S, I, I5)
  * Industrial center tables (`table1–13`)

---

## 📋 Installation & Usage

### 1. Clone the Repository

```bash
git clone https://github.com/arminnakhjiri/air-quality-model.git
cd air-quality-model
```

### 2. Open in GEE Code Editor

* Copy `main.js` into the [GEE Code Editor](https://code.earthengine.google.com).
* Update placeholders (`aoi`, `table1–13`) with your asset IDs.

### 3. Run the Workflow

Sequential steps:

1. **Data loading**
2. **Preprocessing & feature computation**
3. **Model training & prediction**

Visualize results with:

```js
Map.addLayer();
```

Export outputs to Google Drive:

```js
Export.image.toDrive();
```

---

## 🌱 Key Features

* Complete **data preprocessing, model training, and validation**
* **Cloud masking** and **spectral index computation**
* **LST downscaling** and pollutant concentration prediction
* **Scalable** to other urban areas with minimal adjustments

---

## 📌 Notes

* Modify **AOI**, **date ranges**, or **bands** for other regions or periods
* High **R² values** indicate strong model performance; additional **ground truth data** can improve validation
* Although optimized for **Mashhad**, the workflow is adaptable to **other cities or countries**

---

## 🧑‍🏫 Author

**Armin Nakhjiri**
📧 [Nakhjiri.Armin@gmail.com](mailto:Nakhjiri.Armin@gmail.com)
