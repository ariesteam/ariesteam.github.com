---
layout: modulespec

title: Sediment regulation module specs
---
<div id="module-spec-intro" markdown="1">

Along with modeling sources of waterborne sediment, we model sink regions where sediment deposition 
occurs, along with users who either value beneficial sediment or would be harmed by delivery of excess 
sediment or the presence of excessively turbid waterways.  Sediment regulation can thus be classified 
as either a provisioning or preventive service, depending on whether the user benefits from or is harmed 
by sediment delivery.  Running the sediment flow model allows the user to map spatial connections between 
sources of sediment, areas that promote sediment deposition, and users that benefit from or are harmed 
by sediment delivery.  Additionally, the sediment models can quantify the erosion control benefits that 
vegetation provides in situ for farmers or other beneficiaries who want to avoid soil loss from their 
lands.  This benefit can be estimated by simply running the erosion source model in the present state and 
comparing results with either no vegetation or a different vegetation type, without needing to run a flow 
model.  By using the ARIES internal rule base to select the appropriate models, we can apply deeterministic 
models (e.g., RUSLE, Renard et al. 1996) on more parts of the landscape where they are known to be more 
suitable, and compliment these models with regionally appropriate ad hoc erosion models for steeper slopes or 
areas where RUSLE is known to be inadequate.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Sediment source

Areas where soil erosion occurs, and water transports sediment to a downstream 
locations.

### Sediment sink

Areas where sediment is deposited. In the ARIES sediment sink models, deposition 
is typically modeled to occur in floodplains and reservoirs.

### Sediment beneficiaries

For the preventive service case, sediment use models map the location of potential 
beneficiaries of avoided 1) detrimental sedimentation, 2) detrimental erosion, or 
3) excessively turbid surface water.  In the provisioning service case, sediment 
use models identify regions that could benefit from sediment deposition. 

### Sediment flow

Sediment flows are routed across the landscape through topography and stream networks. 
Once sediment is in a stream, it can be deposited in floodplains, reservoirs, or lakes
and coastal zones. Sediment delivery can be attributed to upstream sediment sources, 
and depostion can be attributed to upstream sediment sinks, which provide the ecosystem 
service of sediment regulation.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
-------------------------

### Case studies

1. Western Washington State
2. Madagascar
3. Dominican Republic

### Model structure and assumptions

**Sediment source models.** Other ecosystem services researchers have also attempted to map 
sedimentation values.  While Eade and Moran (1996) and Tallis et al. (2011) modeled sedimentation 
using the USLE, Egoh et al. (2008) and Wendland et al. (2010) used other proxy data.  Egoh et al. 
combined local estimates of soil erosion potential with expert rankings of the ability of tree 
canopy cover to prevent erosion.  Drawing on Quinton et al.'s (1997) work in semiarid Spain, Egoh 
et al. note that soil erosion is slightly reduced at about 30% tree canopy cover and significantly 
reduced at about 70% tree canopy cover.  By combining areas of high erosion potential and <30, >30, 
or >70% tree canopy cover, they estimate spatially explicit values of vegetation for erosion control. 
Wendland et al., noting the established link between forest cover and sedimentation for Madagascar 
(Albietz 2007), map upstream forest cover from population centers, irrigated rice fields, and mangroves 
- areas that benefit from sediment-free water.  We use these authors' work to inform our sedimentation 
models.

We designed probabilistic sediment source models that could complement the deterministic (RUSLE) 
models where their results are expected to be less reliable.  For each model, we set annual sediment 
loss as a function of runoff, vegetative maturity (i.e., vegetation characteristics that affect runoff), 
and soil erodibility.  We set vegetative maturity as a function of vegetation type and percent tree 
canopy cover for all case studies, and added successional stage as a further influence on vegetative 
maturity for the Dominican Republic and Western Washington.  We set runoff as a function of annual 
precipitation and tropical storm probability for the Dominican Republic and Madagascar.  For Western 
Washington, we used annual precipitation as a direct influence on annual sediment source value. Finally, 
we set soil erodibility in all models as a function of hydrologic soils group, soil texture, and slope. 
In Western Washington, we added slope stability as a fourth influence on soil erodiblity, since these 
data were available for the region.  We discretized percent tree canopy cover using Quinton et al.'s 
(1997) breakpoints of 30% and 70% cover discussed above and used Jenks natural breaks to discretize 
all other continuous variables.  We estimated priors based on their corresponding spatial datasets 
for the Dominican Republic, Madagascar, and Western Washington.

