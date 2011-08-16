---
layout: modulespec

title: Water supply module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

Water supply is a complex ecosystem service to spatially model, given that groundwater and surface water 
are closely connected but move based on different controlling factors, that these influences on hydrology 
and hydrologic models differ greatly based on the spatial and temporal scale and the region of the world 
considered, and that available spatial data can rarely support modeling at both high spatial and temporal 
resolutions.  Given these limitations, our initial water supply models operate at an annual scale (which 
is matched by available spatial data for important variables including precipitation, infiltration, snowmelt, 
and evapotranspiration).  We currently consider only flows of surface water, though we do model the 
infiltration of surface water into groundwater and groundwater extraction from wells.  We also use a set of 
generalized models to represent sources of surface water (precipitation, snowmelt, springs, baseflow to 
rivers, and incoming inter-basin water transfers), sinks of surface water (evapotranspiration, infiltration), 
beneficiaries or users of surface water, and the flow of surface water across the landscape (routed using 
SRTM elevation data).  The long-term intent of our modeling process is to incorporate existing hydrologic 
models wherever appropriate that will more realistically account for hydrologic processes.  Over time this 
includes modeling groundwater and its movement and use.  As spatial data continue to improve, it may also be 
possible to model water supply at finer temporal scales.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Surface water source

Areas where surface water enters the landscape and becomes available for human use, via 
precipitation, snowmelt, springs, baseflow to rivers, and incoming inter-basin water 
transfers.

### Surface water sink

Areas that where surface water transitions to groundwater (via infiltration) or atmospheric 
water (via evapotranspiration).

### Surface water beneficiaries

Human users of surface water, obtained via water intakes or surface diversions.

### Surface water flow

Surface water flows are routed across the landscape through topography and stream networks.

### Groundwater source

Areas where groundwater enters the water table and becomes available for human use, via 
infiltration or artificial groundwater augmentation.

### Groundwater sink

Areas where groundwater transitions to surface water (via springs or baseflow).

### Groundwater beneficiaries

Human users of groundwater, obtained via groundwater wells.

### Groundwater flow

Groundwater flows, which depend on subsurface geology (e.g., porosity of rock layers) and 
groundwater elevations.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
-------------------------

### Case studies

1. San Pedro River Watershed, Arizona and Sonora
2. La Antigua Watershed, Veracruz, Mexico

### Model structure and assumptions

**Water supply source models.** Past studies have used a variety of spatial data to map water supply and 
regulation services on the landscape.  These have typically included overlays of supply and demand (Boyd 
and Wainger 2003, Wundscher et al. 2008), estimates of water stored in soils and aquifers using infiltration 
data (Egoh et al. 2008), precipitation and evapotranspiration data (Chan et al. 2006), or the SCS curve 
number (SCS 1972, Gately 2008) or Budyko Curve method to account for precipitation and evapotranspiration
across the landscape (Tallis et al. 2011).  Given the difficulty in developing a generalized model of 
hydrologic processes that is applicable at multiple spatial scales and in different ecological contexts, 
the initial ARIES water supply models include direct data or Bayesian models (for surface water sinks) 
that are applicable to our case study regions but that incorporate many of the influences on hydrologic 
processes that were used by the above authors.   In cases where vegetation-hydrology relationships are 
poorly understood, such as in tropical forests (Bruijnzeel 2004), ARIES' data-driven modeling approach 
may be more appropriate than using process-based approaches.  In many other cases, future generation ARIES 
models will link existing hydrologic models, improving model quality and credibility.

Spatial data or calibrated hydrologic model outputs can generally be used as the source value for surface 
and groundwater supply, with no Bayesian model needed.  There are at least five potential sources of 
surface water, which can be summed to obtain the total annual surface water source value: precipitation, 
snowmelt, springs, baseflow to rivers, and incoming inter-basin water transfers where water is discharged 
into surface water bodies.  If we run the model using annual average values, snowmelt only becomes important 
in locations with glaciers (i.e., annual snowmelt in all other locations is included in annual precipitation 
totals).  Sources of groundwater include areas of infiltration and deep percolation that lead to aquifer 
recharge, along with artificial groundwater recharge.

For the San Pedro, we use annual precipitation as the source value for surface water.  We show initial 
results for a representative dry (2002) and wet year (2007), since the 30-year average data from PRISM 
is less meaningful in arid environments where annual precipitation is highly variable.  If desired, a 
user could also input precipitation data from other years to use as the surface water source value. For 
groundwater, we can compare spatial data for soil infiltration, infiltration results from the surface 
water sink Bayesian network model, and the results of hydrologic models (once incorporated) as possible 
source values.  In the future, we could also incorporate data on the location of groundwater recharge 
facilities in the Sierra Vista area, assuming the data were available.  We do not include snowmelt in 
the source model, as there is no persistent snowpack in the mountains within the San Pedro River Watershed. 
Until detailed surface and groundwater models are incorporated, we lack data on baseflow.  Although incoming 
interbasin water transfers are proposed (Bureau of Reclamation 2007), there are currently no incoming water 
transfers from outside the basin.  Finally, while we have data on the location of springs in the San Pedro, 
we do not use these data in the source model as we do not know their discharge volume, and most spring 
discharge quickly infiltrates back into the soil via ephemeral stream channels.

