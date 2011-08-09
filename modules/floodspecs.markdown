---
layout: modulespec

title: Flood regulation module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

The ARIES flood models start by mapping sources of precipitation and snowmelt, which can cause floods, 
sinks that absorb, detain, or promote infiltration of floodwater, and beneficiaries that may receive 
flood mitigation services.  Sink models incorporate vegetation and soil data that describe how well 
different areas can promote infiltration and evapotranspiration.  Vegetation and soils provide what 
is collectively termed green infrastructure, which acts along with gray infrastructure such as dams 
and detention basins that detain flood waters.  Flood flow models spatially link sources of floodwater, 
beneficial sinks, and beneficiaries in the landscape.  These models account for the location and width 
of floodplains and the effects of levees, which protect assets at risk behind levees but at the same 
time increase the energy of the water conveyed downstream, potentially increasing downstream damage.  
Different beneficiary groups may be protected from flooding - crops, privately owned housing or other 
buildings, publicly owned infrastructure, and human life.  GIS data showing riverine flood zones and 
maps of population, agriculture, and structures allow beneficiaries to be mapped.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Flood source

Precipitation and snowmelt, which can cause floods.

### Flood sink

Areas that absorb, detain, or promote infiltration of floodwater, including vegetation 
and soils that can promote infiltration and evapotranspiration (green infrastructure) 
and dams and detention basins (gray infrastructure) that can detain flood waters.

### Flood beneficiaries

Beneficiaries of flood regulation include residents, farmers, and users of public 
infrastructure in flood zones.

### Flood flow

Flood flows are routed across the landscape through topography and stream networks. 
Once floodwater is in a stream, it can overtop the streambanks, depending on the 
amount of floodwater, floodplain width, and the presence of levees. Flood damage 
can be attributed to upstream flood sources, and mitigated damage can be attributed 
to upstream flood sinks, which provide the ecosystem service of flood regulation.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
-------------------------

### Case studies

1. Western Washington State
2. Orange County, California

### Model structure and assumptions

**Flood source models.** We use annual precipitation is the source of floodwater. Flood regulation is 
For event-based flood modeling, snowmelt is an extremely important variable in seasonally cold-weather 
climates, such as Western Washington.  Since data limitations prevent event-based flood modeling in 
ARIES, snow presence and snowmelt are not currently included in the flood source model.  

**Flood sink models.** Past ecosystem services studies have essentially mapped flood sinks using spatial 
data; we drew on these approaches in developing our sink models.  Eade and Moran (1996) mapped flood 
regulation based on soil drainage classifications, while Chan et al. (2006) did so by estimating percent 
natural land cover, percent natural land cover within riparian zones, distance to the 100-year floodplain, 
percent agricultural land, and housing units in the 100-year floodplain.  Finally, Boyd and Wainger (2003) 
mapped flood regulation using spatial data including floodplain locations, housing and commercial units 
and value, percent floodplain as impervious and wetland.  Boyd and Wainger also included an environmental 
justice component to their measures, by mapping median income and percent black or Hispanic populations 
within their impacted area.  We drew on these studies to conceptualize our flood sink models, then extended 
these approaches by including additional variables considered by others to be important for flood regulation 
(Eade and Moran 1996, Boyd and Wainger 2003, Chan et al. 2006, Bradshaw et al. 2007).

We defined flood sink value, the top-level output of the sink model, as the sum of green infrastructure 
storage (the sum of infiltration, absorption, detention, or evapotranspiration of potential flood waters by 
vegetation, soils, and floodplains) and gray infrastructure storage (the sum of storage in detention basins 
and reservoirs). Both gray and green infrastructure can be "saturated" when their individual components are 
at full capacity. Because of this, we added the mean days of precipitation per year as an influence to green 
and gray infrastructure storage in the Western Washington model.  This accounts for the fact that green and 
gray infrastructure are likely to be saturated for more of the year in regions where precipitation is more 
evenly distributed over the course of a year, allowing soil moisture to remain more temporally uniform.  We 
did not include this variable in the Orange County model, since we assume the system to be "unsaturated" 
for most of the year, since Southern California experiences low annual rainfall and flood events are 
extremely flashy.