For Madagascar, we completed the contingent probability table for vegetative maturity by "pegging the 
corners" (Marcot et al. 2006) for highest vegetative maturity under conditions of very high tree canopy 
cover and forest/wetland vegetation type, the lowest vegetative maturity for very low tree canopy cover 
and cropland/developed vegetation type, and interpolating intermediate values.  We set forests and 
wetlands as having the highest maturity, followed by degraded forests, savannas, and cropland/developed 
land.  For the Dominican Republic and Western Washington, we set conditional priors for vegetative maturity 
by ranking the order of importance of child nodes, with vegetation type most important and successional 
stage and percent tree canopy cover progressively less important.  We set the greatest vegetative maturity 
(all else being equal) for Western Washington for forests and wetlands, followed by shrubland and grasslands, 
followed by cropland, barren, and developed.  For the Dominican Republic, we set the greatest vegetative 
maturity (all else being equal) for water, wetlands, and mangroves, followed by forests and shrubland, 
followed by shade coffee and cocoa, followed by intensive cropland and pasture, and finally by urban and 
roads.  We set the contingent probability table for runoff in Madagascar and the Dominican Republic by 
pegging the corners for high precipitation and/or high tropical storm probability leading to the greatest 
runoff and vice versa, with intermediate values interpolated.  We set values in the contingent probability 
table for erodibility as greatest on steep, coarse soils with high infiltration potential (hydrologic soils 
group A) and erodibility (for Western Washington), and vice versa, with intermediate values interpolated. We 
set the top node, the annual sediment erosion source value, at zero for all soils with very low erodibility, 
set it at its highest on very erodible soils with very high runoff and no vegetative maturity, and interpolated 
intermediate values.

[![](/images/bn/SedimentSourceMg.gif)](/downloads/SedimentSourceMg.xdsl)
{: .bayesnet title="Bayesian network model for sediment sources in
Madagascar. Please visit http://genie.sis.pitt.edu/downloads.html to
download the GeNIe Bayesian network editor, which will read .xdsl files." }

**Sediment sink models.** Erosion sinks are areas where sediment accumulates as it flows downhill or downstream. We 
only consider the deposition of sediment in floodplains and reservoirs, as opposed to sediment carried and then 
deposited by overland flow before reaching a stream.  We define sediment deposition ("Annual sediment sink", 
measured in tons of sediment per year) to be a function of three stream and floodplain variables - stream gradient, 
floodplain tree canopy cover, and floodplain width - plus dams that cause sediment deposition in reservoirs.

The erosion sink models for the three case studies are identical, except that we set prior probabilities for 
artificial infrastructure much lower for less developed settings (e.g., Dominican Republic, Madagascar) than 
in more developed settings (e.g., Western Washington).  We discretized floodplain tree canopy cover using Jenks 
natural breaks and stream gradient using breakpoints of 0-2% for low gradient streams, 2-5% for moderate gradient 
streams, and >5% for high gradient streams.  We based priors for all nodes on relevant spatial data for each case 
study.  We set the contingent probability table for annual sediment sink by assuming deposition to be greatest in 
low-gradient streams with wide floodplains and high levels of tree canopy cover, and lowest under the opposite 
conditions, with intermediate values interpolated.  The presence of reservoirs, which create slack water flow 
conditions, leads to high deposition levels in all circumstances.

[![](/images/bn/SedimentSinkMg.gif)](/downloads/SedimentSinkMg.xdsl)
{: .bayesnet title="Bayesian network model for sediment sinks in
Madagascar. Please visit http://genie.sis.pitt.edu/downloads.html to
download the GeNIe Bayesian network editor, which will read .xdsl files." }

**Sediment use models.** While not explicitly presenting ecosystem service flow model results, both Tallis et al. 
(2011) and Wendland et al. (2010) incorporate beneficiaries in their sedimentation models.  Tallis et al. map 
the locations of reservoirs where avoided sedimentation is a benefit, while Wendland et al. map human population 
density (for drinking water), mangroves (for avoided sedimentation of fish habitat), and rice fields (for avoided 
crop damage).  Mapping these beneficiaries in ARIES can often be done with a single spatial data layer or simple 
GIS operations rather than Bayesian networks.  For instance, we can map: 1) the location of reservoirs, drinking 
water intakes, and navigation infrastructure (where high turbidity or excess sedimentation are undesirable), 2) 
floodplain farmers (where sedimentation may be beneficial or undesirable, using a simple overlay of floodplains 
and farmland), or 3) erosion-prone farmers (where erosion is undesirable, by simply intersecting erosion sources 
and farmland).