For La Antigua, we also use annual precipitation as the source value for surface water.  Infiltration 
results from the surface water sink Bayesian network model can serve as the source value for groundwater.  
Like the San Pedro, there is no persistent snowpack in the mountains within the La Antigua watershed.  
We also lack detailed hydrologic data or models on springs, baseflow, incoming interbasin water transfers, 
and groundwater recharge, so do not include these as sources of surface or groundwater.

**Water supply sink models.** Surface water sinks include areas of evapotranspiration and infiltration.  
Conversely, groundwater sinks include springs and baseflow to rivers.  Lacking an external groundwater model, 
we currently do not include springs or baseflow as groundwater sinks for the San Pedro.  For both the San Pedro 
and La Antigua, we set the total surface water sink as the sum of evapotranspiration and deep soil infiltration. 
Runoff data will play a role in training of the Bayesian network models to help account for the difference 
between precipitation and sinks.

For the San Pedro, nationwide data are available for deep soil infiltration and global data for actual 
evapotranspiration.  While these data sources can be used as training data for Bayesian network models, both 
datasets are problematic.  The evapotranspiration dataset has low spatial resolution (0.5 x 0.5 degree) and 
does not capture local variation in vegetation type, tree canopy cover, and temperature, all of which are key 
influences on evapotranspiration.  The infiltration data, having been developed at the national level, are 
unlikely to account for the limited area over which infiltration actually occurs in the semiarid Basin and 
Range region of the southwestern United States.  We therefore use a Bayesian network that considers vegetation 
type, percent tree canopy cover, and annual maximum temperature as influences on evapotranspiration.  We set 
the locations of stream channels and limestone bedrock and the intersection of valley fill alluvium and the 
mountain fronts to account for the two key locations of deep percolation and groundwater recharge: the mountain 
fronts, stream banks, and ephemeral stream channels (Pool and Dickinson 2007). In the future, we could also 
incorporate data on the location of groundwater recharge facilities in the Sierra Vista area, assuming the data 
are available.  We set priors for these nodes based on a review of the corresponding spatial data.  We set the 
highest values for the evapotranspiration conditional probability table under greater percent tree canopy cover 
and higher temperatures, all else being equal.  We set the highest evapotranspiration rates for vegetation type 
to riparian, followed by forests, then mesquite woodland, oak woodland, agriculture, urban, and grassland, with 
the lowest values set for desert scrub.  We set the conditional probability for infiltration as highest at the 
mountain fronts and as slightly lower in stream channels, and set it as extremely low elsewhere.

For La Antigua, we set the evapotranspiration as a function of vegetation type and percent tree canopy cover, and 
set deep infiltration as a function of hydrologic soils group, slope, and percent impervious surface cover.  We set 
the conditional probability for evapotranspiration to be highest with greater tree canopy cover and for riparian 
vegetation and forests and lowest for agriculture, urban, and grassland.  We assume infiltration to be greatest on 
shallow slopes, low levels of impervious surface cover, and hydrologic soils groups A and B.

[![Bayesian network model for surface water sinks in La Antigua Watershed, Veracruz, Mexico. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files.](/images/bn/WaterSinkLaAntigua.gif)](/downloads/SurfaceWaterSinkLA.xdsl)
{: .bayesnet }

**Water supply use models.** Users access groundwater through wells and surface water through surface diversions, 
direct pumping from water bodies, and outgoing inter-basin water transfers.  Users can be split by use type (e.g., 
agriculture, domestic, industrial use) if deemed relevant to the case study of interest.

For the San Pedro, we mapped the location and volume of the two surface water diversions on the river at St. David 
and Pomerene.  We use well data and capacity to identify groundwater use.  Although the state wells database 
identifies users, they are not explicitly grouped by use, so at this time we do not separate out agricultural, mining, 
military, or domestic water uses.  Also, since we do not currently have an integrated groundwater flow model, we do 
not explicitly connect sources, sinks, and users for groundwater.

For La Antigua, we used spatial and tabular data to map the location and volume of surface water diversions.  Well 
data and well capacity could be used to identify groundwater use. In either case, legally binding water rights would 
also be informative for further identifying beneficiaries and use. We mapped four distinct beneficiary classes, 
including agriculture, aquaculture, industrial, and residential water use.

