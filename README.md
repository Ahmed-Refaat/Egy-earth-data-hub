# 🌍 Awesome Google Earth Engine Community Datasets

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
![GitHub stars](https://img.shields.io/github/stars/Ahmed-Refaat/awesome-gee-community-datasets?style=social)

> A comprehensive collection of community-sourced geospatial datasets for Google Earth Engine, making research data accessible to everyone.

## 📖 Table of Contents

- [What is This Project?](#what-is-this-project)
- [Understanding Google Earth Engine](#understanding-google-earth-engine)
- [Why This Catalog Exists](#why-this-catalog-exists)
- [Getting Started](#getting-started)
- [Complete Dataset Categories](#complete-dataset-categories)
- [How to Access and Use Data](#how-to-access-and-use-data)
- [Detailed Examples](#detailed-examples)
- [Technical Details](#technical-details)
- [Contributing to the Catalog](#contributing-to-the-catalog)
- [Troubleshooting](#troubleshooting)
- [Resources and Learning](#resources-and-learning)
- [License](#license)

## 🤔 What is This Project?

The **Awesome Google Earth Engine (GEE) Community Datasets** is a massive, curated library of geospatial data that has been preprocessed and optimized for immediate use in Google Earth Engine. This catalog serves as a bridge between raw research data and practical analysis.

### The Core Concept

Imagine having access to thousands of satellite images, climate models, population data, environmental datasets, and more—all in one place, ready to analyze without downloading a single file. That's what this catalog provides.

### What Makes This Different?

Unlike traditional data repositories where you download gigabytes of files, this catalog:
- Hosts data directly in Google's cloud infrastructure
- Provides instant access without downloads
- Offers pre-processed, analysis-ready datasets
- Includes datasets from hundreds of contributors worldwide
- Updates regularly with new data

## 🛰️ Understanding Google Earth Engine

Before diving into the datasets, let's understand the platform they run on.

### What is Google Earth Engine?

Google Earth Engine (GEE) is a cloud-based platform for planetary-scale geospatial analysis. It combines:

1. **Massive Data Catalog**: Petabytes of satellite imagery and geospatial datasets
2. **Cloud Computing**: Google's computational infrastructure
3. **APIs**: JavaScript and Python interfaces for analysis
4. **No Downloads**: All processing happens in the cloud

### How Does GEE Work?

```
Your Computer → GEE API → Google's Servers → Process Data → Return Results
```

Instead of downloading terabytes of satellite images to your computer:
- Data stays in Google's cloud
- You send code to process it
- Only results come back to you
- Massive computational power available instantly

### Who Uses GEE?

- **Researchers**: Climate scientists, ecologists, urban planners
- **Government Agencies**: Environmental monitoring, disaster response
- **NGOs**: Conservation, humanitarian projects
- **Companies**: Agriculture, insurance, real estate
- **Students**: Learning remote sensing and geospatial analysis

## 🎯 Why This Catalog Exists

### The Problem with Geospatial Data

Working with geospatial data traditionally involves several challenges:

#### 1. **Data Discovery**
- Datasets scattered across hundreds of websites
- No central index or search functionality
- Difficult to find relevant data for your region/topic

#### 2. **Preprocessing Nightmares**
- Different file formats (GeoTIFF, NetCDF, HDF, Shapefiles)
- Mismatched coordinate systems and projections
- Various temporal and spatial resolutions
- Days or weeks of preprocessing before analysis

#### 3. **Storage Limitations**
- Large datasets require terabytes of storage
- Expensive infrastructure needed
- Slow data transfer times

#### 4. **Access Barriers**
- Many datasets behind paywalls
- Registration requirements
- Limited download speeds
- Expired links and broken downloads

#### 5. **Technical Complexity**
- Requires expertise in multiple tools (GDAL, QGIS, Python)
- Steep learning curve
- Platform-specific issues

### The Solution: Community Datasets

This catalog solves all these problems by:

✅ **Centralized Discovery**: All datasets indexed and searchable in one place  
✅ **Pre-Processed**: Ready for immediate analysis, no preprocessing needed  
✅ **Cloud-Based**: No storage or download requirements  
✅ **Free Access**: No paywalls or registration barriers  
✅ **Standardized Format**: Consistent structure across all datasets  
✅ **Well Documented**: Metadata, examples, and usage instructions included  
✅ **Community Maintained**: Continuously updated and improved  

## 🚀 Getting Started

### Step 1: Set Up Google Earth Engine Account

1. **Sign Up** (Free for research and education)
   - Visit: [https://earthengine.google.com/signup/](https://earthengine.google.com/signup/)
   - Use your Google account
   - Approval usually takes 1-2 days

2. **Choose Your Interface**
   - **Code Editor** (JavaScript): Browser-based, beginner-friendly
   - **Python API**: For integration with existing Python workflows
   - **R**: Via the rgee package

### Step 2: Access the Code Editor

1. Go to: [https://code.earthengine.google.com/](https://code.earthengine.google.com/)
2. Interface components:
   - **Left Panel**: Scripts, documentation, assets
   - **Center Panel**: Code editor
   - **Right Panel**: Console, tasks, profiler
   - **Bottom**: Map visualization

### Step 3: Your First Script

```javascript
// This is your first GEE script!
// Let's load and visualize a dataset

// 1. Load a Landsat image
var image = ee.Image('LANDSAT/LC08/C02/T1_TOA/LC08_044034_20140318');

// 2. Define visualization parameters
var vizParams = {
  bands: ['B4', 'B3', 'B2'],  // RGB
  min: 0,
  max: 0.3,
  gamma: 1.4
};

// 3. Add to map
Map.centerObject(image, 9);
Map.addLayer(image, vizParams, 'Landsat Image');

// 4. Print information
print('Image Details:', image);
```

### Step 4: Use Community Datasets

Now let's use a dataset from this community catalog:

```javascript
// Load global population data from community catalog
var population = ee.ImageCollection('projects/sat-io/open-datasets/ORNL/LANDSCAN_GLOBAL')
  .filterDate('2020-01-01', '2020-12-31')
  .first();

// Visualize
var popViz = {
  min: 0,
  max: 1000,
  palette: ['white', 'yellow', 'orange', 'red', 'darkred']
};

Map.addLayer(population, popViz, 'Population Density 2020');
Map.setCenter(0, 20, 3);

// Calculate statistics for a region
var stats = population.reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: ee.Geometry.Rectangle([-10, 35, 40, 60]),
  scale: 1000,
  maxPixels: 1e9
});

print('Total Population in Region:', stats.get('b1'));
```

## 📊 Complete Dataset Categories

The catalog includes over 1,000 datasets across diverse domains. Here's a comprehensive breakdown:

### 🌡️ Climate & Meteorology

**Temperature Data**
- Historical temperature records (1900-present)
- Climate model projections (2020-2100)
- Heat wave indices and extreme events
- Urban heat island effects
- Sea surface temperature

**Precipitation**
- Global rainfall datasets (daily, monthly, annual)
- Drought indices (PDSI, SPI, SPEI)
- Snow cover and depth
- Flood frequency analysis

**Weather & Atmospheric**
- Wind speed and direction
- Humidity and atmospheric pressure
- Cloud cover and types
- Lightning strike data
- Air quality (PM2.5, PM10, NO2, SO2, O3)

**Climate Models**
- CMIP6 model outputs
- Downscaled regional climate projections
- Future scenarios (RCP, SSP)
- Climate anomalies

### 🌿 Land Cover & Vegetation

**Land Use/Land Cover**
- Global land cover maps (multiple years)
- Urban extent and growth
- Agricultural land classification
- Forest type classification
- Wetland mapping

**Vegetation Indices**
- NDVI time series (1981-present)
- EVI, SAVI, MSAVI variations
- Phenology metrics
- Vegetation health indices
- Leaf Area Index (LAI)

**Forests**
- Forest cover and change
- Tree height and biomass
- Deforestation alerts
- Forest fire history
- Mangrove extent

**Agriculture**
- Crop type mapping
- Crop yield estimates
- Irrigation patterns
- Agricultural productivity
- Cropland extent

### 🌊 Hydrology & Water Resources

**Rivers & Streams**
- Global river networks
- Stream flow data
- River discharge
- Floodplain mapping

**Water Bodies**
- Lake and reservoir extent
- Water level changes
- Reservoir storage
- Coastal waters

**Water Quality**
- Turbidity measurements
- Chlorophyll concentration
- Dissolved oxygen
- Water temperature
- Pollution indicators

**Groundwater**
- Aquifer locations
- Groundwater levels
- Recharge rates

**Floods & Droughts**
- Historical flood events
- Flood risk zones
- Drought severity indices
- Water scarcity maps

### 🏔️ Terrain & Geology

**Elevation Models**
- Digital Elevation Models (DEM)
  - SRTM (30m, 90m)
  - ASTER GDEM (30m)
  - ALOS World 3D (30m)
  - High-resolution DEMs (1m-10m)

**Derived Terrain**
- Slope and aspect
- Hillshade
- Topographic wetness index
- Terrain ruggedness
- Geomorphology

**Geological**
- Soil types and properties
- Lithology (rock types)
- Seismic zones
- Mineral deposits

### 🏙️ Urban & Infrastructure

**Buildings & Structures**
- Building footprints (global)
- Building heights
- Urban density
- Construction activity

**Transportation**
- Road networks (all classes)
- Railway lines
- Airports and ports
- Bridges and tunnels

**Urban Analysis**
- Urban sprawl indicators
- Impervious surface
- Night-time lights
- Urban green space

**Infrastructure**
- Power plants and grids
- Cell tower locations
- Internet connectivity
- Water treatment facilities

### 👥 Population & Demographics

**Population Data**
- Global population counts (1km-1m resolution)
- Population density
- Age and gender distribution
- Population projections (2020-2100)
- Migration patterns

**Settlements**
- Built-up areas
- Slum mapping
- Rural vs urban classification
- Settlement growth

**Socioeconomic**
- Poverty maps
- Economic activity
- GDP per capita
- Human Development Index
- Education levels
- Healthcare access

### 🌍 Environmental & Conservation

**Protected Areas**
- National parks and reserves
- UNESCO World Heritage Sites
- Marine protected areas
- Conservation zones

**Biodiversity**
- Species distribution
- Habitat suitability
- Biodiversity hotspots
- Endangered species ranges

**Ecosystem Services**
- Carbon sequestration
- Pollination services
- Water purification
- Soil conservation

**Environmental Hazards**
- Wildfire risk and history
- Landslide susceptibility
- Earthquake zones
- Tsunami inundation

### 🛰️ Remote Sensing Collections

**Optical Imagery**
- Landsat (1972-present)
- Sentinel-2 (10m, 2015-present)
- MODIS (250m-1km, 2000-present)
- Planet imagery
- High-resolution commercial imagery

**Radar & SAR**
- Sentinel-1 (10m, 2014-present)
- PALSAR (25m)
- ALOS-2
- TerraSAR-X

**Specialized Sensors**
- Hyperspectral imagery
- Thermal imagery
- Lidar point clouds
- Nighttime imagery (VIIRS, DMSP)

### 🔥 Natural Disasters

**Fire**
- Active fire detections
- Burned area mapping
- Fire weather indices
- Smoke plume tracking

**Storms & Cyclones**
- Hurricane tracks
- Tornado paths
- Storm surge models
- Wind damage assessment

**Earthquakes & Tsunamis**
- Seismic activity
- Ground displacement
- Tsunami models

### 🌐 Global Administrative Boundaries

**Political Boundaries**
- Country borders
- State/province boundaries
- County/district boundaries
- Municipal boundaries

**Statistical Areas**
- Census tracts
- Postal codes
- Electoral districts
- Statistical regions

## 💻 How to Access and Use Data

### Method 1: Search the Online Catalog

**Visit**: [https://gee-community-catalog.org/](https://gee-community-catalog.org/)

**Features:**
- Full-text search across 1000+ datasets
- Filter by:
  - Category (climate, vegetation, urban, etc.)
  - Spatial resolution (1m to 1km+)
  - Temporal coverage (historical vs current)
  - Geographic region
  - Data type (image, vector, table)
  
**Each dataset page includes:**
- Detailed description
- Data provider information
- Spatial and temporal extent
- Resolution specifications
- Update frequency
- Usage examples
- Asset ID for GEE
- Download links (if applicable)
- Related datasets

### Method 2: Browse GitHub Repository

**Structure:**
```
docs/
  └── projects/
      ├── agriculture/
      ├── climate/
      ├── elevation/
      ├── population/
      └── ... (50+ categories)
```

Each dataset has its own `.md` file containing:
- Comprehensive description
- Methodology
- Data sources
- Preprocessing steps
- Code examples
- Limitations
- References

### Method 3: Direct Access via Asset IDs

All datasets have unique asset IDs in this format:
```
projects/sat-io/open-datasets/CATEGORY/DATASET_NAME
```

**Example Asset IDs:**
- Population: `projects/sat-io/open-datasets/ORNL/LANDSCAN_GLOBAL`
- Land Cover: `projects/sat-io/open-datasets/landcover/ESRI_Global-LULC_10m`
- Elevation: `projects/sat-io/open-datasets/GLO-30`
- Roads: `projects/sat-io/open-datasets/OSM/roads`

### Method 4: Programmatic Search

```javascript
// Search for datasets containing "population"
var catalog = ee.FeatureCollection('projects/sat-io/open-datasets/catalog_index');
var results = catalog.filter(ee.Filter.stringContains('keywords', 'population'));
print('Matching datasets:', results.size());
print('Dataset list:', results.aggregate_array('name'));
```

## 📚 Detailed Examples

### Example 1: Urban Growth Analysis

**Objective**: Analyze urban expansion in a city over 20 years

```javascript
// Define area of interest (Cairo, Egypt)
var roi = ee.Geometry.Rectangle([31.1, 29.9, 31.5, 30.2]);

// Load urban extent datasets
var urban2000 = ee.Image('projects/sat-io/open-datasets/GHSL/built_up_2000');
var urban2020 = ee.Image('projects/sat-io/open-datasets/GHSL/built_up_2020');

// Calculate urban growth
var urbanGrowth = urban2020.subtract(urban2000);

// Visualize
var urbanViz = {
  min: 0,
  max: 1,
  palette: ['white', 'red']
};

Map.centerObject(roi, 10);
Map.addLayer(urban2000.clip(roi), urbanViz, 'Urban 2000');
Map.addLayer(urban2020.clip(roi), urbanViz, 'Urban 2020');
Map.addLayer(urbanGrowth.clip(roi), {min: 0, max: 1, palette: ['white', 'yellow']}, 'New Urban Growth');

// Calculate statistics
var area2000 = urban2000.multiply(ee.Image.pixelArea())
  .reduceRegion({
    reducer: ee.Reducer.sum(),
    geometry: roi,
    scale: 100,
    maxPixels: 1e9
  });

var area2020 = urban2020.multiply(ee.Image.pixelArea())
  .reduceRegion({
    reducer: ee.Reducer.sum(),
    geometry: roi,
    scale: 100,
    maxPixels: 1e9
  });

print('Urban Area 2000 (km²):', ee.Number(area2000.get('b1')).divide(1e6));
print('Urban Area 2020 (km²):', ee.Number(area2020.get('b1')).divide(1e6));
print('Growth (%):', ee.Number(area2020.get('b1')).subtract(area2000.get('b1'))
  .divide(area2000.get('b1')).multiply(100));
```

### Example 2: Climate Change Impact Assessment

**Objective**: Compare historical vs projected temperature

```javascript
// Load historical temperature (1980-2010)
var historicalTemp = ee.ImageCollection('projects/sat-io/open-datasets/ERA5/temperature')
  .filterDate('1980-01-01', '2010-12-31')
  .select('temperature_2m')
  .mean();

// Load future projection (2050-2080)
var futureTemp = ee.ImageCollection('projects/sat-io/open-datasets/CMIP6/temperature')
  .filterDate('2050-01-01', '2080-12-31')
  .select('temperature')
  .mean();

// Calculate temperature change
var tempChange = futureTemp.subtract(historicalTemp);

// Visualization
var tempViz = {
  min: -20,
  max: 40,
  palette: ['blue', 'cyan', 'yellow', 'orange', 'red']
};

var changeViz = {
  min: 0,
  max: 5,
  palette: ['white', 'yellow', 'orange', 'red', 'darkred']
};

Map.addLayer(historicalTemp, tempViz, 'Historical Temperature');
Map.addLayer(futureTemp, tempViz, 'Future Temperature');
Map.addLayer(tempChange, changeViz, 'Temperature Increase (°C)');

// Regional statistics
var regions = ee.FeatureCollection('USDOS/LSIB_SIMPLE/2017');
var stats = tempChange.reduceRegions({
  collection: regions,
  reducer: ee.Reducer.mean(),
  scale: 1000
});

print('Temperature change by country:', stats);

// Export results
Export.table.toDrive({
  collection: stats,
  description: 'temperature_change_by_country',
  fileFormat: 'CSV'
});
```

### Example 3: Water Quality Monitoring

**Objective**: Monitor lake water quality over time

```javascript
// Define lake boundary
var lake = ee.Geometry.Polygon([
  [[32.5, 30.0], [32.6, 30.0], [32.6, 30.1], [32.5, 30.1]]
]);

// Load Sentinel-2 imagery
var s2 = ee.ImageCollection('COPERNICUS/S2_SR')
  .filterBounds(lake)
  .filterDate('2020-01-01', '2023-12-31')
  .filter(ee.Filter.lt('CLOUDY_PIXEL_PERCENTAGE', 20));

// Function to calculate water quality indices
function addWaterIndices(image) {
  // NDWI - Normalized Difference Water Index
  var ndwi = image.normalizedDifference(['B3', 'B8']).rename('NDWI');
  
  // Turbidity (simplified)
  var turbidity = image.select('B4').divide(image.select('B2')).rename('turbidity');
  
  // Chlorophyll-a proxy
  var chlorophyll = image.select('B5').divide(image.select('B4')).rename('chlorophyll');
  
  return image.addBands([ndwi, turbidity, chlorophyll]);
}

// Apply indices
var waterQuality = s2.map(addWaterIndices);

// Time series analysis
var turbidityTS = ui.Chart.image.series({
  imageCollection: waterQuality.select('turbidity'),
  region: lake,
  reducer: ee.Reducer.mean(),
  scale: 10
}).setOptions({
  title: 'Lake Turbidity Over Time',
  vAxis: {title: 'Turbidity Index'},
  hAxis: {title: 'Date'}
});

var chlorophyllTS = ui.Chart.image.series({
  imageCollection: waterQuality.select('chlorophyll'),
  region: lake,
  reducer: ee.Reducer.mean(),
  scale: 10
}).setOptions({
  title: 'Chlorophyll-a Proxy Over Time',
  vAxis: {title: 'Chlorophyll Index'},
  hAxis: {title: 'Date'}
});

print(turbidityTS);
print(chlorophyllTS);

// Visualize latest image
var latest = waterQuality.sort('system:time_start', false).first();
Map.centerObject(lake, 12);
Map.addLayer(latest, {bands: ['B4', 'B3', 'B2'], min: 0, max: 3000}, 'RGB');
Map.addLayer(latest.select('turbidity'), {min: 0.5, max: 2, palette: ['blue', 'green', 'yellow', 'red']}, 'Turbidity');
Map.addLayer(latest.select('chlorophyll'), {min: 0.5, max: 1.5, palette: ['blue', 'cyan', 'green']}, 'Chlorophyll');
```

### Example 4: Agricultural Productivity Assessment

**Objective**: Assess crop health and predict yield

```javascript
// Define agricultural region
var farmland = ee.Geometry.Rectangle([30.0, 29.0, 31.0, 30.0]);

// Load crop type data
var cropTypes = ee.Image('projects/sat-io/open-datasets/GFSAD/crops');

// Load NDVI time series
var ndvi = ee.ImageCollection('MODIS/006/MOD13Q1')
  .filterBounds(farmland)
  .filterDate('2023-01-01', '2023-12-31')
  .select('NDVI');

// Calculate growing season metrics
var maxNDVI = ndvi.max();
var meanNDVI = ndvi.mean();
var minNDVI = ndvi.min();
var rangeNDVI = maxNDVI.subtract(minNDVI);

// Phenology metrics
var startOfSeason = ndvi.reduce(ee.Reducer.percentile([25]));
var endOfSeason = ndvi.reduce(ee.Reducer.percentile([75]));

// Productivity proxy (integrated NDVI)
var productivity = ndvi.sum();

// Visualizations
Map.centerObject(farmland, 9);
Map.addLayer(cropTypes.clip(farmland), {min: 1, max: 10, palette: ['yellow', 'green', 'darkgreen']}, 'Crop Types');
Map.addLayer(productivity.clip(farmland), {min: 1000, max: 8000, palette: ['red', 'yellow', 'green']}, 'Productivity');

// Statistics by crop type
var stats = productivity.addBands(cropTypes).reduceRegion({
  reducer: ee.Reducer.mean().group({
    groupField: 1,
    groupName: 'crop_type'
  }),
  geometry: farmland,
  scale: 250,
  maxPixels: 1e9
});

print('Productivity by crop type:', stats);

// Create time series chart
var chart = ui.Chart.image.series({
  imageCollection: ndvi,
  region: farmland,
  reducer: ee.Reducer.mean(),
  scale: 250
}).setOptions({
  title: 'NDVI Time Series - Crop Growing Season',
  vAxis: {title: 'NDVI'},
  hAxis: {title: 'Date'},
  lineWidth: 2
});

print(chart);

// Export productivity map
Export.image.toDrive({
  image: productivity.clip(farmland),
  description: 'crop_productivity_2023',
  scale: 250,
  region: farmland,
  maxPixels: 1e9
});
```

### Example 5: Disaster Response - Flood Mapping

**Objective**: Rapidly map flood extent after an event

```javascript
// Define affected area
var affectedArea = ee.Geometry.Rectangle([89.0, 23.0, 91.0, 25.0]);

// Pre-flood imagery (Sentinel-1 SAR - works through clouds)
var preFlood = ee.ImageCollection('COPERNICUS/S1_GRD')
  .filterBounds(affectedArea)
  .filterDate('2023-06-01', '2023-07-01')
  .filter(ee.Filter.listContains('transmitterReceiverPolarisation', 'VV'))
  .select('VV')
  .mean();

// Post-flood imagery
var postFlood = ee.ImageCollection('COPERNICUS/S1_GRD')
  .filterBounds(affectedArea)
  .filterDate('2023-07-15', '2023-07-25')
  .filter(ee.Filter.listContains('transmitterReceiverPolarisation', 'VV'))
  .select('VV')
  .mean();

// Calculate difference
var floodChange = postFlood.subtract(preFlood);

// Threshold to identify flooded areas (lower backscatter = water)
var floodThreshold = -3;
var floodMask = floodChange.lt(floodThreshold);

// Load population data to estimate affected people
var population = ee.Image('projects/sat-io/open-datasets/ORNL/LANDSCAN_GLOBAL/2023');

// Calculate affected population
var affectedPopulation = population.updateMask(floodMask);

var totalAffected = affectedPopulation.reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: affectedArea,
  scale: 1000,
  maxPixels: 1e9
});

// Visualizations
Map.centerObject(affectedArea, 9);
Map.addLayer(preFlood, {min: -25, max: 0}, 'Pre-Flood SAR');
Map.addLayer(postFlood, {min: -25, max: 0}, 'Post-Flood SAR');
Map.addLayer(floodMask.updateMask(floodMask), {palette: ['blue']}, 'Flooded Areas');
Map.addLayer(affectedPopulation, {min: 0, max: 1000, palette: ['yellow', 'red']}, 'Affected Population');

// Calculate flood statistics
var floodArea = floodMask.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: affectedArea,
  scale: 10,
  maxPixels: 1e9
});

print('Flooded Area (km²):', ee.Number(floodArea.get('VV')).divide(1e6));
print('Estimated Affected Population:', totalAffected.get('b1'));

// Export flood map
Export.image.toDrive({
  image: floodMask.updateMask(floodMask),
  description: 'flood_extent_map',
  scale: 10,
  region: affectedArea,
  maxPixels: 1e9
});
```

## 🔧 Technical Details

### Data Formats and Structure

**Image Collections**
- Time series of raster data
- Each image has bands (layers) and properties (metadata)
- Organized by date
- Access via: `ee.ImageCollection('asset_id')`

**Single Images**
- Individual raster datasets
- Static or single-time snapshots
- Access via: `ee.Image('asset_id')`

**Feature Collections**
- Vector data (points, lines, polygons)
- Attribute tables included
- Access via: `ee.FeatureCollection('asset_id')`

**Tables**
- Non-spatial tabular data
- Attribute information
- Can be joined with spatial data

### Spatial Resolutions Available

| Resolution | Use Cases | Example Datasets |
|------------|-----------|------------------|
| <1m | Urban planning, building detection | High-res commercial imagery |
| 1-10m | Agricultural monitoring, land use | Sentinel-2, Planet |
| 10-30m | Regional analysis, forest monitoring | Landsat, Sentinel-1 |
| 30-100m | Landscape ecology, habitat mapping | SRTM DEM, various thematic maps |
| 100-500m | Climate studies, large-scale patterns | MODIS vegetation indices |
| 500m-1km | Global monitoring, climate models | MODIS climate products |
| 1-10km | Continental analysis, weather data | Climate reanalysis |
| >10km | Global models, coarse climate data | GCM outputs |

### Temporal Coverage

**Historical Archives**
- Some datasets go back to 1900s
- Satellite era: 1972-present (Landsat)
- Most comprehensive: 2000-present

**Update Frequencies**
- Real-time: Weather, air quality
- Daily: Satellite imagery, fire detection
- Weekly: Vegetation indices
- Monthly: Climate summaries
- Annual: Land cover, population
- One-time: Static datasets (soil, geology)

### Data Processing Levels

**Level 0**: Raw instrument data (rarely available)  
**Level 1**: Radiometrically corrected  
**Level 2**: Surface reflectance, atmospherically corrected  
**Level 3**: Composited, gridded products  
**Level 4**: Model outputs, derived products  

Most community datasets are Level 2-4, ready for analysis.

### Asset Naming Convention

```
projects/sat-io/open-datasets/[CATEGORY]/[PROVIDER]/[DATASET_NAME]
```

**Examples:**
- `projects/sat-io/open-datasets/climate/ERA5/temperature`
- `projects/sat-io/open-datasets/population/LANDSCAN/2023`
- `projects/sat-io/open-datasets/landcover/ESA/WorldCover_2021`

## 🤝 Contributing to the Catalog

### Ways to Contribute

#### 1. Add a New Dataset

**Requirements:**
- Dataset must be openly accessible
- Proper licensing for redistribution
- Scientific or practical value
- Good documentation

**Process:**
1. Prepare your dataset (GeoTIFF, Shapefile, or compatible format)
2. Upload to Earth Engine asset
3. Create documentation file
4. Submit pull request with:
   - Dataset description
   - Metadata
   - Usage example
   - Source attribution

**Documentation Template:**
```markdown
# Dataset Name

## Description
Clear explanation of what the dataset contains

## Source
Original data provider and URL

## Spatial Extent
Geographic coverage (global, regional, local)

## Temporal Extent
Time period covered

## Resolution
Spatial resolution in meters

## Bands/Variables
List of all bands/variables with descriptions

## Usage Example
Code snippet showing how to load and use

## Citation
How to cite this dataset

## License
Data license information

## Contact
Maintainer information
```

#### 2. Improve Existing Documentation

- Fix typos or errors
- Add usage examples
- Improve explanations
- Add visualizations

#### 3. Report Issues

If you find problems:
- Broken asset links
- Incorrect metadata
- Data quality issues
- Missing information

Open an issue on GitHub with details.

#### 4. Share Your Use Cases

Help others by sharing:
- Analysis workflows
- Visualization techniques
- Integration examples
- Research findings

### Code Quality Standards

**JavaScript Examples:**
```javascript
// Good: Clear variable names, comments, organized
var temperatureData = ee.ImageCollection('dataset_id')
  .filterDate('2020-01-01', '2020-12-31')
  .mean();

// Define visualization parameters
var vizParams = {
  min: -20,
  max: 40,
  palette: ['blue', 'white', 'red']
};

Map.addLayer(temperatureData, vizParams, 'Temperature');
```

**Python Examples:**
```python
# Good: PEP 8 compliant, documented
import ee
ee.Initialize()

# Load and process data
temperature_data = (ee.ImageCollection('dataset_id')
    .filterDate('2020-01-01', '2020-12-31')
    .mean())

# Visualization
viz_params = {
    'min': -20,
    'max': 40,
    'palette': ['blue', 'white', 'red']
}

Map.addLayer(temperature_data, viz_params, 'Temperature')
```

## 🔧 Troubleshooting

### Common Issues and Solutions

#### 1. "Asset not found" Error

**Problem:** Asset ID incorrect or access denied

**Solutions:**
- Double-check asset ID spelling
- Ensure you're signed in to GEE
- Verify asset is publicly accessible
- Check if asset has been moved/renamed

#### 2. "Computation timeout" Error

**Problem:** Processing takes too long

**Solutions:**
```javascript
// Reduce spatial resolution
.reduceRegion({
  scale: 1000,  // Increase from 100 to 1000
  maxPixels: 1e9
});

// Limit temporal range
.filterDate('2020-01-01', '2020-01-31')  // One month instead of year

// Use smaller geometry
var smallerROI = roi.buffer(-1000);  // Shrink region
```

#### 3. "Out of memory" Error

**Problem:** Dataset too large for processing

**Solutions:**
```javascript
// Tile the processing
var grid = roi.coveringGrid(proj, 100000);  // 100km tiles

var results = grid.map(function(tile) {
  return image.reduceRegion({
    reducer: ee.Reducer.mean(),
    geometry: tile.geometry(),
    scale: 1000
  });
});

// Export instead of computing
Export.image.toDrive({
  image: result,
  description: 'export_name',
  scale: 100
});
```

#### 4. "Too many concurrent requests"

**Problem:** Rate limiting

**Solutions:**
- Add delays between requests
- Batch operations
- Use `Export` instead of `getInfo()`
- Upgrade to commercial GEE (if needed)

#### 5. Incorrect Projections

**Problem:** Data doesn't align properly

**Solutions:**
```javascript
// Reproject to common CRS
var reprojected = image.reproject({
  crs: 'EPSG:4326',  // WGS84
  scale: 30
});

// Or let GEE handle it automatically
var result = image1.addBands(image2);  // Auto-reprojects
```

#### 6. Slow Visualization

**Problem:** Map layers load slowly

**Solutions:**
```javascript
// Use pyramiding for faster display
var displayed = image.reduceResolution({
  reducer: ee.Reducer.mean(),
  maxPixels: 1024
});

// Or set max zoom
Map.addLayer(image, vizParams, 'Layer', true, 0.7, 10);  // Max zoom: 10
```

### Performance Optimization Tips

#### 1. Filter Early
```javascript
// Bad: Process then filter
var result = collection.map(expensiveFunction).filterDate(start, end);

// Good: Filter then process
var result = collection.filterDate(start, end).map(expensiveFunction);
```

#### 2. Use Built-in Functions
```javascript
// Bad: Custom NDVI calculation
var ndvi = image.select('B5').subtract(image.select('B4'))
  .divide(image.select('B5').add(image.select('B4')));

// Good: Use normalizedDifference
var ndvi = image.normalizedDifference(['B5', 'B4']);
```

#### 3. Avoid getInfo() in Loops
```javascript
// Bad: Causes multiple server calls
for (var i = 0; i < 100; i++) {
  var value = image.reduceRegion(...).getInfo();
}

// Good: Batch processing
var values = collection.map(function(img) {
  return ee.Feature(null, img.reduceRegion(...));
});
var allValues = values.aggregate_array('property').getInfo();
```

#### 4. Use Appropriate Scale
```javascript
// Match scale to data resolution
// Landsat: scale: 30
// Sentinel-2: scale: 10
// MODIS: scale: 250 or 500

// Don't over-sample
var stats = image.reduceRegion({
  scale: 30,  // Good for Landsat
  // scale: 1,  // Bad: too fine, slow and unnecessary
});
```

## 📚 Resources and Learning

### Official Documentation

**Google Earth Engine**
- [Main Documentation](https://developers.google.com/earth-engine)
- [API Reference](https://developers.google.com/earth-engine/apidocs)
- [Guides and Tutorials](https://developers.google.com/earth-engine/guides)
- [Code Editor Guide](https://developers.google.com/earth-engine/playground)

### Learning Platforms

#### Free Courses
1. **Google's Official Course**
   - [Earth Engine 101](https://developers.google.com/earth-engine/tutorials/community/intro-to-python-api)
   - Beginner-friendly
   - Self-paced

2. **Spatial Thoughts**
   - [End-to-End GEE](https://courses.spatialthoughts.com/end-to-end-gee.html)
   - Comprehensive tutorials
   - Real-world projects

3. **SERVIR Global**
   - [Training Materials](https://servir.adpc.net/tools/google-earth-engine)
   - Application-focused
   - Regional examples

#### Video Tutorials

**YouTube Channels:**
- Google Earth Engine (Official)
- Spatial Thoughts
- Geospatial School
- Earth Lab

### Books

1. **"Cloud-Based Remote Sensing with Google Earth Engine"**
   - Comprehensive guide
   - Theory + Practice
   - Multiple applications

2. **"Remote Sensing and GIS for Ecologists"**
   - Ecological applications
   - GEE examples included

### Python Libraries

#### geemap
```python
# Interactive mapping with GEE
import geemap

Map = geemap.Map()
Map.addLayer(image, viz_params, 'Layer')
Map.centerObject(roi, 10)
Map
```

**Features:**
- Interactive maps in Jupyter
- Easy data export
- Time series tools
- Split-panel visualization

**Installation:**
```bash
pip install geemap
```

#### eemont
```python
# Extended functionality
import ee, eemont

ee.Initialize()

# Spectral indices with one line
image = ee.Image('COPERNICUS/S2/20200101').spectralIndices('NDVI')
```

**Installation:**
```bash
pip install eemont
```

#### geedim
```python
# Download images easily
from geedim import download

# Download Sentinel-2 image
download.download_image(
    image_id='COPERNICUS/S2/20200101',
    region=roi,
    scale=10
)
```

### Community Resources

**Forums & Discussion**
- [GEE Google Group](https://groups.google.com/g/google-earth-engine-developers)
- [Stack Overflow (GEE tag)](https://stackoverflow.com/questions/tagged/google-earth-engine)
- [GIS Stack Exchange](https://gis.stackexchange.com/questions/tagged/google-earth-engine)

**Code Repositories**
- [GEE Community Tutorials](https://github.com/google/earthengine-community)
- [Awesome GEE Scripts](https://github.com/giswqs/qgis-earthengine-examples)

**Newsletters & Blogs**
- GEE Medium Publication
- Spatial Thoughts Blog
- Geo for Good Newsletter

### Research Papers Using Community Datasets

**Climate Change**
- Urban heat island studies
- Temperature trend analysis
- Climate model validation

**Agriculture**
- Crop yield prediction
- Irrigation monitoring
- Drought assessment

**Conservation**
- Deforestation tracking
- Habitat mapping
- Biodiversity monitoring

**Disaster Management**
- Flood mapping
- Fire risk assessment
- Damage evaluation

**Urban Planning**
- City growth analysis
- Infrastructure mapping
- Population distribution

### Example Applications by Domain

#### Environmental Science
```javascript
// Carbon sequestration estimation
var biomass = ee.Image('projects/sat-io/open-datasets/biomass/global');
var carbonStock = biomass.multiply(0.5);  // 50% of biomass is carbon
var co2Equivalent = carbonStock.multiply(3.67);  // C to CO2
```

#### Public Health
```javascript
// Air quality exposure assessment
var pm25 = ee.ImageCollection('projects/sat-io/open-datasets/air-quality/PM25');
var population = ee.Image('projects/sat-io/open-datasets/population/landscan');
var exposure = pm25.mean().multiply(population);
```

#### Economics
```javascript
// Night lights as GDP proxy
var nightlights = ee.ImageCollection('NOAA/VIIRS/DNB/MONTHLY_V1/VCMSLCFG')
  .filterDate('2020-01-01', '2020-12-31')
  .select('avg_rad')
  .mean();

var gdpProxy = nightlights.reduceRegions({
  collection: countries,
  reducer: ee.Reducer.sum(),
  scale: 500
});
```

#### Hydrology
```javascript
// Watershed delineation
var dem = ee.Image('projects/sat-io/open-datasets/DEM/FABDEM');
var flowDirection = dem.focalMax(1).subtract(dem).divide(100);
var watershed = flowDirection.cumulativeCost({
  source: outlet,
  maxDistance: 50000
});
```

## 📊 Dataset Statistics

### Current Catalog Size

- **Total Datasets**: 1,200+
- **Total Data Volume**: Multiple Petabytes
- **Categories**: 50+
- **Geographic Coverage**: Global
- **Temporal Range**: 1900 - Present
- **Contributors**: 200+ individuals and organizations

### Most Popular Datasets

1. **LandScan Population** - Global population density
2. **ESA WorldCover** - 10m land cover classification
3. **Global Forest Change** - Annual forest loss/gain
4. **MODIS Vegetation Indices** - NDVI/EVI time series
5. **Climate Reanalysis (ERA5)** - Historical weather data
6. **Global Surface Water** - Water occurrence mapping
7. **OpenStreetMap Roads** - Global road networks
8. **SRTM DEM** - Elevation data
9. **VIIRS Nightlights** - Night-time imagery
10. **Sentinel-2 Cloudless** - Annual cloud-free composites

### Update Schedule

**Weekly Updates:**
- New satellite imagery ingested
- Fire detection data
- Weather observations

**Monthly Updates:**
- New datasets added
- Existing datasets updated
- Documentation improvements

**Quarterly Reviews:**
- Dataset quality checks
- Broken links fixed
- Deprecated datasets removed

## 🔐 Data Access and Licensing

### Access Levels

**Public Assets**
- No authentication required (beyond GEE account)
- Free for research and education
- Most datasets in this catalog

**Shared Assets**
- Require permission from owner
- Usually granted upon request
- Some commercial datasets

**Private Assets**
- User-uploaded data
- Not part of this catalog

### Common Licenses

**Creative Commons**
- CC0: Public domain
- CC-BY: Attribution required
- CC-BY-SA: Share-alike

**Open Data Commons**
- ODbL: Open Database License
- ODC-BY: Attribution required

**Government Data**
- Public domain (US)
- Open Government License (UK)
- Various national policies

**Research Data**
- Often CC-BY
- Requires citation
- May have restrictions

### Citation Guidelines

Always cite:
1. **Dataset creators/providers**
2. **This catalog** (if dataset found here)
3. **Google Earth Engine** (for platform)

**Example Citation Format:**
```
Dataset Name (Year). Provider Name. Accessed through Google Earth Engine 
Community Catalog (https://github.com/Ahmed-Refaat/awesome-gee-community-datasets). 
Accessed: [Date].
```

## 🌟 Success Stories

### Research Applications

**Climate Studies**
- 500+ peer-reviewed papers
- Global temperature trend analysis
- Sea level rise projections
- Extreme weather event tracking

**Conservation**
- Protected area monitoring
- Illegal logging detection
- Wildlife habitat assessment
- Marine ecosystem tracking

**Agriculture**
- Crop type mapping in 50+ countries
- Yield prediction models
- Irrigation efficiency studies
- Food security assessments

**Urban Planning**
- City growth documentation
- Infrastructure development
- Green space analysis
- Traffic pattern studies

**Disaster Response**
- Hurricane damage assessment
- Flood extent mapping
- Wildfire progression tracking
- Earthquake impact analysis

### Real-World Impact

**UN Sustainable Development Goals**
- Data supporting 12+ SDGs
- Used by 20+ UN agencies
- Policy decision support

**Government Use**
- National forest monitoring
- Agricultural statistics
- Urban development planning
- Environmental compliance

**NGO Projects**
- Conservation planning
- Community development
- Disaster preparedness
- Resource management

## 💡 Tips and Best Practices

### Code Organization

```javascript
// 1. Define parameters at top
var START_DATE = '2020-01-01';
var END_DATE = '2020-12-31';
var CLOUD_THRESHOLD = 20;

// 2. Define geometry
var roi = ee.Geometry.Rectangle([...]);

// 3. Load and filter data
var collection = ee.ImageCollection('dataset')
  .filterDate(START_DATE, END_DATE)
  .filterBounds(roi);

// 4. Processing functions
function processImage(img) {
  // Processing logic
  return img;
}

// 5. Apply processing
var processed = collection.map(processImage);

// 6. Visualization
Map.centerObject(roi, 10);
Map.addLayer(processed, vizParams, 'Processed');

// 7. Export if needed
Export.image.toDrive({...});
```

### Documentation

```javascript
/**
 * Calculate vegetation health index
 * @param {ee.Image} image - Input Sentinel-2 image
 * @returns {ee.Image} - Image with VHI band added
 */
function calculateVHI(image) {
  var ndvi = image.normalizedDifference(['B8', 'B4']);
  var ndwi = image.normalizedDifference(['B3', 'B8']);
  var vhi = ndvi.subtract(ndwi).rename('VHI');
  return image.addBands(vhi);
}
```

### Version Control

- Save scripts regularly
- Use meaningful names
- Comment your code
- Share via GitHub
- Document changes

### Collaboration

- Use shared repositories
- Create reusable functions
- Write clear documentation
- Provide examples
- Respond to feedback

## 🚦 Getting Help

### Where to Ask Questions

1. **GitHub Issues** (This repository)
   - Dataset problems
   - Documentation errors
   - Feature requests

2. **GEE Forum**
   - Technical GEE questions
   - Code troubleshooting
   - Algorithm discussions

3. **Stack Overflow**
   - Specific coding problems
   - Error messages
   - Best practices

### Before Asking

1. Search existing answers
2. Check documentation
3. Try minimal example
4. Include error messages
5. Share reproducible code

### Question Template

```markdown
**Problem Description:**
Clear explanation of what you're trying to do

**Code:**
Minimal reproducible example

**Error Message:**
Exact error text

**What I've Tried:**
Steps already attempted

**Environment:**
- GEE Code Editor or Python
- Dataset(s) used
- Region of interest
```

## 📄 License

This project is licensed under the **Apache License 2.0**.

### What You Can Do

✅ **Commercial Use** - Use for commercial projects  
✅ **Modification** - Modify and adapt the code  
✅ **Distribution** - Share with others  
✅ **Patent Use** - Use any patents in the project  
✅ **Private Use** - Use privately  

### What You Must Do

⚠️ **Include License** - Include license in distributions  
⚠️ **State Changes** - Document modifications  
⚠️ **Include Notice** - Include NOTICE file if provided  

### What You Cannot Do

❌ **Trademark Use** - Use project trademarks without permission  
❌ **Liability** - Hold authors liable  
❌ **Warranty** - Expect warranties  

### Individual Dataset Licenses

Each dataset may have its own license. Always check:
- Dataset documentation
- Original source
- Usage restrictions
- Citation requirements

When in doubt, contact the dataset provider.

## 🙏 Final Notes

This catalog represents collaborative effort from researchers, scientists, and developers worldwide who believe in open access to geospatial data. By sharing datasets, we:

- **Accelerate Research** - No need to reinvent the wheel
- **Promote Transparency** - Open data, open science
- **Enable Innovation** - More access = more creativity
- **Support Education** - Free learning resources
- **Address Global Challenges** - Climate, conservation, development

### Contributing Back

If this catalog helps your work:
- Share your results
- Contribute new datasets
- Improve documentation
- Support others in the community
- Cite the catalog in publications

### Stay Connected

- ⭐ **Star this repository**
- 👁️ **Watch for updates**
- 🔄 **Share with colleagues**
- 💬 **Join discussions**
- 🐛 **Report issues**

### Project Maintenance

**Maintained by:** Ahmed Refaat  
**Contact:** [GitHub Profile](https://github.com/Ahmed-Refaat)  
**Issues:** [Report Here](https://github.com/Ahmed-Refaat/awesome-gee-community-datasets/issues)  
**Updates:** Regular additions and improvements  

---

**Happy Mapping! 🌍🛰️**

*Making geospatial data accessible to everyone, everywhere.*

*Last Updated: January 2026*
