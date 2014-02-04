---
layout: modulespec

title: Recreation module specs
---
<div id="module-spec-intro" markdown="1">

From a spatial perspective, we can map sources of recreational value (areas capable of providing the natural setting 
needed for a particular activity), sinks of recreational value (landscape features that reduce those source values, 
if applicable), and the users of a particular recreation area for a given activity.  A recreation flow model accounts 
for travel from a person's home to a particular location suitable for that recreational activity.  Travel cost and 
recreational site choice studies also use basic transportation routing to connect recreationists to recreation sites, 
but typically do not map the process or facilitate comparisons with other ecosystem services (Clawson and Knetsch 1966, 
Hunt et al. 2005, Hunt 2008).  Users may simultaneously value a particular bundle of recreational attributes (e.g., 
the quality of an area for hunting or fishing plus the quality of scenic views), built infrastructure meant to enhance 
the recreational experience (i.e., trails, other facilities), congestion or lack thereof (with potential resulting 
visitor response), and the management policies that facilitate a particular recreational experience (Lawson and Manning 
2002, Arnberger and Haider 2007, Boyd and Banzhaf 2007, Bullock and Lawson 2008).  The ARIES recreation models are 
intended to solely map an ecosystem's capacity to support a particular recreational activity, as opposed to the other 
attributes that contribute to the overall quality of a recreational experience, with the understanding that only the 
ecosystem attributes supporting recreation represent actual natural capital and are thus the ecosystem service (Boyd 
and Banzhaf 2007).  By mapping the ecosystem's contribution toward different recreational attributes, we can explore 
tradeoffs between different types of recreational use, tradeoffs between recreation and other ecosystem services, and 
relative preferences for certain recreational attributes.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html) for full documentation 
and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Recreation source

Open space capable of providing a particular type of recreational experience (e.g., 
wildlife for viewing, hunting, fishing; scenic views), exclusive of the area's 
infrastucture, congestion, and management policies.

### Recreation sink

A feature that depletes the quanitity of a recreational source value for human users (e.g., 
visual blight that detracts from view quality, landscape features that deplete wildlife 
populations valued for recreational activities).

### Recreation beneficiaries

People who travel to a recreation area to engage in a given recreational activity.

### Recreation flow

The movement of people from residences to recreation sites, typically via road networks.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
--------------------------

### Case studies

1. Vermont
2. San Pedro River Watershed, Arizona

### Model structure and assumptions

**Recreation source models: Birding, hunting, and wildlife viewing.** Other ecosystem services researchers have 
mapped potential recreational value across the landscape by overlaying factors including viewsheds or visibility 
(Eade and Moran 1996, Chen et al. 2009), proximity or access to roads, population centers, or recreation 
infrastructure (Eade and Moran 1996, Boyd and Wainger 2003, Chan et al. 2006, Beier et al. 2008), and land 
ownership and cover characteristics (Boyd and Wainger 2003, Chan et al. 2006).  Most of these authors, however, 
develop a general model of recreation site quality, rather than looking at sites' suitability for a specific 
recreational activity.  We thus draw selectively from the factors these studies use to model recreation, depending 
on the particular type of recreation model we are interested in constructing.

Potentially valuable birding areas can be identified using spatial data for bird species richness and the presence 
of rare birds.  We map the presence of rare and charismatic birds by noting the number of bird species' habitats 
present, based on a list of ten rare or charismatic birds for the San Pedro River Watershed and surrounding 
mountains (Southwest Wings Festival 2010).  Hunting potential can be identified based on habitat maps for the 
above-listed game species - javelina plus two species each of deer and doves and three species of quail.  We map 
wildlife viewing potential by averaging decile values for diversity of amphibian, bird, mammal, and reptile species. We 
set the source value for birding, hunting, and wildlife viewing as a function of public access, potential presence 
of surface water (springs or streams) and riparian habitat quality (where known), along with the appropriate bird 
richness and rarity, harvestable species habitat, or overall biodiversity value.  We set priors for each variable 
based on reviews of the corresponding spatial data.