**Sediment flow models.** The source and sink models estimate the annual quantity (in tons or kg of sediment 
per hectare) of sediment that could potentially be eroded from one part of the landscape (in the source model) 
and deposited in another (in the sink model).  For the preventive service case, use models map the location of 
potential beneficiaries of avoided 1) detrimental sedimentation, 2) detrimental erosion, or 3) excessively turbid 
surface water.  In the provisioning service case, use models identify regions that could benefit from sediment 
deposition. As discussed in the introduction to this chapter, flow models are not necessary to calculate the 
benefit of avoided erosion: we simply estimate the erosion source value with and without vegetation in order to 
determine the effects of vegetation on reduced erosion.  For the other beneficiary classes, the flow models 
describe the amount of beneficial or detrimental sediment delivered or the amount of sediment carried in flowing 
water (i.e., turbidity).  Since we do not model wind-based erosion, sediment flows are modeled using a relatively 
simple hydrologic model.  We use hydrography and SRTM elevation data to derive flow direction to route water across 
the landscape and through waterways.  During flood events, sediment can be deposited in floodplains, thus floodplain 
extents and the presence of levees are used in the water and sediment routing models.  Finally, dams are included 
in the flow models, because essentially all sediment will be deposited into a reservoir as the speed of flowing 
water slows dramatically when a stream empties into a reservoir.  Whenever sediment is deposited on the landscape, 
its effect, whether beneficial or detrimental, is assigned to any users in the same spatial location as the sink. If 
no human users (people or assets) are present at the sink site, then no service is accrued by sediment deposition 
in that location.

Key outputs from the flow models include: 

1. Possible sediment flow: The downstream movement of sediment when not accounting for sediment sinks.
2. Possible sediment source: Areas which, based on the flow pattern of sediment but disregarding the effects of sinks, provide sediment which reaches downstream users who either benefit from or are damaged by sediment delivery.
3. Possible sediment deposition beneficiaries; Possible reduced sediment deposition beneficiaries; Possible reduced turbidity beneficiaries: Beneficiaries who receive beneficial or detrimental sedimentation when accounting for flow paths but not sinks.
4. Actual sediment flow: The downstream movement of sediment that accounts for sediment sinks.
5. Actual sediment source: Areas which, based on the flow pattern of sediment and accounting for sinks, provide sediment to downstream users who either benefit from or are damaged by sediment delivery.
6. Utilized deposition: Depositional areas that undergo sedimentation, receiving upstream sediment and actively performing a sediment trapping function.
7. Actual sediment deposition beneficiaries; Actual reduced sediment deposition beneficiaries; Actual reduced turbidity beneficiaries: Beneficiaries who receive beneficial or detrimental sedimentation when accounting for flow paths and sinks.
8. Absorbed sediment flow: The flow of sediment that does not reach downstream beneficiaries who benefit from either avoided detrimental sedimentation or beneficial sediment delivery.
9. Negated sediment source: Areas which, due to deposition occurring in downstream sink areas, do not provide sediment to downstream users who either benefit from or are damaged by sediment delivery.
10. Lost valuable sediment; Blocked harmful sediment; Reduced turbidity: Beneficiaries who either receive less beneficial or detrimental sediment as a result of sinks.

### Spatial data

