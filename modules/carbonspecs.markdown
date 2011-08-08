---
layout: modulespec

title: Carbon sequestration and storage module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

The importance of ecosystems in storing and sequestering carbon is increasingly recognized 
given the threat of climate change and the rapid human-induced rise in atmospheric CO<sub>2</sub> 
concentrations (Portela et al. 2008).  Because these processes are influenced by different 
ecological processes in different regions, local carbon models have been developed in ARIES 
for Madagascar as well as four ecologically distinct areas in the United States: Orange 
County, California, Southeast Arizona and Northern Sonora's San Pedro River Watershed, 
Vermont, and Western Washington State.  In the ARIES system, the areas of carbon sequestered 
in vegetation and soils are designated as sources of the ecosystem service; the areas of 
potential stored carbon release, due to fire, land use change, deforestation, or other vegetation 
and soil disturbances, are sinks.  By subtracting the potential stored carbon release from carbon 
sequestration in a region of interest, we can compute the carbon available to offset anthropogenic 
emissions. Greenhouse gas emitters can be conceptualized as the beneficiaries of carbon 
sequestration and storage.  By mapping levels of carbon sequestration, stored carbon release, 
and anthropogenic emissions in a common unit (tonnes C/yr), we can fully describe regional carbon 
balances - the level of a region's net release or uptake of atmospheric CO<sub>2</sub>.  

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Carbon source

The term "carbon sink" is used in the scientific and popular media to
describe locations that sequester or store carbon (e.g., forests,
soils, grasslands, the ocean, or underground geologic formations). 
This definition aligns with the ARIES carbon "source" models, since 
sources are areas where an ecosystem service carrier, in
this case, carbon absorption capacity, is generated.  Ecosystems 
provide carbon sequestration capacity, which can be used by greenhouse gas
emitters to "offset" their emissions.

### Carbon sink

Carbon sinks in the ARIES framework are areas of potential stored carbon 
release, due to fire, land use change, deforestation, or other vegetation and 
soil disturbances. These sinks leave less carbon sequestration capacity available 
for offsetting anthropogenic emissions.

### Carbon beneficiaries

In ARIES, greenhouse gas emitters are defined as the users of carbon sequestration 
and storage. By releasing CO<sub>2</sub> into the atmosphere, emitters rely on 
ecosystems to absorb and store carbon in order to avoid even larger rises in 
atmospheric CO<sub>2</sub> than are currently seen.

### Carbon flow

Since carbon dioxide is a well-mixed atmospheric gas, the benefits of
carbon sequestration and storage can be enjoyed by any human
beneficiary on Earth, regardless of location. As such, no flow model
is necessary for carbon sequestration and storage.  However, for a
given region, it is possible to calculate the differential between
carbon uptake by ecosystems (sequestration minus release of stored
carbon) and anthropogenic carbon release. This information can show
whether that region has a negative or positive carbon balance, i.e.,
whether its emissions are greater or less than the amount of carbon
sequestered.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
-------------------------

### Case studies

1. Western Washington State
2. Vermont
3. Orange County, California
4. San Pedro River, Arizona and Sonora
5. Madagascar

### Model structure and assumptions

**Carbon sequestration source models.** Although carbon sequestration data are 
available globally at 1 km<sup>2</sup> resolution, we developed simple Bayesian 
network models that include the influences on carbon sequestration (e.g., vegetation, 
soils, climate).  Existing datasets can be used in ARIES to provide mean values to 
use in training finer-grained models, allowing estimation of carbon sequestration 
changes in scenarios or for up-scaled modeling of carbon sequestration where higher 
resolution input data are available.  

