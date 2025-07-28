# Geosetta


<p align="center">
  <strong>The most comprehensive geotechnical database platform</strong>
</p>

<p align="center">
  <a href="https://geosetta.org">Website</a> •
  <a href="#api-documentation">API</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#contact">Contact</a>
</p>

---

## Overview

Geosetta is a platform for hosting subsurface investigation and historic geotechnical data from various publicly funded sources throughout the United States. As a non-profit Maryland-based organization, we offer subscription-based tools for geospatial visualization of historic geotechnical data, providing preliminary understanding of existing and anticipated subsurface conditions using machine learning techniques.

**Note:** Geosetta's data are NOT to be used as a substitute for site-specific investigations.

## 🚀 Features

### Interactive Map Interface
- **Browse Historic Data**: Access thousands of boring logs from DOTs across the United States
- **Real-time Search**: Find locations by address, latitude/longitude, zip code, or description
- **Layer Controls**: Toggle terrain elevation, geology layers, and karst data at appropriate zoom levels
- **Data Clustering**: Efficient visualization of large datasets with intelligent clustering

### Deliverable Types

#### 📍 Points
- **Historic Locations**: View existing geotechnical data with options to:
  - Download PDF boring logs
  - View data in browser and download DIGGS XML files
  - Generate 3D point cloud models
  - Access USDA soil maps
  - View in RSLog format
  - Report data issues

- **User-Placed Points**: Generate predicted geotechnical data with:
  - Anticipated boring log predictions
  - Seismic site class predictions
  - Surface elevation calculations
  - Monthly precipitation history (NOAA)

#### 📏 Lines
- Draw elevation profiles with:
  - Estimated depth to rock
  - Groundwater levels
  - Predicted blow count ranges
  - Export to Excel/CSV for CAD and slope stability analysis

#### 🔲 Polygons
- Select areas to:
  - Download all contained boring logs
  - Generate DIGGS files for multiple borings
  - Create fence diagrams
  - Export as GeoJSON, Shapefile, or KML
  - View in 3D
  - Generate subsurface statistics

### 🌟 New Features
- **MnDOT Integration**: Thousands of boring logs and CPT data from Minnesota DOT
- **Data Quality Tools**: Help improve accuracy by fixing GPS locations and reporting issues
- **3D Visualization**: Interactive 3D point cloud models of subsurface conditions
- **CPT Data Support**: Comprehensive cone penetration testing data display

## 📡 API Documentation

Geosetta offers a powerful API for sponsors to integrate our data into their systems. API access requires sponsorship.

### Available Endpoints

#### 1. Retrieve Historic Data in Radius
```python
import requests

api_key = "your_api_key_here"

json_payload = {
    "deliverableType": "Return_Historic_Data_In_Radius",
    "data": {
        "points": [{
            "latitude": 39.21884440935613,
            "longitude": -76.84346423232522,
            "radius_m": 1000
        }]
    }
}

response = requests.post(
    "https://geosetta.org/web_map/api_key/",
    json=json_payload,
    headers={"Authorization": f"Bearer {api_key}"}
)
```

#### 2. SPT Point Prediction
Generate subsurface predictions for up to 50 points per request (max depth: 100 feet).

```python
json_payload = {
    "deliverableType": "SPT_Point_Prediction",
    "data": {
        "points": [{
            "latitude": 39.387080,
            "longitude": -76.813480,
            "depth": 50,
            "surfaceelevation": None  # Optional
        }]
    }
}
```

#### 3. Project Visualization Link
Create a shareable link displaying your project data alongside Geosetta's historic data.

```python
json_payload = {
    "deliverableType": "Project_Link",
    "data": {
        "type": "FeatureCollection",
        "features": [
            # Your GeoJSON features here
        ]
    }
}
```

#### 4. Distance from Trained Point
Check the distance to the nearest point used in our training dataset.

#### 5. PDF to DIGGS Conversion
Convert PDF boring logs to DIGGS XML format.

```python
with open(pdf_file_path, 'rb') as pdf_file:
    response = requests.post(
        "https://geosetta.org/web_map/api_key/",
        files={'file': pdf_file},
        data={'json_data': json.dumps(json_payload)},
        headers={"Authorization": f"Bearer {api_key}"}
    )
```

## 🗺️ Getting Started

1. **Visit** [Geosetta.org](https://geosetta.org)
2. **Accept** the terms of use
3. **Create** a free account to view data locations
4. **Subscribe** for full access to download data and generate deliverables

### Subscription Benefits
- Download historic boring logs
- Generate subsurface predictions
- Create elevation profiles
- Export data in multiple formats
- API access (sponsors only)
- Up to 60 deliverables per month

## 🤝 Contributing

### Data Contributions
We're actively expanding our database! If your organization has boring logs, CPT data, or other geotechnical data to contribute:

📧 Contact us at [data@geosetta.org](mailto:data@geosetta.org)

### Current Data Sources
- **VDOT** - Virginia Department of Transportation
- **MDOT** - Maryland Department of Transportation  
- **MnDOT** - Minnesota Department of Transportation (NEW!)
- **Montana DOT**
- And many more...

Over half of the US DOTs are now contributing data to Geosetta!

## 📞 Contact

- **Data Contributions**: [data@geosetta.org](mailto:data@geosetta.org)
- **Feature Requests**: [features@geosetta.org](mailto:features@geosetta.org)
- **Membership**: [membership@geosetta.org](mailto:membership@geosetta.org)
- **Bug Reports**: [GitHub Issues](https://github.com/ross-cutts/Geosetta/issues)

## 📄 License & Disclaimer

The information provided by Geosetta has been made available by various DOTs and other public agencies. The predictive models are based on machine learning tools applied to the data. The predicted subsurface conditions are probabilistic models and do not depict actual conditions at the site.

**Important**: 
- No claim as to the accuracy of the data and predictive model is made or implied
- Geosetta is a tool for planning subsurface investigations, not a substitute for them
- Users must uphold engineering ethics in the use of Geosetta

## 🙏 Support Geosetta

Geosetta needs your support to continue providing this resource to our profession. Please help spread the word and consider sponsoring our mission to make geotechnical data openly accessible to professionals and researchers worldwide.

---

<p align="center">
  Made with ❤️ by the Geosetta Team
</p>
