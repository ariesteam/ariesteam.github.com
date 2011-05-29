---
layout: modulespec

title: Carbon sequestration and storage module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

<p>The importance of carbon sequestration and storage by ecosystems is
increasingly recognized given the threat of climate change. Carbon
sequestration and storage help provide a more stable global climate by
taking up greenhouse gases and keeping them out of the atmosphere.
Specific beneficiaries of climate stability can be identified,
particularly in regions most vulnerable to climate change. Regions and
human populations vulnerable to climate change are described in the
ecosystem services and climate change literature (MA 2005,
Schr&ouml;ter et al.  2005, Stern 2006, Parry et al. 2007). These
groups include coastal populations at risk of sea level rise and more
intense storms, populations dependent on glaciers and snowpack for
water supplies, populations in arid regions at risk of drought, and
populations using infrastructure built on permafrost, among others. A
variety of spatial data layers enable the mapping of these groups
vulnerable to climate change. Alternatively, greenhouse gas emitters
can be conceptualized as the beneficiaries of carbon sequestration and
storage. Since greenhouse gas emitters benefit from the waste
absorption capacity of the biosphere, carbon sequestration and storage
can be divided among emitters. Existing and proposed systems to cap
and assign property rights to atmospheric greenhouse gas emissions use
this framework.</p>

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Carbon sinks

The term "carbon sink" is used in the scientific and popular media to
describe locations that sequester and store carbon (e.g., forests,
soils, grasslands, the ocean, or underground geologic formations as
carbon sinks).This definition is more in line with the carbon "source"
models, since sources are areas where an ecosystem service carrier, in
this case, carbon absorption capacity, is generated.  However, using
the ARIES framework, where sinks denote regions that deplete an
ecosystem service carrier en route from an ecosystem to its human
users, this service has no "sink." Ecosystems provide carbon
sequestration and storage capacity, which are used by greenhouse gas
emitters to "offset" their emissions.

### Net carbon uptake

Net carbon is the difference between vegetation and soil carbon
storage and stored carbon release (i.e., due to deforestation, land
use change, or fire) - both of which are rates or flows.

### Carbon use