High diversity of birds and wildlife or habitat for rare or game species are clear prerequisites for supporting 
related recreational activities, as is public access, particularly in states like Arizona where access on private 
lands is likely to be controlled.  We set these factors as the strongest influences on recreation source values in 
their respective contingent probability tables.  We set the presence of perennial or intermittent surface water, 
including streams and springs, as an important but slightly lesser influence on source values in the contingent 
probability tables, since the presence of surface water is highly important for attracting wildlife in arid 
environments.  Where riparian condition is known, we assigned higher values for birding, hunting, and wildlife 
viewing quality to higher-quality riparian areas.

[![](/images/bn/RecSourceSanPedroBird.gif)](/downloads/RecreationSourceSanPedroBirding.xdsl)
{: .bayesnet title="Bayesian network model for birding source areas in the San Pedro River Watershed. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files." }

[![](/images/bn/RecSourceSanPedroQuail.gif)](/downloads/RecreationSourceSanPedroQuailHunting.xdsl)
{: .bayesnet title="Bayesian network model for birding source areas in the San Pedro River Watershed. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files." }

**Recreation source models: Viewsheds.** Mountains, open water, forested and open lands are commonly valued objects 
in viewsheds (USFS 1974, Zube et. al. 1975, USFS 1995, Chhetri and Arrowsmith 2003, Manning et. al. 2006, Goonan et 
al. 2007). We define several types of open space, including agricultural, forested, and other types of land cover. 
Agricultural lands include pasture land, crop land, and orchards.  Other open land includes barren lands, brush and 
transitional lands, and wetlands.  Forested lands include broadleaf, coniferous, and mixed forests.  We estimated 
prior probability distributions for elevation, land cover, and the presence of open water based on relevant spatial 
data for Vermont.  

We set overall view quality, or "Theoretical natural beauty" as a function of water views, open space views, and the 
presence of mountains.  We set the highest values for large mountains, lakes, and forested open space, the lowest 
values for developed land, and no mountains or water views, and intermediate values for other open space and agriculture. 
These relative values could be adjusted for different parts of the world based on local view preferences indicating 
relative values of different types.  The highest and lowest quality view combinations allowed us to "peg the corners" 
of the contingent probability table and interpolate intermediate values for natural beauty (Marcot et al. 2006).

People value highly scenic landscapes (those with high natural beauty as defined in the source model) but also landscapes 
with a diversity of landforms, water characteristics, and vegetation patterns (USFS 1995, Chhetri and Arrowsmith 2003). 
The precise relationship between this variability and value may vary regionally.  Research is lacking for the eastern 
United States, but data from Switzerland show that in a reforesting landscape people prefer a landscape that was 
heterogeneous with patches ranging from slightly to mostly reforested (Hunziker and Kienast 1999).  The diversity of 
landscape types present in views will be incorporated into future recreational viewshed flow models, building on the 
viewshed flow model described in the aesthetic viewshed module.

[![](/images/bn/RecSourceVTView.gif)](/downloads/RecreationSourceVtView.xdsl)
{: .bayesnet title="Bayesian network model for viewshed source areas in Vermont. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files." }

**Recreation sink models.** Sinks will be present for some, but not all types of recreation.  For most types of 
recreation where the source value can be assessed in situ, no sink model is necessary.  This is true for the birding, 
hunting, and wildlife viewing models for the San Pedro, where we do not specify the dependence of a particular species 
on additional habitat outside its currently mapped habitat.  However, habitat-based flow models could eventually be 
developed or an existing ones incorporated to account for spatial dependencies in wildlife habitat (e.g., Semmens et 
al. in press).

For viewsheds, the sink model identifies areas of visual blight that reduce view quality, similar to the viewshed model 
described in the aesthetic viewshed module.  We assumed that obstructions (e.g., buildings, topography, or vegetation) 
or undesirable visual features (blight associated with development, energy infrastructure, or roads) reduce view quality 
(Benson et al. 1998, Bourassa et al. 2004, Gret-Regamey et al. 2008). Views of lost forest cover, including clearcuts, 
could also reduce view quality (Palmer 2008, Wundscher et al. 2008).  We set prior probability distributions using 
corresponding spatial datasets.  Based on a 1998 Vermont Agency of Natural Resources assessment, approximately 2% of the 
Vermont landscape was heavily cut or clear cut, which we assume as a prior probability for clearcuts.  We set values in 
the contingent probability table for visual blight as high when individual or combined blight features were observed 
in the landscape and as zero when these features were absent.