Based on the literature (e.g., Iverson et al. 1994, Eade and Moran 1996, Gaston et al. 1998, 
Chan et al. 2006, Naidoo and Ricketts 2006, Egoh et al. 2008, Wundscher et al. 2008, Auch 2010, 
Wendland et al. 2010, Tallis et al. 2011) and discussions with regional experts, we set carbon 
sequestration as a function of vegetation density and sequestration rate, two intermediate variables 
created to keep conditional probability tables tractable (Marcot et al. 2006).  We set 
sequestration rate as a function of soil C:N ratio and the difference between mean summer 
high and winter low (in Madagascar and Western Washington), and as a function of land cover, 
vegetation type, and actual evapotranspiration (in Orange County).  We set vegetation density 
as a function of hardwood:softwood ratio, percent tree canopy cover, and successional stage 
(in Western Washington), and percent tree canopy cover and forest degradation status (in Madagascar).  
For the San Pedro, Orange County, and Vermont agricultural carbon models, we used a collapsed number 
of variables, removing the intermediate nodes for vegetation density and sequestration rate.  For 
the San Pedro model, we estimate sequestration as a function of vegetation type, percent tree canopy 
cover, and mean annual precipitation.  For the Orange County model, we used the above noted variables 
as input nodes to sequestration rate, then combined sequestration rate with percent tree canopy cover 
to estimate annual vegetation and soil carbon sequestration. Actual evapotranspiration (AET) has been 
found to have a strong relationship with primary productivity, and therefore carbon sequestration 
(Lieth and Box 1972, Elegene 1989, Metherell et al. 1993). This is especially true in water-limited 
regions such as semi-arid biomes, as with the Orange County case study (Claudio et al. 2006, Fuentes 
et al., 2006). Vegetation type can help to predict the quantity of vegetation sequestration and storage 
capacities from expected biomass for certain plant species (Kirby and Potvin 2007).  In the Vermont 
model, we estimated sequestration as a function of vegetation carbon storage (itself a function of mean 
annual precipitation, vegetation type, and the difference between mean summer high and winter low) and 
soil C:N ratio (Liu et al. 2010).  We used Jenks natural breaks to discretize summer high-winter low, 
soil C:N ratio, and actual evapotranspiration.  We used equal intervals to discretize vegetation and 
soil carbon sequestration, hardwood:softwood ratio, and percent tree canopy cover.  

We based prior probabilities for the models on either the actual distribution of regional data (where we 
have these datasets), expert opinion (where consensus by experts was possible), or uninformed priors (where 
there was true uncertainty and a lack of consensus by experts).  We filled out conditional probability tables 
by setting extremes set at both ends (i.e., "pegging the corners," Marcot et al. 2006) and interpolating 
intermediate values.  Where possible we used expert opinion about which variables are most influential, and 
which should have the greatest influence on the contingent probability tables, and what the general level of 
uncertainty was for that system (i.e., how wide to set the distribution of values across discrete states).  
All else being equal, we set vegetation density at its highest values at greater percent tree canopy cover, 
later successional stages, more softwoods, and no forest degradation (where applicable).  We set sequestration 
rate with its highest values at higher C:N ratios, higher actual evapotranspiration, lower differences between 
mean summer high and winter low temperatures, and land cover and vegetation types with greater biomass (where 
applicable).  We set sequestration to its greatest values at high levels of vegetation density and sequestration 
rate.