By computing the difference between precipitation and runoff (which accounts for vegetation and soil 
characteristics), we can estimate the contribution of green infrastructure to flood mitigation.  We can thus 
use the difference between precipitation and runoff as training data for the Bayesian network.  Models such 
as the Curve Number method (CN, SCS 1972), which incorporates data on precipitation, hydrologic soils group, 
and land use-land cover, can also be used to calculate runoff.

We set soil infiltration as a function of impervious surface cover, slope, and hydrologic soils group. These 
variables have been routinely recognized as predictive variables for potential soil infiltration (i.e., USACE 
1998, Tetra Tech, Inc. 2005, Laton et al. 2006, BOR 2007).  We considered adding water table depth (available 
from SSURGO/STATSGO data) as an influence on infiltration but ultimately decided not to include it to maintain 
tractability in the contingent probability table. Evapotranspiration reduces soil moisture, thereby allowing 
increased infiltration.  In addition, it serves as a proxy for other flood mitigation processes due to the 
presence of vegetation.  We set evapotranspiration as a function of percent tree canopy cover and vegetation 
type (in both models) and added influences for successional stage and vegetation height for the Western Washington 
model.  Jones and Post (2004) and Moore and Wondzell (2005) note the importance of forest cover and successional 
stage as drivers of hydrologic processes in Pacific Northwest forests.

We discretized mean days of precipitation per year using Jenks natural breaks and estimated its priors on a 
review of the data for Western Washington.  We reviewed GIS data for Orange County and Western Washington to 
derive priors for impervious surface cover, slope, and hydrologic soils group. We discretized impervious surface 
cover to account for ecological thresholds typically present when impervious surface exceeds 10% (Booth and 
Jackson 1997). We used equal intervals to discretize percent tree canopy cover and Jenks natural breaks to 
discretize vegetation height for Western Washington. We estimated priors based on spatial data for percent tree 
canopy cover, successional stage, vegetation height, and vegetation type.

For the soil infiltration contingent probability table, we set the highest values of infiltration at low 
impervious surface cover and slope and hydrologic soils groups A and B.  We set the lowest values for infiltration 
under opposite conditions and interpolated intermediate values.  We set the evapotranspiration contingent 
probability table to its greatest values in cases of greater percent tree canopy cover, later successional stage, 
tall vegetation (where applicable), and wetlands, and vice versa, and interpolated intermediate values.  We set 
evapotranspiration as slightly lower than wetlands for forests, grassland, and shrubland, and substantially lower 
for developed and cultivated land use types.  

We set evapotranspiration and soil infiltration as equivalent influences on the green infrastructure storage 
contingent probability table.  In the Western Washington model, we set mean days of precipitation per year as 
a strong influence on the contingent probability tables for both gray and green infrastructure storage (i.e., 
much greater storage when there were very low or low mean days of precipitation per year, and vice versa).  
We summed values for dam and detention basin storage to quantify gray infrastructure storage, and added this 
to the value of green infrastructure storage to estimate the total flood sink.

[![Bayesian network model for flood sinks in Western Washington. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files.](/images/bn/FloodSinkPuget.gif)](/downloads/FloodSinkPugetAnnual.xdsl)
{: .bayesnet }

**Flood use models.** Beneficiaries of flood regulation can be mapped using spatial data and simple GIS 
overlay operations, eliminating the need for more complex approaches.  In these case studies, we identified 
different beneficiary classes, including farmers, residents, and municipalities with public infrastructure 
located within the floodplain boundaries.  We mapped beneficiaries in both the 100-year and 500-year 
floodplains in order to differentiate between levels of risk from catastrophic floods of different sizes.

**Flood flow models.** The source and sink models determine the quantity (in mm/yr) of precipitation falling 
on the landscape and absorbed or detained by the landscape, while the use model defines the location of potential 
flood regulation beneficiaries.  The flow model routes water from its source locations through the watershed 
based on the topography of the location.  Once the flow of water moving across a landscape intersects a stream, 
its movement is no longer determined by topography and instead follows the direction of the streambed.  Once 
floodwater is in a stream, it can overtop the streambanks, depending on the amount of floodwater, floodplain 
width, and the presence of levees.  If the downstream flow reaches a dam, floodwater is temporarily detained 
unless excess water in an already-full reservoir must be released downstream.  If floodwater reaches a user, 
it causes damage.  This damage can be attributed to upstream flood sources, and mitigated damage can be attributed 
to upstream flood sinks, which provide the ecosystem service of flood regulation.