|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|
| Model                                   | Layer                                 | Source                                                       | Spatial Extent               | Data type/Spatial resolution                 | Year                          |
|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|
| Source - All models                     | Slope                                 | Derived from global SRTM data                                | Global                       | Raster/90 x 90 m                             | n/a                           |
| Source - Dominican Republic, Madagascar | Annual precipitation                  | WorldClim                                                    | Global                       | Raster/30 x 30 arc-seconds                   | 1950-2000                     |
| Source - Western WA                     | <span />                              | PRISM/Oregon State Univ.                                     | United States                | Raster/800 x 800 m                           | 1971-2000                     |
| Source - Dominican Republic, Madagascar | Average annual runoff                 | SAGE/Univ. of Wisconsin                                      | Global                       | Raster/0.5 x 0.5 degree                      | 1955-1990                     |
| Source - Dominican Republic, Madagascar | Hydrologic soils group                | Gately (2008) using FAO soils data                           | Global                       | Raster/0.083 degrees<sup>2</sup>             | n/a                           |
| Source - Western WA                     | <span />                              | SSURGO & STATSGO soil data                                   | United States                | Rasterized shapefile at 30 x 30 m            | n/a                           |
| Source - Dominican Republic, Madagascar | RUSLE factors & avg. annual soil loss | Yang et al. (2003)                                           | Global                       | Raster/0.5 x 0.5 degree                      | 2000                          |
| Source - Western WA                     | <span />                              | U.S. EPA (2010)                                              | United States                | Vector shapefile (HUC 8 watersheds)          | Not available                 |
| <span />                                | Slope stability                       | Washington Dept. of Natural Resources                        | Washington State             | Raster/30 x 30 m                             | n/a               |
| Source - Dominican Republic, Madagascar | Soil texture                          | FAO soils                                                    | Global                       | Raster/0.083 degrees<sup>2</sup>             | n/a                           |
| Source - Western WA                     | <span />                              | SSURGO soil data                                             | Western Washington           | Rasterized shapefile at 30 x 30 m            | n/a                           |
| <span />                                | Successional stage                    | BLM/Interagency Vegetation Mapping Project                   | Western Washington & Oregon  | Raster/25 x 25 m                             | 1996                          |
| Source - Dominican Republic, Madagascar | Tree canopy cover                     | GLCF/Univ. of Maryland                                       | Global                       | Raster/1 km<sup>2</sup>                      | 2000                          |
| Source - Western WA                     | <span />                              | NLCD 2001                                                    | United States                | Raster/30 x 30 m                             | 2001                          |
| Source - Dominican Republic, Madagascar | Tropical storm probability            | CIESIN/Columbia University                                   | Global                       | Raster/2.5 x 2.5 minute                      | 1981-2000                     |
| Source - Dominican Republic             | Vegetation type                       | Deutsche Gesellschaft fur Technische Zusammenarbeit (GTZ)    | Northwest Dominican Republic | Raster/30 x 30 m                             | Not available                 |
| Source - Madagascar                     | <span />                              | FTM (Madagascar National Mapping Agency)                     | Madagascar                   | Vector shapefile                             | Mid-1990s                     |
| Source - Western WA                     | <span />                              | NLCD 2001                                                    | United States                | Raster/30 x 30 m                             | 2001                          |
|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|
| Sink - Dominican Republic, Madagascar   | Floodplain tree canopy cover          | GLCF/Univ. Maryland tree cover & Dartmouth Flood Observatory | Global                       | Raster/1 km<sup>2</sup>                      | 2000                          |
| Sink - Western WA                       | <span />                              | NLCD 2001 & FEMA Q3 Flood Data                               | United States                | Raster/30 x 30 m                             | 2001                          |
| <span />                                | Floodplain width                      | FEMA Q3 Flood Data                                           | United States                | Vector shapefile                             | Varies                        |
| Sink - Dominican Republic               | Stream gradient                       | Digital Chart of the World hydrography & SRTM slope          | Dominican Republic           | Raster/90 x 90 m                             | n/a                           |
| Sink - Madagascar                       | <span />                              | BD500 (Madagascar infrastructure data) & SRTM slope          | Madagascar                   | Raster/90 x 90 m                             | n/a                           |
| Sink - Western WA                       | <span />                              | DNR hydrography & SRTM slope                                 | Western Washington           | Raster/90 x 90 m                             | n/a                           |
|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|
| Use - Dominican Republic                | Farmland                              | Deutsche Gesellschaft fur Technische Zusammenarbeit (GTZ)    | Northwest Dominican Republic | Raster/30 x 30 m                             | Not available                 |
| Use - Madagascar                        | <span />                              | FTM (Madagascar National Mapping Agency)                     | Madagascar                   | Vector shapefile                             | Mid-1990s                     |
| Use - Western Washington                | <span />                              | NLCD 2001                                                    | United States                | Raster/30 x 30 m                             | 2001                          |
| Use & flow - DR, Madagascar             | Floodplain extents                    | Dartmouth Flood Observatory                                  | Greater Antilles, Madagascar | Vector shapefile                             | Based on 2003-2010 flood data |
| Use & flow - Western Washington         | <span />                              | FEMA Q3 Flood Data                                           | United States                | Vector shapefile                             | Varies                        |
| Sink, use & flow - Dominican Republic   | Reservoirs                            | Digitized from Global Database of Dams                       | Northwest Dominican Republic | Vector shapefile                             | 2010                          |
| Sink, use & flow - Madagascar           | <span />                              | BD500 (Madagascar infrastructure data)                       | Madagascar                   | Vector point data                            | Not available                 |
| Sink, use & flow - Western Washington   | <span />                              | Oak Ridge National Laboratory                                | United States                | Digitized reservoir locations for Western WA | 2005                          |
|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|
| Flow - All models                       | Elevation                             | SRTM                                                         | Global                       | Raster/90 x 90 m                             | n/a                           |
| Flow - Dominican Republic               | Hydrography                           | Digital Chart of the World                                   | Domninican Republic          | Vector line data                             | n/a                           |
| Flow - Madagascar                       | <span />                              | BD500 (Madagascar infrastructure data)                       | Madagascar                   | Vector line data                             | n/a                           |
| Flow - Western Washington               | <span />                              | Washington DNR                                               | Washington State             | Vector line data                             | n/a                           |
| Flow - Western Washington               | Levees                                | County GIS offices                                           | King, Lewis, Pierce counties | Vector line data                             | Varies                        |
|-----------------------------------------+---------------------------------------+--------------------------------------------------------------+------------------------------+----------------------------------------------+-------------------------------|