[![](/images/bn/RecSinkVTView.gif)](/downloads/RecreationSinkVtView.xdsl)
{: .bayesnet title="Bayesian network model for viewshed sink areas in Vermont. Please visit http://genie.sis.pitt.edu/downloads.html to download the GeNIe Bayesian network editor, which will read .xdsl files." }

**Recreation use models: Birding, hunting, and wildlife viewing.** Initial mapping of recreational use relies on 
population or housing density data.  For some activities, it may be possible to estimate the percentage of the 
population taking part in that recreational activity (i.e., the number of licensed hunters or anglers in a state 
relative to its total population).  Representing users as a uniform percentage of the population engaging in a 
particular activity makes the admittedly naive assumption that the same percentage of recreational users across 
all communities engage in a particular activity.  It also assumes that different user groups for the same activity 
have similar preferences, which is not always a realistic assumption.  For example, Hunt et al. (2005) found urban 
and rural hunters to prefer different types of hunting experiences.

A more realistic model would account for the fact that different types of communities are likely to prefer different 
recreational activities and to value attributes of a particular recreational experience differently.  Indeed, in some 
cases individuals will choose their location of residence to provide proximity to an especially valued recreational 
amenity.

Our initial use models for the San Pedro start simply with a population density map and anecdotal information on total 
visitation and the distance groups typically travel to reach the SPRNCA.  We then assign the home locations of visitors 
to the SPRNCA based on population density for the estimated number of visitors coming from within the watershed, from 
the Tucson area, and from more distant locations.  This is an admittedly simplistic way to map visitors, but in the 
absence of better data (e.g., surveys where visitors identify their zip code of origin), it at least enables mapping 
of the spatial dependencies between recreation areas and recreationists.  These simplistic assumptions about visitation 
can be easily replaced with actual data in locations where better survey data are available.

**Recreation use models: Viewsheds.** The use model for aesthetic views is based on locations where hikers have access 
to views (i.e. trails, vistas, outcroppings).  Since only Vermont's tallest mountains have elevations above the treeline, 
many of these viewpoints are rock outcrops.  These use points are relatively small in number, and are generally well known 
within the region's large hiking community, so we simply digitized them to create a use layer.  After running the view 
flow model to measure the view quality at each viewpoint, a transportation flow model can then be used to connect use of 
each recreational site to its potential user population.  Lacking data about the annual number of Vermonters and out of 
state visitors who hike to places with scenic views, we initially assume that 25% of the state's population will hike in 
a given year.  This assumption, which can easily be adjusted to reflect better data or anecdotal evidence, can be used to 
identify the location of users on the landscape and to map spatial flows of visitors.

**Recreation flow models.** With information on how many visitors participate in a given activity at a particular 
recreation site and how far they travel, we can complete a simple flow model by distributing the visitor population 
across the landscape based on a population density map and road networks that incorporate data on trailhead locations 
(if applicable for that activity).  This allows the model to estimate travel times for people traveling from their 
residences to recreational sites.  Where data are available, zip code based travel cost, recreational preference surveys, 
or permit data can show how far people travel to a particular site.  For a given recreational area, this will result in 
a map showing from where its user population is likely derived.  Zip code data are often available from state park 
systems and for the National Park Service through the University of Idaho Park Studies Unit's Visitor Services Project.

For instance, on the San Pedro, birders visit the site from around the nation and world.  Hunters and other recreational 
users (e.g., hikers, mountain bikers, equestrians, viewers of historical sites) are less likely to travel great distances. These 
visitors are more likely to come from "local" areas such as the San Pedro Valley itself or from Tucson, while recreationists 
from Phoenix are more likely to choose closer sites for their activities, and more rarely travel to the San Pedro.

For the Vermont case study, we lack data about the distance that hikers typically travel.  We initially assume that they 
will hike summits within a 1-hour driving distance from home 70% of the time, a 1-2 hour driving distance from home 20% 
of the time, and a greater than 2 hour driving distance from home 10% of the time. This assumption can easily be adjusted 
to reflect better data or anecdotal evidence.

Key outputs from the flow models include: 