**Potential stored carbon release sink models.**
We set stored carbon release as a function of vegetation and soil carbon storage (the sum of vegetation carbon 
storage and soil carbon storage) and the risk of deforestation and/or fire, with greater stored carbon release 
at higher risk and carbon storage levels.  Soil carbon storage is influenced by slope, soil pH, soil oxygen 
conditions (i.e., greater storage in wetlands where anaerobic conditions inhibit respiration), vegetation density 
(an intermediate variable incorporating tree canopy cover and degradation status in Madagascar, tree canopy cover, 
and vegetation type in the San Pedro, and successional stage, tree canopy cover, and hardwood:softwood ratio in 
Western Washington, noted as important determinants of carbon sequestration in the Pacific Northwest by Nelson et 
al. 2008), and soil carbon:nitrogen ratio.  The importance of these variables in influencing soil carbon dynamics 
has been noted by previous authors.  We set vegetation carbon storage as a function of the difference between mean 
summer high and winter low temperature (Auch 2010) and vegetation density, with population density added as an 
influence in Madagascar.   For the San Pedro, we set vegetation carbon storage as a function of mean annual precipitation 
and vegetation density.  For the Orange County model, deforestation was not considered as an influence on stored 
carbon release (though it would be included in non-urban areas within the same biome), slope was dropped as an 
influence on soil carbon storage (since slope/aspect influence AET and other water balance measurements in chaparral 
and scrub ecosystems, Miller 1947, Parsons 1973, Ng 1980), and actual evapotranspiration and percent tree canopy cover 
were added as influences on soil carbon storage.  We set vegetation carbon storage as a function of land cover, vegetation 
type, percent tree canopy cover, and AET for the Orange County model.  The Vermont model used soil tillage and biomass 
removal rate as influences on agricultural stored carbon release (Gollany et al. 2010, Gonzalez-Chavez et al. 2010).  
This model considered soil C:N ratio, biomass residue input (Hai et al. 2010), and vegetation type as influences on 
soil carbon storage and vegetation type, mean annual precipitation, and the difference between mean summer high and 
winter low temperature.

Iverson et al. (1994) and Gaston et al. (1998) provide discretization of continuous variables for slope and population 
density. Bosworth and Tricou (1999) and Darby et al. (2009) provide discretization for vegetation carbon storage in the 
Vermont carbon model.  We used Jenks natural breaks to discretize soil carbon storage, summer high-winter low, vegetation 
and soil carbon storage, soil C:N ratio, vegetation carbon storage, fire frequency, and actual evapotranspiration.  We 
used equal intervals to discretize hardwood:softwood ratio and percent tree canopy cover.  

All else being equal, we set soil carbon storage at its highest values at low or high pH, high C:N ratio, level slopes, 
high vegetation density, and on anoxic (i.e., wetland) soils, and vice versa.  We set vegetation carbon storage at its 
highest values with low differences between mean summer high and winter low temperature, high vegetation density, and 
low population density (in Madagascar).  We set stored carbon release at its highest with greater vegetation and soil 
carbon storage and greater deforestation and fire risk.

The output of the carbon sink model is the potential stored carbon release.  To better estimate actual carbon release in 
a given year, the user would need to overlay areas of fire or land use change.  Actual carbon loss could then be estimated 
for that year.  This feature will be included in carbon flow models within a future ARIES release.

**Greenhouse gas emissions use models.**
The beneficiaries of carbon sequestration and storage are greenhouse gas emitters 
who release CO<sub>2</sub> into the atmosphere. Spatially explicit data on greenhouse 
gas emissions exist for the United States.  Globally, we use population density data 
multiplied by per capita emissions for the country or sub-national region of interest.

**Carbon flow models.**
Since carbon dioxide is relatively quickly mixed in the atmosphere, the benefits of carbon 
sequestration and storage can be enjoyed by any human beneficiary on Earth, regardless of 
location.  As such, no flow model is necessary for carbon sequestration and storage.  However, 
for a given region, we can calculate the differential between carbon uptake by ecosystems 
(sequestration minus release of stored carbon) and anthropogenic carbon release.  This 
information can be used in a flow model to show whether that region has a negative or 
positive carbon balance, i.e., whether its emissions are greater or less than the amount 
of carbon sequestered.

Key model outputs from the flow models include: 

1. Carbon mitigation surplus: Calculated when local sequestration exceeds emissions plus atmospheric carbon sources.
2. Carbon mitigation deficit: Calculated when local emissions exceed net carbon uptake (sequestration minus stored carbon release).

### Spatial data