**Water supply flow models.** The source models determine the annual quantity (in mm<sup>3</sup>/yr) of precipitation 
and other surface water sources (in the surface water models) or infiltration to groundwater (in the groundwater 
source models).  The sink models estimate the annual quantity of water transitioning between surface and groundwater, 
and vice versa, and the use models estimate the quantity of water used by beneficiaries in each location.  Surface 
and groundwater flows must be modeled separately, as they move at different rates, with flows governed by different 
factors.

Currently, we map surface water flow using a simple water routing model.  This model relies on the SRTM elevation data 
to identify flow directions for water.  Water is moved across the landscape using this derived flow direction layer 
until it encounters a stream (represented using a hydrography layer), at which point it moves downstream through 
the stream network.  Users or sinks encountered in transit reduce the quantity of water carried across the landscape.

Subsurface water flows are considerably more complex, and are governed by factors including geology (i.e., porosity 
of rock layers) and groundwater elevations.  Subsurface flows are commonly modeled using the MODFLOW model (Harbaugh 
et al. 2000).  Future releases of ARIES will investigate the feasibility of linking groundwater models to source, 
sink, and use models to fully and more accurately represent water flows using accepted hydrologic models.

Key outputs from the flow models include: 

1. Possible surface water flow: The movement of surface water via topography and stream networks, and groundwater via appropriate groundwater flow paths while disregarding sinks.
2. Possible surface water supply: Atmospheric, ground, or surface water transitions providing an initial source quantity of surface or groundwater, that are capable of providing water to human beneficiaries when accounting for surface or groundwater flow paths but not sinks.
3. Possible surface water use: Water actually reaching a user, but not accounting for the activity of sinks.
4. Actual surface water flow: The movement of surface and groundwater, accounting for flow topology and sinks.
5. Used surface water supply: Atmospheric, ground, or surface water transitions that result in an initial source quantity surface or groundwater, that are capable of providing water to human beneficiaries when accounting for surface or groundwater flow paths and sinks (i.e., locations actually providing water to human beneficiaries).
6. Actual surface water sink: Locations where surface water transitions into groundwater (via infiltration) or atmospheric water (via evapotranspiration), or where groundwater transitions into surface water (via springs or baseflow).
7. Satisfied surface water demand; Satisfied groundwater demand: The portion of demand for water satisfied by extraction of surface or groundwater.
8. Sunk surface water flow: Water flow that fails to reach a user because it encountered a sink and transitioned from surface or groundwater into the atmosphere, surface, or groundwater.
9. Sunk surface water supply: Source locations of surface or groundwater that fail to reach a user due to their encountering a sink and that transitions water to the atmospheric, surface, or groundwater.
10. Blocked surface water demand: Demand for surface or groundwater that goes unsatisfied due to the action of sinks that transition water between surface, atmospheric, and groundwater.

### Spatial data