Key outputs from the flow models include: 

1. Potentially damaging flood flow: The flow route of floodwater across the landscape in the absence of sinks.
2. Potentially damaging runoff: Runoff capable of harming people or damaging property when accounting for flow paths but not sinks.
3. Potential flood damage received: People and property receiving damage when accounting for sources of floodwater and its flow path but not accounting for the action of sinks that reduce potential damage from floodwater.
4. Actual flood flow: The flow route of floodwater across the landscape in the presence of sinks.
5. Flood damaging runoff: Runoff that actually harms people or damages property when accounting for flow paths and sinks.
6. Utilized runoff mitigation: Sinks that actively reduce floodwater, providing the benefit of reduced flood damage for people.
7. Flood damage received: Actual damage received by people and property when accounting for sources of floodwater, flow paths, and sinks encountered.
8. Absorbed flood flow: Flood flows that are absorbed by sinks prior to reaching vulnerable human beneficiaries.
9. Flood mitigated runoff: The portion of the total runoff that is absorbed, detained, or slowed by the action of flood sinks.
10. Flood mitigation benefits accrued: People or economically valuable assets who are spared from flood damage due to the flood regulation activity of sinks.

### Spatial data

|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|
| Model                     | Layer                                    | Source                                         | Spatial Extent                                                                      | Data type/Spatial resolution                       |                                                     Year |
|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|
| Source - All models       | Annual precipitation                     | PRISM/Oregon State Univ.                       | United States                                                                       | Raster/800 x 800 m                                 |                                                1971-2000 |
|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|
| Sink - All models         | Average annual actual evapotranspiration | SAGE/Univ. of Wisconsin                        | Global                                                                              | Raster/0.5 x 0.5 degree                            |                                                1950-1999 |
| <span />                  | Average annual runoff                    | SAGE/Univ. of Wisconsin                        | Global                                                                              | Raster/0.5 x 0.5 degree                            |                                                1955-1990 |
| <span />                  | Dam storage                              | National Atlas of the United States            | United States                                                                       | Rasterized point data                              |                                                     2006 |
| <span />                  | Hydrologic soils group                   | SSURGO & STATSGO soil data                     | United States                                                                       | Rasterized shapefile at 30 x 30 m                  |                                                      n/a |
| <span />                  | Impervious surface cover                 | NLCD 2001                                      | United States                                                                       | Raster/30 x 30 m                                   |                                                     2001 |
| <span />                  | Slope                                    | Derived from global SRTM data                  | Global                                                                              | Raster/90 x 90 m                                   |                                                      n/a |
| <span />                  | Tree canopy cover                        | NLCD 2001                                      | United States                                                                       | Raster/30 x 30 m                                   |                                                     2001 |
| Sink - Orange County      | Average annual soil infiltration         | LA Basin Groundwater Augmentation Model (GWAM) | West Coyote Hills site                                                              | Vector shapefile                                   |                                                1951-2002 |
| <span />                  | Vegetation type                          | U.S. Forest Service                            | Northern Orange & Southern LA Counties                                              | Vector shapefile                                   |                                                     2003 |
| Sink - Western WA         | Vegetation type                          | NLCD 2001                                      | United States                                                                       | Raster/30 x 30 m                                   |                                                     2001 |
| <span />                  | Detention basins                         | County GIS offices                             | King, Pierce, San Juan counties                                                     | Rasterized point data                              |                                                   Varies |
| <span />                  | Mean days of precipitation per year      | PRISM/Oregon State Univ.                       | United States                                                                       | Vector shapefile>                                  |                                                1971-2000 |
| <span />                  | Successional stage                       | BLM/Interagency Vegetation Mapping Project     | Western Washington & Oregon                                                         | Raster/25 x 25 m                                   |                                                     1996 |
| <span />                  | Vegetation height                        | Puget Sound LIDAR Consortium                   | Parts of Western Washington                                                         | Raster/3 foot2 & 6 foot2, downsampled to 30 x 30 m |                                                2000-2006 |
|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|
| Use - All models          | Farmland                                 | NLCD 2001                                      | United States                                                                       | Raster/30 x 30 m                                   |                                                     2001 |
| <span />                  | Floodplain extents                       | FEMA Q3 Flood Data                             | United States                                                                       | Vector shapefile                                   |                                                   Varies |
| <span />                  | Highways                                 | TIGER/Line files                               | United States                                                                       | Vector line data                                   |                                                     2000 |
| <span />                  | Railways                                 | TIGER/Line files                               | United States                                                                       | Vector line data                                   |                                                     2000 |
| Use - Western Washington  | Presence of housing                      | County assessors' offices                      | Clallam, Grays Harbor, Jefferson, King, Kitsap, Mason, Snohomish, Thurston cos., WA | Rasterized shpefile at 100 x 100 m                 | 2004 (Kitsap Co.), 2006 (King Co.); uncertain for others |
|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|
| Flow - All models         | Dams                                     | National Atlas of the United States            | United States                                                                       | Rasterized point data                              |                                                     2006 |
| <span />                  | Elevation                                | SRTM                                           | Global                                                                              | Raster/90 x 90 m                                   |                                                      n/a |
| <span />                  | Floodplain extents                       | FEMA Q3 Flood Data                             | United States                                                                       | Vector shapefile                                   |                                                   Varies |
| Flow - Orange County      | Hydrography                              | Caltrans Teale Data Center                     | California                                                                          | Vector line data                                   |                                                      n/a |
| Flow - Western Washington | <span />                                 | Washington DNR                                 | Washington State                                                                    | Vector line data                                   |                                                      n/a |
| <span />                  | Levees                                   | County GIS offices                             | King, Lewis, Pierce counties                                                        | Vector line data                                   |                                                   Varies |
|---------------------------+------------------------------------------+------------------------------------------------+-------------------------------------------------------------------------------------+----------------------------------------------------+----------------------------------------------------------|