|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|
| Model                       | Layer                                    | Source                                                         | Resolution                                          | Extent                                 |      Year |
|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|
| Source - Western Washington | Slope                                    | Derived from National Elevation Dataset                        | 30 x 30 m                                           | Western Washington                     |       n/a |
| <span />                    | Soil pH                                  | SSURGO soils data                                              | 30 x 30 m                                           | Western Washington                     |       n/a |
| <span />                    | Soil oxygen conditions                   | NLCD 2001                                                      | 30 x 30 m                                           | United States                          |      2001 |
| <span />                    | Soil carbon storage                      | FAO soils                                                      | 0.0833 min<sup>2</sup>                              | Global                                 | 1970-1978 |
| <span />                    | Successional stage                       | BLM/Interagency Vegetation Mapping Project                     | 25 x 25 m                                           | Western Washington & Oregon            |      1996 |
| <span />                    | Vegetation cover                         | NLCD 2001                                                      | 30 x 30 m                                           | United States                          |      2001 |
| <span />                    | Fire frequency                           | Washington DNR                                                 | 1.5 x 1.5 km point density derived from fire points | Washington State                       | 1970-2007 |
| <span />                    | Vegetation carbon storage                | National Biomass and Carbon Dataset                            | 30 x 30 m                                           | Western Washington                     |      2000 |
| <span />                    | Soil C:N ratio                           | FAO soils                                                      | 0.0833 min<sup>2</sup>                              | Global                                 | 1970-1978 |
| <span />                    | Summer high - winter low                 | PRISM/Oregon State                                             | 800 x 800 m                                         | United States                          | 1971-2000 |
| <span />                    | Hardwood: softwood ratio                 | BLM/Interagency Vegetation Mapping Project                     | 25 x 25 m                                           | Western Washington & Oregon            |      1996 |
| <span />                    | Vegetation and soil carbon sequestration | NBII/Millennium Ecosystem Assessment                           | 1 km<sup>2</sup>                                    | Global                                 |      2000 |
|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|
| Source - Madagascar         | Slope                                    | Derived from global SRTM data                                  | 90 x 90 m                                           | Madagascar                             |       n/a |
| <span />                    | Soil pH                                  | FAO soils                                                      | 0.5 min<sup>2</sup>                                 | Global                                 | 1970-1978 |
| <span />                    | Soil oxygen conditions                   | Kew Gardens Madagascar vegetation map                          | 30 x 30 m                                           | Madagascar                             | 1999-2003 |
| <span />                    | Soil carbon storage                      | FAO soils                                                      | 0.0833 min<sup>2</sup>                              | Global                                 | 1970-1978 |
| <span />                    | Population density                       | LANDSCAN/Oak Ridge National Lab                                | 30 arc-second                                       | Global                                 |      2006 |
| <span />                    | Vegetation cover                         | GLCF/Univ. of Maryland                                         | 1 km<sup>2</sup>                                    | Global (processed only for Africa)     |      2000 |
| <span />                    | Soil C:N ratio                           | FAO soils                                                      | 0.0833 min<sup>2</sup>                              | Global                                 | 1970-1978 |
| <span />                    | Summer high - winter low                 | WorldClim                                                      | 30 arc-seconds<sup>2</sup>                          | Global                                 | 1950-2000 |
| <span />                    | Degradation status                       | FTM (Madagascar National Mapping Agency)                       | Vector shapefile                                    | Madagascar                             | Mid-1990s |
| <span />                    | Deforestation risk                       | GLCF/Univ. of Maryland                                         | 250 x 250 m                                         | Global (processed only for Madagascar) | 2001-2005 |
| <span />                    | Vegetation and soil carbon sequestration | NBII/Millennium Ecosystem Assessment                           | 1 km<sup>2</sup>                                    | Global                                 |      2000 |
|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|
| Use - Western Washington    | GHG emissions                            | VULCAN Project, Purdue Univ.                                   | 10x10 km                                            | United States                          |      2002 |
|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|
| Use - Madagascar            | Population density                       | LANDSCAN, Oak Ridge National Lab                               | 30 arc-second                                       | Global                                 |      2006 |
| <span />                    | Per capita emissions                     | Energy Information Administration: International Energy Annual | Non-spatial                                         | Global                                 |      2006 |
|-----------------------------+------------------------------------------+----------------------------------------------------------------+-----------------------------------------------------+----------------------------------------+-----------|