|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|
| Model                     | Layer                                    | Source                                                 | Spatial Extent                     | Data type/Spatial resolution     |                               Year |
|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|
| Source - All models       | Annual precipitation                     | WorldClim                                              | Global                             | Raster/30 x 30 arc seconds       |                          1950-2000 |
| Source - San Pedro        | <span />                                 | PRISM/Oregon State Univ.                               | United States                      | Raster/800 x 800 m               |                          1971-2000 |
| Source & sink - San Pedro | Soil infiltration                        | USGS                                                   | Continental United States          | Raster/1 km<sup>2</sup>          | Derived from 1951-1980 runoff data |
| <span />                  | Springs                                  | Arizona Geographic Information Council                 | Arizona                            | Rasterized point data            |                                n/a |
| Source - All models       | Snowmelt                                 | Univ. Delaware Global Water Balance Archive            | Global                             | Raster/0.5 x 0.5 degree          |                          1950-1999 |
|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|
| Sink - All models         | Average annual actual evapotranspiration | SAGE/Univ. Wisconsin                                   | Global                             | Raster/0.5 x 0.5 degree          |                          1950-1999 |
| <span />                  | Average annual runoff                    | SAGE/Univ. Wisconsin                                   | Global                             | Raster/0.5 x 0.5 degree          |                          1955-1990 |
| <span />                  | Tree canopy cover                        | GLCF/Univ. Maryland                                    | Global                             | Raster/1 km<sup>2</sup>          |                               2000 |
| Sink - San Pedro          | <span />                                 | NLCD 2001                                              | United States                      | Raster/30 x 30 m                 |                               2001 |
| <span />                  | Annual maximum temperature               | WorldClim                                              | Global                             | Raster/30 x 30 arc seconds       |                          1950-2000 |
| <span />                  | <span />                                 | PRISM/Oregon State Univ.                               | United States                      | Raster/800 x 800 m               |                          1971-2000 |
| <span />                  | Mountainfront recharge zones             | Derived from Arizona Geographic Information Council    | Arizona                            | Vector shapefile                 |                                n/a |
| Sink - San Pedro          | Vegetation type                          | Southwest Regional Gap Analysis (SWReGAP) LULC         | AZ, CO, NM, NV, UT                 | Raster/30 x 30 m                 |                               2000 |
| Sink & flow - San Pedro   | Hydrography                              | National Hydrography Dataset                           | Arizona                            | Vector line data                 |                                n/a |
| <span />                  | <span />                                 | EPA San Pedro Data Browser                             | Upper San Pedro in Sonora, Mexico  | Vector line data                 |                                n/a |
| Sink & flow - La Antigua  | <span />                                 | INECOL                                                 | La Antigua                         | Vector line data                 |                                n/a |
| Sink - La Antigua         | Vegetation tyoe                          | INECOL                                                 | La Antigua                         | Vector shapefile                  |                      Not available |
| <span />                  | Slope                                    | Derived from global SRTM data                          | Global                             | Raster/90 x 90 m                 |                                n/a |
| <span />                  | Impervious surface cover                 | NOAA-NGDC                                              | Global                             | Raster/1 km<sup>2</sup>          |                          2000-2001 |
| <span />                  | Hydrologic soils group                   | Gately (2008) using FAO soils data                     | Global                             | Raster/0.083 degrees<sup>2</sup> |                                n/a |
|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|
| Use - San Pedro           | Surface diversions                       | Digitized locations of St. David & Pomerene Diversions | San Pedro                          | Rasterized point data            |                               2010 |
| <span />                  | Well user type, capacity, depth          | Arizona Dept. of Water Resources Wells 55 Database     | Arizona                            | Rasterized point data            |                               2010 |
| Use - All models          | Well locations                           | INECOL                                                 | States of Puebla, Sonora, Veracruz | Rasterized point data            |                      Not available |
| Use - La Antigua          | Water extracton amounts and user types   | INECOL                                                 | La Antigua                         | Rasterized point data            |                      Not available |
|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|
| Flow - All models         | Elevation                                | SRTM                                                   | Global                             | Raster/90 x 90 m                 |                                n/a |
|---------------------------+------------------------------------------+--------------------------------------------------------+------------------------------------+----------------------------------+------------------------------------|

<div id="module-spec-references" markdown="1">

### References

Boyd, J and L. Wainger.  2003.  Measuring ecosystem service benefits: The use of landscape analysis to evaluate 
environmental trades and compensation.  Discussion Paper 02-63, Resources for the Future: Washington, DC.

Bruijnzeel, L.A.  2004.  Hydrological functions of tropical forests: Not seeing the soil for the trees?  
Agriculture, Ecosystems, and Environment 104: 185-228.

Bureau of Reclamation.  2007.  Appraisal report: Augmentation alternatives for the Sierra Vista Sub-watershed, 
Arizona: Lower Colorado Region.  U.S. Department of Interior Bureau of Reclamation: Denver, CO.

Chan, K.M.A., et al.  2006.  Conservation planning for ecosystem services.  PLOS Biology 4 (11): 2138-2152.

Egoh, B, et al.  2008.  Mapping ecosystem services for planning and management.  Agriculture, Ecosystems and 
Environment 127: 135-140.

Gately, M.  2008.  Dynamic modeling to inform environmental management: Applications in energy resources and 
ecosystem services.  MS Thesis, University of Vermont, Burlington, VT.

Harbaugh, A.W., et al.  2000.  MODFLOW-2000, The U.S. Geological Survey modular ground-water model - User guide 
to modularization concepts and the ground-water flow process: USGS Open-File Report 00-92.  USGS: Reston, VA.

Pool, D.R. and J.E. Dickinson.  2007.  Ground-water flow model of the Sierra Vista Subwatershed and Sonoran 
portions of the Upper San Pedro Basin, southeast Arizona, United States, and northern Sonora, Mexico.  USGS 
Scientific Investigations Report 2006-5228.  USGS: Reston, VA.

Soil Conservation Service (SCS).  1972.  National Engineering Handbook, Section 4, Hydrology.  SCS: Washington, DC.

Tallis, H.T., et al.  2011. InVEST 2.0 beta User's Guide. The Natural Capital Project: Stanford.

Wundscher, T., et al. 2008.  Spatial targeting of payments for environmental services: A tool for boosting conservation 
benefits.  Ecological Economics 65: 822-833.

</div>

### Acknowledgements and additional contributors

Octavio Perez-Maqueo, Gabriela Mendoza, Rowan Post, and Karyn Tabor developed the Veracruz case study. An expert 
review panel including individuals from the U.S. Geological Survey, University of Arizona, Bureau of Land Management, 
and other organizations provided data and model review for the San Pedro case study.

</div>