There are several ways to describe the users of carbon sequestration
and storage. For example, greenhouse gas emitters who release
CO<sub>2</sub> into the atmosphere rely on ecosystems to absorb and
store carbon in order to avoid even larger rises in atmospheric
CO<sub>2</sub> than are currently seen. A healthy planetary
atmospheric carbon balance also helps maintain a stable climate.  We
can thus map all people on the planet as beneficiaries of a stable
climate, or map groups particularly vulnerable to climate change
(e.g., residents of coastal regions vulnerable to sea level rise,
regions dependent on snowpack for water supply). Our initial carbon
sequestration and storage use maps simply display greenhouse gas
emitters. GIS datasets of greenhouse gas emissions exist for the
United States (. Globally, we can use maps of population density
multiplied by per capita emissions for the country or sub-national
region of interest.

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

### Explanation

We conceptualize the provision of this service as carbon sequestration
and storage by terrestrial ecosystems (i.e., within vegetation and
soils). In order to combine sequestration (a rate or flow, e.g., tons
C/ha-yr) and storage (a stock, e.g., tons C/ha), we estimate carbon
source value (i.e., net carbon uptake) as the difference between
vegetation and soil carbon sequestration and stored carbon release
(i.e., due to deforestation, land use change, or fire) - both of which
are rates or flows.  This framework is analogous to proposed
forest-based carbon credit programs, where credits could be issued for
sequestration plus avoided deforestation (e.g., REDD, Gibbs et
al. 2007). While spatial datasets exist for net primary productivity
(i.e., carbon sequestration) and vegetation and carbon soil storage,
these values are influenced by various biotic, physical, and climate
factors, which can be used to train Bayesian networks in cases where
datasets are incomplete or of inadequate spatial resolution. Past
spatial ecosystem service models have identified a number of these
influences including land use-land cover (Tallis et al. 2010), timber
harvest or deforestation probabilities (Tallis et al. 2010, Wundscher
et al. 2008), carbon pools and decay rates (Eade and Moran 1996, Chan
et al. 2006, Egoh et al. 2008, Tallis et al. 2010, Wendland et al. in
press), biotic life zones (Wundscher et al. 2008), tree height, DBH,
and stem density by forest type (Naidoo and Ricketts 2006), and
population density, slope, elevation, mean annual precipitation, soil
texture and depth, and climatic indices (Iverson et al. 1994, Gaston
et al.  1998), including the difference between mean summer high and
winter low temperatures (Auch 2010). These influences can be assembled
into Bayesian models to map carbon sequestration and storage.

### Assumptions

We set stored carbon release as a function of vegetation and soil
carbon storage (the sum of vegetation carbon storage and soil carbon
storage) and the risk of deforestation and/or fire, with greater
stored carbon release at higher risk and carbon storage levels. Soil
carbon storage is influenced by slope, soil pH, soil oxygen conditions
(i.e., greater storage in wetlands where anaerobic conditions inhibit
respiration), vegetation density (an intermediate variable
incorporating vegetation cover, degradation status in Madagascar, and
successional stage and hardwood:softwood ratio in Western Washington),
and soil carbon:nitrogen ratio. The importance of these variables in
influencing soil carbon dynamics has been noted by previous authors
(including those listed in the preceding paragraph). We set vegetation
carbon storage as a function of the difference between mean summer
high and winter low temperature (Auch 2009) and vegetation density,
with population density added as an influence in Madagascar. Iverson
et al. (1994) and Gaston et al. (1998) note the importance of this
variable in measuring carbon storage in developing tropical nations,
where subsistence firewood collection is an economically important
activity.

We set vegetation and soil sequestration rate as a function of
vegetation density and sequestration rate, two intermediate variables
created to keep conditional probability tables tractable (Marcot et
al. 2006). Sequestration rate is set as a function of soil C:N ratio
and the difference between mean summer high and winter low. Vegetation
density is a function of hardwood:softwood ratio, vegetation percent
cover, and successional stage (in Western Washington) and vegetation
percent cover and forest degradation status (in Madagascar).

Iverson et al. (1994) and Gaston et al. (1998) provide discretization
of continuous variables for slope and population density. We used
natural breaks to discretize soil carbon storage, summer high-winter
low, vegetation and soil carbon storage, soil C:N ratio, vegetation
carbon storage, fire frequency, and actual evapotranspiration. We used
equal intervals to discretize vegetation and soil carbon
sequestration, hardwood:softwood ratio, and vegetation percent cover.

Most of the priors for the carbon source model are currently
uninformed. We filled out conditional probability tables with extremes
set at both ends (i.e., "pegging the corners," Marcot et al. 2006) and
intermediate values interpolated. We set soil carbon storage at its
highest values at low or high pH, high C:N ratio, level slopes, high
vegetation density, and on anoxic (i.e., wetland) soils, and vice
versa. Vegetation carbon storage was set at its highest values with
low differences between mean summer high and winter low temperature,
high vegetation density, and low population density (in
Madagascar). Vegetation density was set with its highest values at
greater vegetation percent cover, later successional stages, more
softwoods, and no forest degradation (where applicable).
Sequestration rate was set with its highest values at higher C:N
ratios and lower differences between mean summer high and winter low
temperatures.  Stored carbon release was set at its highest with
greater vegetation and soil carbon storage and greater deforestation
and fire risk.

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
{: rules="groups"}

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

### Additional contributors

Ted Auch and Serguei Krivov reviewed generalized carbon
models. Specific case studies were developed by Mark Casias (Orange
County) and Sam Gorton and Jennifer Wright (Vermont). Data and model
review were provided by Dave Batker and Paula Swedeen at Earth
Economics for Western Washington and Miro Honzak at Conservation
International for Madagascar.

</div>

</div>
