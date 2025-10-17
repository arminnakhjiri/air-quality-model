# 🌍 Air Pollution Modeling Google Earth Engine (GEE)

This repository contains a **Google Earth Engine (GEE)** JavaScript script designed for modeling the **spatial distribution** of major air pollutants—**carbon monoxide (CO)**, **sulfur dioxide (SO₂)**, **nitrogen dioxide (NO₂)**, and **formaldehyde (HCHO)**—in **Mashhad County, Iran**.

The workflow integrates **multi-source remote sensing data** from **Sentinel-1**, **Sentinel-2**, **Landsat-9**, **MODIS**, and **Sentinel-5P**, along with auxiliary datasets such as elevation, weather parameters, population density, and industrial proximity.

Using the **Random Forest algorithm**, the script:

* Filters cloud cover
* Computes spectral indices (e.g., **NDVI**, **SAVI**)
* Downscales **land surface temperature (LST)** via linear regression
* Achieves a **99.9% accurate land cover classification**

Separate Random Forest models are trained for each pollutant, validated with a **70/30 train-test split**, achieving **R² values from 0.81 (SO₂)** to **0.98 (CO)**, along with **MAE** and **RMSE** metrics.

Fully executable in GEE, the workflow **exports classified maps and stacked predictor images to Google Drive**, offering a **cost-effective, scalable solution** for **air quality assessment** in **data-scarce regions** like Mashhad.

---

## 🔍 Overview

This script provides an **end-to-end environmental monitoring solution**, addressing the lack of ground-based measurements by leveraging satellite-derived insights.
By combining **advanced data processing**, **machine learning**, and **validation techniques**, it delivers **actionable pollutant distribution maps** that support **environmental policy** and **urban planning** in Mashhad—a city with ~3.4 million residents (2024) and substantial industrial activity [WMO, 2024].

---

## 🛠 Requirements

* **Google Earth Engine Account**
  Register at [earthengine.google.com](https://earthengine.google.com) and authenticate:

  ```js
  ee.Authenticate();
  ```
* **JavaScript Basics**
  Familiarity with GEE scripting is recommended.
* **Assets**
  Upload and import:

  * AOI geometry (e.g., Mashhad boundary)
  * Training data (`FeatureCollections` V, W, S, I, I5)
  * Industrial center tables (`table1–13`)

---

## 📋 Installation & Usage

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/air-pollution-modeling.git
cd air-pollution-modeling
```

### 2. Open in GEE Code Editor

* Copy `main.js` into the [GEE Code Editor](https://code.earthengine.google.com).
* Update placeholders (`aoi`, `table1–13`) with your own asset IDs.

### 3. Execute the Script

Run the workflow sequentially:

1. **Data loading**
2. **Processing & feature computation**
3. **Classification & modeling**

Visualize results using:

```js
Map.addLayer();
```

Export outputs via:

```js
Export.image.toDrive();
```

---

## 🌱 Key Features

* Integrated **data preprocessing**, **model training**, and **validation**
* **Cloud masking** and **spectral index** computation
* **LST downscaling** and pollutant concentration prediction
* **Scalable** to other urban areas with minimal adjustments

---

## 📌 Notes

* Modify **AOI**, **date ranges**, or **band selections** for different regions or time frames.
* High R² values indicate strong model performance; additional **ground truth data** can further enhance validation.
* Although optimized for **Mashhad**, the script can be adapted for **other cities or countries**.

---

## 🧑‍🏫 About the Author

**Armin Nakhjiri**
📧 [Nakhjiri.Armin@gmail.com](mailto:Nakhjiri.Armin@gmail.com)
