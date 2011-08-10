---
layout: modulespec

title: Recreation module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

In the ecosystem services literature, aesthetic values are often defined as the value derived from views 
Bourassa et al. 2004) or proximity to open space (Fausold and Lileholm 1999, McConnell and Walls 2005, 
Brander and Koetse 2007).  These values accrue to housing or property values and are commonly measured using 
hedonic pricing.  Homeowners may gain some combination of benefits through sensory enjoyment of views of 
nearby open space, proximity to open space for recreation, or privacy.  Park visitors (e.g., hikers) and 
drivers along scenic highways may also value scenic views (Walsh et al. 1990).  The appreciation of scenic 
views for recreation by these groups is addressed in the ARIES recreation module  Spatial mapping of homeowners 
is relatively straightforward, as housing units, open space, and viewsheds have all been frequently analyzed in 
hedonic studies of amenity values.  However, the spatial flow characteristics of open space proximity and 
viewsheds differ, with the value of proximity declining with distance from an accessible parcel of open space, 
while view values rely on an unimpeded line of sight to visually significant objects such as mountains or water 
bodies.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Recreation source

Open space, whose type and quality determine its relative value for 
beneficiaries.

### Recreation sink

The presence of highways, which at the neighborhood scale highways can 
reduce access to and enjoyment of open space.

### Recreation beneficiaries

Residents who live near and have access to open space.

### Recreation flow

The movement of people from residences to open space.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
--------------------------

### Case studies

1. Vermont
2. San Pedro River Watershed, Arizona

### Model structure and assumptions

**Recreation source models: Birding, hunting, and wildlife viewing.** Aesthetic proximity values depend foremost on having open space in 
some form.  For the San Pedro, major open space types include desert scrub, grassland, farmland, parks, 
forests and woodlands, and riparian and wetlands.  For Western Washington these include forests, wetlands, 
beach, riverfront, lakefront, golf courses, cemeteries, farmland, or parks.  We use the intermediate variable 
"Open Space Resource" to aggregate these open space types.  Along with the type of open space, its quality 
matters in determining proximity value. We aggregated several independent measures of open space quality - 
open space area and formal protection for both models, water quality and crime for Western Washington, and 
fire threat for the San Pedro - into a single intermediate variable, "Resource Quality," in order to maintain 
tractability of conditional probability tables. Anderson and West (2002) found park value to increase with 
size, though Brander and Koetse (2007) note that open space value on a per hectare basis declines as its size 
grows.  All else being equal, we would generally expect lower per-area value in the vast open landscapes of the 
rural Southwest than around urban areas.  A series of papers from Maryland noted that homeowners more highly 
value land that is permanently protected over land that may be developed in the future (Irwin and Bockstael 2001, 
Irwin 2002, Geoghegan 2002, Geoghegan et al. 2003).  Troy and Grove (2008) found crime to reduce the value of 
parks in urban areas in Baltimore, a result that could also potentially apply to older, economically distressed 
suburbs.  We do not include crime in the San Pedro model since the region lacks large urban centers with higher 
crime rates.  Finally, poor water quality could reduce the value of open space due to odors, public health 
concerns, or reduced recreational opportunities.  We did not include water quality in the San Pedro model since, 
given its rarity, we assume the presence of water of almost any quality to indicate higher quality open space.  
We added the variable "fire threat" to the San Pedro model.  In fire-prone regions of the west, living near 
fire-prone ecosystems is a risk that may be understood by landowners, leading to lower perceived open space 
proximity value (Loomis 2004).   Finally, we set the top node, "Theoretical Proximity Source" as a function of 
Open Space Resource and Resource Quality.

We derived prior probability distributions for the presence/absence of open space types based on 2001 NLCD and 
local land use data (i.e., for parks, lakefront, or riverfront) in the San Pedro and Western Washington.  The 
Open Space Resource node uses a NoisyMax node (Pearl 1988), based on the simplifying assumption that the most highly 
valued land use type will be representative of the total value (i.e., there are no synergistic effects among value 
components, so a high probability of presence of the most valued nearby landscape component can be taken as the 
likelihood of a high total potential value).  We set the highest values in the contingent probability table for 
Open Space Resource for beach, parks, riparian, lakefront, and riverfront (which frequently feature public access 
and open water), the lowest values for farmland (known to provide disamenities like noise and odors), cemeteries 
and golf courses (which may have limited public access), desert scrub and grasslands (extremely abundant vegetation 
types in the Southwest) and intermediate values for wetlands and forests. In a global meta-analysis of proximity 
studies, Brander and Koetse (2007) found parks to be more highly valued than forests, which were more highly valued 
than farmland.  However, these relative values could be adjusted for different parts of the world based on local 
preferences and hedonic studies indicating relative values of different types.