1. Recreational user flow: The movement of people toward recreation areas, based on transportation networks, recreational preferences, site quality, and a distance decay function.
2. Recreational use: The amount of recreational use actually seen at a recreation area when accounting for demand and spatial flows of visitors.
3. Actual recreational users: The residential location of users who actually travel to sites via recreation flows to engage in recreational activities at source areas.
4. Transportation restricted recreational use: Recreational areas whose current accessibility via transportation networks makes their use level more limited than their attractiveness alone would dictate.

### Spatial data

|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Model              | Layer                                             | Source                                                              | Spatial Extent     | Data type/Spatial resolution |          Year |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Source - San Pedro | Amphibian, bird, mammal, reptile species richness | USGS Southwestern Biological Center Sonoran Desert Research Station | AZ, CO, NM, NV, UT | Vector polygon data          |     1999-2001 |
| <span />           | Habitat for game species                          | Southwest Regional GAP Analysis LULC (SWReGAP)                      | AZ, CO, NM, NV, UT | Raster/240 x 240 m           |     1999-2001 |
| <span />           | Public lands                                      | Arizona Geographic Information Council                              | Arizona            | Vector polygon data          |          2000 |
| <span />           | Rare & charismatic bird habitat presence          | Southwest Regional GAP Analysis LULC (SWReGAP)                      | AZ, CO, NM, NV, UT | Raster/240 x 240 m           |     1999-2001 |
| <span />           | Riparian condition class                          | Stromberg et al. (2006)                                             | SPRNCA             | Vector polygon data          |     2001-2004 |
| <span />           | Springs                                           | Arizona Geographic Information Council                              | Arizona            | Rasterized point data        |           n/a |
| <span />           | Hydrograpy                                        | National Hydrography Dataset                                        | Arizona            | Vector line data             |           n/a |
| Source - Vermont   | <span />                                          | National Hydrography Dataset                                        | Vermont            | Vector line data             |           n/a |
| <span />           | Elevation                                         | SRTM                                                                | Global             | Raster/90 x 90 m             |           n/a |
| <span />           | Lakes & ponds                                     | National Hydrography Dataset                                        | Vermont            | Vector polygon data          |           n/a |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Sink - Vermont     | Developed land                                    | NLCD 2001                                                           | United States      | Raster/30 x 30 m             |          2001 |
| <span />           | Energy infrastructure                             | Vermont Center for Geographic Information)                          | Vermont            | Vector line data             |          2003 |
| <span />           | Transportation infrastructure                     | Vermont Agency of Transportation                                    | Vermont            | Vector line data             |          2010 |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Use - All models   | Population density                                | U.S. Census Bureau                                                  | Arizona            | Vector polygon data          |     2000-2007 |
| Use - Vermont      | Scenic viewpoints                                 | Digitized locations of VT peaks with scenic views                   | Vermont            | Rasterized point data        |           n/a |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|
| Flow - All models  | Roads: speed limits/travel capacity               | TIGER/Line files                                                    | United States      | Vector line data             |          2000 |
| Flow - San Pedro   | <span />                                          | Arizona Geographic Information Council                              | Arizona            | Vector line data             |          2009 |
| <span />           | Trails                                            | BLM                                                                 | SPRNCA             | Vector line data             | Not available |
|--------------------+---------------------------------------------------+---------------------------------------------------------------------+--------------------+------------------------------+---------------|

<div id="module-spec-references" markdown="1">

### References

Arnberger, A. and W. Haider.  2007.  Would you displace?  It depends!  A 
multivariate visual approach to intended displacement from an urban forest 
trail.  Journal of Leisure Research 39 (2): 345-365. 

Beier, C.M., et al.  2008.  Ecosystem services and emergent vulnerability in 
managed ecosystems: A geospatial decision-support tool.  Ecosystems 11: 923-938.

Benson E.D., et al.  1998.  Pricing residential amenities: the value of a view. 
Journal of Real Estate Finance and Economics 16: 55-73. 

Bourassa, S.C., et al.  2004.  What's in a view?  Environment and Planning A 36: 
1427-1450.

Boyd, J. and L. Wainger.  2003.  Measuring ecosystem service benefits: The use of 
landscape analysis to evaluate environmental trades and compensation.  Discussion 
Paper 02-63, Resources for the Future: Washington, DC.