<div id="module-spec-references" markdown="1">

### References

Albietz, J.  2007.  Watershed protection for ecosystem services in the Makira Forest Area, Madagascar.  
Tropical Resources Bulletin 26: 21-30.

Eade, J.D.O. and D. Moran.  1996.  Spatial economic valuation: Benefits transfer using geographical 
information systems.  Journal of Environmental Management 48: 97-110.

Egoh, B, et al.  2008.  Mapping ecosystem services for planning and management.  Agriculture, Ecosystems 
and Environment 127: 135-140.

Gately, M.  2008.  Dynamic modeling to inform environmental management: Applications in energy resources 
and ecosystem services.  MS Thesis, University of Vermont, Burlington, VT.

Marcot, B.G., et al. 2006.  Guidelines for developing and updating Bayesian belief networks applied to 
ecological modeling and conservation.  Canadian Journal of Forest Research 36: 3063-3074.

Quinton, J.N., et al.  1997. The influence of vegetation species and plant properties on runoff and soil 
erosion; results from a rainfall simulation study in south east Spain. Soil Use and Management 13: 143-148. 

Renard K.G., et al. 1996. Predicting Soil Erosion by Water: A Guide to Conservation Planning with the Revised 
Universal Soil Loss Equation (RUSLE). Handbook 703, US Department of Agriculture, 404 pp. 

Tallis, H.T., et al.  2011. InVEST 2.0 beta User's Guide. The Natural Capital Project: Stanford.

U.S. Environmental Protection Agency (USEPA).  2010. EMAP-West Metric Browser.  Accessed March 3, 2010 from: 
http://www.epa.gov/esd/land-sci/emap_west_browser/EMAP-West_Metric_Browser.htm.

Wendland, K.J., et al.  2010.  Targeting and implementing payments for ecosystem services: Opportunities for 
bundling biodiversity conservation with carbon and water services in Madagascar.  Ecological Economics 69: 
2093-2107.

Yang, D., et al.  2003. Global potential soil erosion with reference to land use and climate changes.  
Hydrological Processes 17: 2913-2928.

</div>

### Acknowledgements and additional contributors

Nathaly Agosto Filion and Lee Gross developed the case study for the Dominican Republic.  Dave Batker, Jim Pittman, 
and Paula Swedeen provided data and reviewed models for the Western Washington case study.  Miro Honzak provided 
data and reviewed models for the Madagascar case study.

</div>