We assume that 25% of the landscape is protected in Western Washington and 60% was protected in Southeast Arizona. 
We assumed that 10% of parks are located in urban areas in Western Washington where crime may be problematic. We 
discretized park size by Jenks natural breaks.  For Western Washington, we assumed that smaller open space parcels 
are most abundant, with the abundance of parks in a particular size class declining as park size grows. These 
assumptions were reversed for Southeast Arizona, since in the rural landscape few small open space parcels and many 
large open space parcels would be found.  We assumed that 85% of open space has no open water, and assume that equal 
areas meet water quality standards, are waters of concern, or require a TMDL (indicating poor water quality).  We 
assumed that 75% of the landscape is at a high fire threat.  We assumed that the highest "Resource Quality" will occur 
in large, formally protected open space with no water quality or crime problems and low fire risk, and that the lowest 
value will occur in small, unprotected parcels of open space with crime, water quality problems and/or higher fire 
frequency.  We thus peg the corners of the contingent probability table for Resource Quality and fill in intermediate 
values (Marcot et al. 2006).  We assume that Formal Protection will have the greatest influence on Resource Quality, 
since unprotected land is potentially much less valuable for its open space quality.  We assume the other variables 
have relatively less influence on Resource Quality.  Finally, in defining the contingent probability table for Theoretical 
Proximity Source, we note that high-value land use-land cover types and high quality (represented through protected status, 
area, crime, water quality, and fire threat) will produce the highest theoretical proximity source value and vice versa, 
peg the corners, and interpolate intermediate values.

[![Bayesian network model for open space proximity sources in Western Washington. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files.](/images/bn/ProxSourcePuget.gif)](/downloads/ProximitySourcePuget.xdsl)
{: .bayesnet }

**Recreation source models: Viewsheds.** 

**Recreation sink models.** If ease of access, privacy, and quiet associated with open space are the 
attributes that lead to proximity value, highways that prevent access or disturb aesthetic quality would act 
as sinks.  We assume that highways deplete 50% of the potential open space proximity value to users if they are 
located between a user and potentially valued open space.  We use a highways data layer, so no model is required.

**Recreation use models: Birding, hunting, and wildlife viewing.** For aesthetic proximity use to occur, housing must be located near open space.  
The use model identifies housing, its value, and urban proximity (e.g., urban, suburban, or rural setting) as a 
proxy for relative scarcity of open space as determinants of proximity use.  Numerous authors have noted that open 
space is valuable in urban settings where user populations and scarcity are greater and less valuable in rural settings 
(Brander and Koetse 2007).

We discretized housing value and population density, a proxy for urban proximity, using Jenks natural breaks.  Based 
on relevant spatial data, we set priors to reflect 5, 25, and 70% of the landscape in Western Washington and 2.5, 7.5, 
and 90% in the San Pedro as urban, suburban, and rural settings, respectively.  We assume that 75% housing values are 
most typically at moderate to low levels, with 15% at very low levels and 10% at high or very high levels.  Finally, 
we assumed that 10% of the landscape has housing in Western Washington and that 2% of the landscape has housing in the 
San Pedro.  We set the contingent probability table for "Aesthetic Proximity Use," the top node by first requiring 
housing to be present in order to have value.  We then set value to decline more quickly moving from urban to rural 
and less quickly moving from high to lower classes of housing values.  Brander and Koetse (2007) found per capita 
income to be a positive but nonsignificant independent variable in a meta-analysis of proximity values.  We thus include 
housing value in our models, but make its prior influence on proximity use value weaker than the presence of housing or 
urban proximity.  Training the models to real data can be used to reveal the actual weight of the variable in each use case.

[![Bayesian network model for open space proximity use in Western Washington. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files.](/images/bn/ProxUsePuget.gif)](/downloads/ProximityUsePuget.xdsl)
{: .bayesnet }

**Recreation use models: Viewsheds.** 