<div id="module-spec-references" markdown="1">

### References

Booth, D.B. and C.R. Jackson.  1997.  Urbanization of aquatic systems: Degradation thresholds, stormwater detection, 
and the limits of mitigation.  Journal of the American Water Resources Association 33 (5): 1077-1090.

Boyd, J and L. Wainger.  2003.  Measuring ecosystem service benefits: The use of landscape analysis to evaluate 
environmental trades and compensation.  Discussion Paper 02-63, Resources for the Future: Washington, DC.

Bureau of Reclamation (BOR) (2007). Los Angeles Basin Ground Water Augmentation Model: User's Manual and Technical 
Documentation, Version 4.1.40. Bureau of Reclamation, Technical Services Center, Water Resources Department: 
Denver, CO.

Bradshaw, C.J.A., et al.  2007.  Global evidence that deforestation amplifies flood risk and severity in the 
developing world.  Global Change Biology 13: 2379-2395.

Chan, K.M.A., et al.  2006.  Conservation planning for ecosystem services.  PLOS Biology 4 (11): 2138-2152.

Eade, J.D.O. and D. Moran.  1996.  Spatial economic valuation: Benefits transfer using geographical information 
systems.  Journal of Environmental Management 48: 97-110.

Jones, J.A. and D.A. Post.  2004.  Seasonal and successional streamflow response to forest cutting and regrowth 
in the northwest and eastern United States. Water Resources Research 40: W052031-W0520319.

Laton, W., et al.  2006.  Estimating runoff quantities for flow and volume- based BMP design. Journal of the 
American Institute of Hydrology 22 (104): 131-144.

Moore, R.D. and S.M. Wondzell.  2005. Physical hydrology and the effects of forest harvesting in the Pacific 
Northwest: A review.  Journal of the American Water Resources Association 41 (4): 763-784.

Soil Conservation Service (SCS).  1972.  National Engineering Handbook, Section 4, Hydrology.  SCS: Washington, 
DC.

Tetra Tech, Inc.  2005.  Model Development for Simulation of Wet-Weather Metals Loading from the San Gabriel 
River Watershed. Prepared for USEPA Region 9 and the Los Angeles Regional Water Quality Control Board by Tetra 
Tech, Inc., San Diego: California.

</div>

### Acknowledgements and additional contributors

Mark Casias developed the Orange County case study.  Dave Batker, Jim Pittman, and Paula Swedeen provided data and 
model review for the Western Washington case study.

</div>
