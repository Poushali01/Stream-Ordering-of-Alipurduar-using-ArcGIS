# 🌍 Stream Ordering in Alipurduar District using ArcGIS  

## 📌 Project Overview                                            
- 📍 *Location:* Alipurduar District, West Bengal, India  
- 🗺 *Software Used:* ArcGIS, Python  
- 🏞 *Data Used:* Digital Elevation Model (DEM)  

## 📂 Dataset Overview  
The following datasets are used in this project:  

### 🗺 1. Raw Data  
- - [Alipurduar DEM (Fill Analyst)](https://github.com/Poushali01/My-Geospatial-Project/raw/main/Alipurduar%20DEM%20(Fill%20Analyst).zip)  
- [Alipurduar Shapefile](https://github.com/Poushali01/My-Geospatial-Project/raw/main/Alipurduar%20Shapefile.zip)

### 🔍 2. Processed Data  
- [Flow Direction](https://github.com/Poushali01/My-Geospatial-Project/raw/main/Flow%20Direction.zip)    

### 📊 3. Outputs  
- [Stream Ordering](https://github.com/Poushali01/My-Geospatial-Project/raw/main/Stream%20Ordering.zip)


### 📄 Stream Ordering Report

[Stream Ordering of Alipurduar using ArcGIS (PDF)](https://github.com/Poushali01/Stream-Ordering-of-Alipurduar-using-ArcGIS/raw/main/Stream%20Ordering%20of%20Alipurduar%20using%20ArcGIS.pdf)


### 🌍 Spatial Data Representation of Alipurduar District
![layout_page-0001](https://github.com/user-attachments/assets/44793674-372b-4f58-8d02-de32db349ddd)



## 🚀 How to Use  
The following workflow was used to analyze the stream network of Alipurduar using ArcGIS hydrological tools:

1️⃣ Fill DEM → Remove sinks and smoothen water flow.
2️⃣ Flow Direction → Generate a raster showing water movement.
3️⃣ Flow Accumulation → Identify major drainage paths.
4️⃣ Set Threshold Value → Use Raster Calculator to filter significant streams.
5️⃣ Stream Ordering → Classify streams using Strahler's method.
6️⃣ Convert to Vector → Transform streams into vector format for better visualization.
7️⃣ Final Layout & Map Composition → Prepare the final map.

🔹 Tools Used → ArcGIS Spatial Analyst, Raster Calculator, and Cartography tools.


## 🛠 Code Used  
The following Python commands were executed in the *ArcGIS Python Prompt* to generate stream ordering of Alipurduar:

```python
import arcpy  
from arcpy.sa import  

# Fill sinks in the DEM
fill = Fill("Alipurduar_DEM")

# Compute Flow Direction
flow_di = FlowDirection("Fill_Dem", "NORMAL")

# Compute Flow Accumulation
flow_accumulation = FlowAccumulation("Flow_Direction", "Fill_Dem", "FLOAT")

# Compute Stream Order using the Strahler method
stream_ordering = StreamOrder("Flow_Raster", "Flow_Direction", "STRAHLER")

# Convert Stream Order raster to vector features
stream_to_feature = StreamToFeature("Stream_Order", "Flow_Direction", "Stream")