<div id="module-spec-references" markdown="1">

### References

Auch, W.A. 2010. Modeling the interaction between climate, chemistry,
and ecosystem fluxes at the global scale. PhD Dissertation, The
University of Vermont, Burlington, VT.

Chan, K.M.A., et al. 2006. Conservation planning for ecosystem
services. PLOS Biology 4 (11): 2138-2152.

Eade, J.D.O. and D. Moran. 1996. Spatial economic valuation: Benefits
transfer using geographical information systems. Journal of
Environmental Management 48: 97-110.

Egoh, B., et al. 2008. Mapping ecosystem services for planning and
management. Agriculture, Ecosystems and Environment 127: 135-140.

Gaston, G., et al. 1998. State and change in carbon pools in the
forests of tropical Africa. Global Change Biology 4: 97-114.

Gibbs, H.K., et al. 2007. Monitoring and estimating tropical forest
carbon stocks: Making REDD a reality. Environmental Research Letters
2: 1-13.

Iverson, L.R., et al. 1994. Use of GIS for estimating potential and
actual biomass for continental South and Southeast Asia. Pp. 67-116
in: Dale, V, ed. Effects of land use change on atmospheric CO2
concentrations: Southeast Asia as a case study. Springer Verlag: New
York.

Marcot, B.G., et al. 2006. Guidelines for developing and updating
Bayesian belief networks applied to ecological modeling and
conservation. Canadian Journal of Forest Research 36: 3063-3074.

Millennium Ecosystem Assessment (MA). 2005. Millennium Ecosystem
Assessment: Living beyond our means - Natural assets and human
well-being. Washington, D.C.: World Resources Institute.

Naidoo, R. and T.H. Ricketts. 2006. Mapping the economic costs and
benefits of conservation. PLOS Biology 4 (11): 2153-2164.

Portela, R., et al. 2008. The idea of market-based mechanisms for
forest conservation and climate change. Pp. 11-29 in: Streck, C., et
al., eds. Climate change and forests: Emerging policy and market
opportunities. Brookings Institution Press: Washington, DC.

Parry, M.L., et al. 2007. Technical Summary. Climate Change 2007:
Impacts, Adaptation and Vulnerability. Contribution of Working Group
II to the Fourth Assessment Report of the Intergovernmental Panel on
Climate Change, Parry, M.L., et al., Eds. Cambridge University Press:
Cambridge, UK.

<p>Schr&ouml;ter, D., et al. 2005. Ecosystem service supply and
vulnerability to global change in Europe. Science 310: 1333-1337.</p>

Stern, N. 2006. Part II: Impacts of climate change on growth and
development. In: Stern, N. Stern Review: The economics of climate
change. Cambridge University Press: Cambridge, UK.

Tallis, H.T., et al. 2010. InVEST 1.004 beta User's Guide. The Natural
Capital Project, Stanford.

Wendland, K.J., et al. In press. Targeting and implementing payments
for ecosystem services: Opportunities for bundling conservation with
carbon and water services in Madagascar. Forthcoming in: Ecological
Economics.

Wundscher, T., et al. 2008. Spatial targeting of payments for
environmental services: A tool for boosting conservation
benefits. Ecological Economics 65: 822-833.

</div>

### Additional contributors

Ted Auch and Serguei Krivov provided input on the initial ARIES carbon models.  
Mark Casias developed the case study for Orange County.  Sam Gorton developed 
the agricultural carbon case study for Vermont.  Dave Batker, Jim Pittman, and 
Paula Swedeen provided data and model review for the Western Washington case 
study.  Miro Honzak provided data and model review for the Madagascar case 
study.  An expert review panel including individuals from the U.S. Geological 
Survey, University of Arizona, Bureau of Land Management, and other organizations 
provided data and model review for the San Pedro case study.

</div>