**Recreation flow models.** Most studies have found proximity value to decline with distance, as housing 
directly adjacent to open space would be more highly valued than housing a short walk from open space, which would 
be more valued than housing a long walk or drive from open space.  Most of the studies reviewed by McConnell and 
Walls (2005) examined housing within a 0.5 to 1-mile radius of open space, and note that open space-related amenity 
values drop rapidly past that distance.  Brander and Koetse's (2007) meta-analysis used 100 m change in the distance 
to open space as a dependent variable in their analysis.  We thus represent aesthetic proximity value using a walking 
simulation model.  Distance to open space starts off at its full value at the edge of an open space area but drops off 
quickly with increasing linear distance during the first 0.5 mile and slower decay from 0.5 to 1 mile, with the value 
reaching zero at a distance of 1 mile from the open space parcel. While Sengupta and Osgood (2003) describe the value of 
proximity to rivers in the arid Southwest as having a less steep distance decay function, for the time being we use a 
uniform distance decay function in the proximity flow model.

Key outputs from the flow models include: 

1. Possible proximate open space: The density of service flow along each walking path between an open space and user, before accounting for highways that limit local access.
2. Accessible open space: Open space providing value when accounting for proximity and the location of homeowners but not highways that limit local access.
3. Open space proximate homeowners: Homeowners benefiting from proximity after accounting for sources of open space and their flow paths, but before accounting for highways that limit local access.
4. Accessible proximity: The density of service flow along each walking path between an open space and user, when accounting for sinks and flow paths.
5. Enjoyed open space: Open space providing proximity when accounting for flow paths, sinks, and the location of beneficiaries.
6. Blocking proximity sink: Highways that actually separate residences from open space.
7. Homeowners with proximate open space: Homeowners benefiting from proximity after accounting for sources of open space, sinks, and flow paths.
8. Homeowners without proximate open space: Homeowners lacking any proximity to open space (typically in urban areas).
9. Blocked proximity: The density of service flow along each walking path between an open space and user that is blocked by highways.
10. Blocked open space: Open space that is blocked by the action of sinks (highways).
11. Homeowners with blocked proximity: Homeowners who would receive benefits from open space proximity but have their access blocked by highways.

### Spatial data

|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Model              | Layer                                             | Source                                                              | Spatial Extent     | Data type/Spatial resolution |          Year |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Source - San Pedro | Amphibian, bird, mammal, reptile species richness | USGS Southwestern Biological Center Sonoran Desert Research Station | AZ, CO, NM, NV, UT | Vector shapefile             |     1999-2001 |
| <span />           | Habitat for game species                          | Southwest Regional GAP Analysis LULC (SWReGAP)                      | AZ, CO, NM, NV, UT | Raster/240 x 240 m           |     1999-2001 |
| <span />           | Public lands                                      | Arizona Geographic Information Council                              | Arizona            | Vector shapefile             |          2000 |
| <span />           | Rare & charismatic bird habitat presence          | Southwest Regional GAP Analysis LULC (SWReGAP)                      | AZ, CO, NM, NV, UT | Raster/240 x 240 m           |     1999-2001 |
| <span />           | Riparian condition class                          | Stromberg et al. (2006)                                             | SPRNCA             | Vector shapefile             |     2001-2004 |
| <span />           | Springs                                           | Arizona Geographic Information Council                              | Arizona            | Rasterized point data        |           n/a |
| <span />           | Hydrograpy                                        | National Hydrography Dataset                                        | Arizona            | Vector line data             |           n/a |
| Source - Vermont   | <span />                                          | National Hydrography Dataset                                        | Vermont            | Vector line data             |           n/a |
| <span />           | Elevation                                         | SRTM                                                                | Global             | Raster/90 x 90 m             |           n/a |
| <span />           | Lakes & ponds                                     | National Hydrography Dataset                                        | Vermont            | Vector shapefile             |           n/a |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Sink - Vermont     | Developed land                                    | NLCD 2001                                                           | United States      | Raster/30 x 30 m             |          2001 |
| <span />           | Energy infrastructure                             | Vermont Center for Geographic Information)                          | Vermont            | Vector line data             |          2003 |
| <span />           | Transportation infrastructure                     | Vermont Agency of Transportation                                    | Vermont            | Vector line data             |          2010 |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Use - All models   | Population density                                | U.S. Census Bureau                                                  | Arizona            | Vector shapefile             |     2000-2007 |
| Use - Vermont      | Scenic viewpoints                                 | Digitized locations of VT peaks with scenic views                   | Vermont            | Rasterized point data        |           n/a |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Flow - All models  | Roads: speed limits/travel capacity               | TIGER/Line files                                                    | United States      | Vector line data             |          2000 |
| Flow - San Pedro   | <span />                                          | Arizona Geographic Information Council                              | Arizona            | Vector line data             |          2009 |
| <span />           | Trails                                            | BLM                                                                 | SPRNCA             | Vector line data             | Not available |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|