Boyd, J., and S. Banzhaf.  2007.  What are ecosystem services?  The need for 
standardized environmental accounting units.  Ecological Economics 63: 616-626.

Bullock, S.D. and S.R. Lawson.  2008.  Managing the 'commons' on Cadillac Mountain: 
A stated choice analysis of Acadia National Park visitors' preferences.  Leisure 
Sciences 30 (1): 71-86.

Chan, K.M.A., et al.  2006.  Conservation planning for ecosystem services.  PLOS 
Biology 4 (11): 2138-2152.

Chen, N., et al.  2009.  A GIS-based approach for mapping direct use of ecosystem 
services at the county scale: Management implications.  Ecological Economics 68 
(11): 2768-2776.

Chhetri, P. and C. Arrowsmith. 2003. Mapping the potential of scenic views for the 
Grapmians National Park.  In: Proceedings of the 21st International Cartographic 
Conference, Durban, South Africa, 10-16 August 2003.

Clawson, M. and J. Knetsch 1966.  Economics of outdoor recreation.  Johns Hopkins 
University Press: Baltimore, MD.

Eade, J.D.O. and D. Moran.  1996.  Spatial economic valuation: Benefits transfer 
using geographical information systems.  Journal of Environmental Management 48: 
97-110.

Goonan, K.A., et al.  2007.  Using science to manage Northern Forest tourism and 
recreation.  Adirondack Journal of Environmental Studies 14 (2): 6.

Gret-Regamey, A., et al.  2008.  Linking GIS-based models to value ecosystem services 
in an Alpine region.  Journal of Environmental Management 89: 197-208.

Hunt, L.M., et al.  2005.  Accounting for varying setting preference among moose hunters. 
Leisure Sciences 27 (4): 297-314.

Hunt, L.M.  2008.  Examining state dependence and place attachment within a recreational 
fishing site choice model.  Journal of Leisure Research 40 (1): 110-127. 

Hunziker, M. and F. Kienast. 1999. Potential impacts of changing agricultural activities 
on scenic beauty- a prototypical technique for automated rapid assessment. Landscape 
Ecology 14: 161-176.

Lawson, S.R. and R.E. Manning.  2002.  Tradeoffs among social, resource, and management 
attributes of the Denali Wilderness Experience: A contextual approach to normative 
research.  Leisure Sciences 24 (3): 297-312.

Manning, R., et al. 2006. Recreation Monitoring at Acadia National Park.  The George 
Wright Forum 23(2): 59-72.

Marcot, B.G., et al. 2006.  Guidelines for developing and updating Bayesian belief 
networks applied to ecological modeling and conservation.  Canadian Journal of 
Forest Research 36: 3063-3074.

Palmer, J.F.  2008.  Perceived effects of clearcutting in the White Mountains of 
New Hampshire, USA.  Journal of Environmental Management 89 (3): 167-183.

Semmens, D.J., et al.  In press.  Accounting for the ecosystem services of migratory 
species: Quantifying migration support and spatial subsidies.  Forthcoming in: 
Ecological Economics.

Southwest Wings Festival.  2010.  19th Annual Southwest Wings Birding and Nature 
Festival, Program Guide.  Southwest Wings Festival: Sierra Vista, AZ.

Stromberg, J.C., et al.  2006.  Status of the riparian ecosystem in the Upper San 
Pedro River: Application of an assessment model.  Environmental Monitoring and 
Assessment 115: 145-173.

U.S. Forest Service (USFS). 1974. The visual management system. In: National 
Forest Landscape Management, Vol. 2. U.S. Department of Agriculture, Washington, 
DC.

U.S. Forest Service (USFS).  1995.  Landscape aesthetics: A handbook for scenery 
management.  USDA-Forest Service Agriculture Handbook Number 701.

Wundscher, T., et al. 2008.  Spatial targeting of payments for environmental 
services: A tool for boosting conservation benefits.  Ecological Economics 65: 
822-833.

Zube, E.H., et al (eds). 1975. Landscape Assessment. Community Development 
Series 11: Halsted Press, United States.

</div>

### Acknowldegements and additional contributors

Rose Graves developed the Vermont case study.  An expert review panel including individuals from 
the U.S. Geological Survey, University of Arizona, Bureau of Land Management, and other organizations 
provided data and model review for the San Pedro case study.

</div>