<div id="module-spec-references" markdown="1">

### References

Anderson, S.T. and S.E. West. 2002. The value of open space proximity
and size: City versus suburbs. Working paper: Macalester College,
Saint Paul, MN.

Benson E.D., et al. 1998. Pricing residential amenities: the value of
a view. Journal of Real Estate Finance and Economics 16: 55-73.

Bourassa, S.C., et al. 2004.  What's in a view? Environment and
Planning A 36: 1427-1450.

Brander, L.M. and Koetse, M.J.  2007.  The value of urban open space: 
Meta-analysis of contingent valuation and hedonic pricing results.  
IVM Working Paper I. 07/03.

Fausold, C.J. and R.J. Lilieholm.  1999.  The economic value of open 
space: A review and synthesis.  Environmental Management 23 (3): 307-320.

Geoghegan, J. 2002. The value of open spaces in residential land
use. Land Use Policy 19: 91-98.

Geoghegan, J., et al. 2003.  Capitalization of open spaces into
housing values and the residential property tax revenue impacts of
agricultural easement programs. Agricultural and Resource Economics
Review 32 (1): 33-45.

<p>Gr&ecirc;t-Regamey, A., et al. 2008.  Linking GIS-based models to
value ecosystem services in an Alpine region. Journal of Environmental
Management 89: 197-208.</p>

Irwin, E.G. 2002. The effects of open space on residential property
values. Land Economics 78 (4): 465-480.

Irwin, E.G. and N.E. Bockstael.  2001. The problem of identifying land
use spillovers: Measuring the effects of open space on residential
property values. American Journal of Agricultural Economics 83 (3):
698-704.

Loomis, J.  2004.  Do nearby forest fires cause a reduction in residential 
property values?  Journal of Forest Economics 10 (3): 149-157.

Marcot, B.G., et al. 2006.  Guidelines for developing and updating 
Bayesian belief networks applied to ecological modeling and conservation.  
Canadian Journal of Forest Research 36: 3063-3074.

McConnell, V. and M. Walls. 2005.  The value of open space: Evidence
from studies of nonmarket benefits. Resources for the Future:
Washington, DC.

Pearl, J.  1988.  Probabilistic reasoning in intelligent systems: 
Networks of plausible inference.  Morgan-Kaufmann: San Francisco.

Sengupta, S. and Osgood, D.E. 2003. The value of remoteness: a hedonic 
estimation of ranchette prices. Ecological Economics 44, 91-103.

Steinitz, C., et al. 2003.  Alternative futures for changing
landscapes: The Upper San Pedro River Basin in Arizona and Sonora.
Island Press: Washington, DC.

Stromberg, J.C., et al.  2006.  Status of the riparian ecosystem in 
the Upper San Pedro River: Application of an assessment model.  
Environmental Monitoring and Assessment 115: 145-173.

Troy, A. and J.M. Grove. 2008.  Property values, parks, and crime: A
hedonic analysis in Baltimore, MD. Landscape and Urban Planning 87:
233-245.

U.S. Forest Service (USFS). 1995.  Landscape aesthetics: A handbook
for scenery management. USDA-Forest Service Agriculture Handbook
Number 701.

Walsh, R.G., et al. 1990. The Consumptive Value of Travel Time on
Recreation Trips. Journal of Travel Research 29 (1): 17-24.

Wundscher, T., et al. 2008.  Spatial targeting of payments for 
environmental services: A tool for boosting conservation benefits.  
Ecological Economics 65: 822-833. 

</div>

### Acknowldegements and additional contributors

Dave Batker, Jim Pittman, and Paula Swedeen provided data and model review for the Western 
Washington case study.  An expert review panel including individuals from the U.S. Geological 
Survey, University of Arizona, Bureau of Land Management, and other organizations provided 
data and model review for the San Pedro case study.

</div>
