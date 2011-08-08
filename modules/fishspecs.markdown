---
layout: modulespec

title: Subsistence fisheries module specs

module-status: functional
---
<div id="module-spec-intro" markdown="1">

Our initial subsistence fisheries case study, developed for
Madagascar, relies on global spatial datasets for fisheries,
population density, and poverty, combined with non-spatial data on
national fisheries use from the FAO (2008) and The Sea Around Us
Project (2010).  Since such data are available for all nations, it is
quite feasible to extend coverage of this subsistence fisheries model
to other countries.  However, since key harvested fish species and
dependence on subsistence fisheries differ by nation, models should be
developed on a nation-by-nation basis rather than as part of a
generalized global model. For Madagascar, FishBase (Froese and Pauly
2010) lists eight commercially important fish species, in some cases
providing descriptions of their habitat, commercial importance, and
typical means of harvest.  From this list, The Sea Around Us project
(Close et al. 2006) provided relative abundance maps for four species,
as described below in the source model. Our initial fisheries models
focus on subsistence use of fisheries as the only class of
beneficiaries, ignoring for the time being both recreational and
commercial fisheries. Future ARIES models will account for
recreational and commercial fisheries, and will include more complex
flow models that represent trade networks and recreational choices.

Please see the [ARIES modeling guide](http://ariesonline.org/resources/toolkit.html)
for full documentation and references for these models.

</div>

<div id="module-spec-definitions" markdown="1">

## Definitions
---------------

### Subsistence fisheries source

Habitat for species valued as part of the subsistence harvest, where
they can be caught and used by subsistence fishermen.

### Subsistence fisheries sink

As an ecosystem good, subsistence fisheries do not have a sink that
depletes the quantity of the good as it moves along flow paths from
ecosystems to people. In other words, there are no anthropogenic or
biophysical features on the landscape that deplete the quantity of
caught fish as they are moved from the point of extraction to the
point of consumption.

### Subsistence fisheries beneficiaries

Human populations that rely on subsistence fisheries as a food source.

### Subsistence fisheries flows

The movement of subsistence fishermen to the fishery and their return
to communities where fish are consumed, via transportation networks.

</div>

<div id="module-spec-specifications" markdown="1">

## Module specifications
-------------------------

### Case studies

1. Madagascar

### Assumptions

**Subsistence fisheries source models.** The data available to
establish the quantity of fish supplied and demanded in subsistence
fisheries are generally quite sparse.  We obtained global relative
abundance maps for four species of commercial importance in
Madagascar.  We also obtained historical catch data for Madagascar
from the FAO (2008).  These catch data do not explicitly describe
subsistence catch, however, nor do they contain catch records specific
to any of the four species for which we have relative abundance data.

Despite these limitations, we can use these data, along with the
assumptions described below, to make a first estimation of the catch
for each species (i.e., its supply or source value).  These
assumptions can be adjusted should more refined fisheries information
become available.  Historical catch data from The Sea Around Us
Project (2010) shows that 71.6% of the total catch for Madagascar from
1950-2004 is "non-identified marine pelagic fishes."  In 2005,
Madagascar produced 138,477 tonnes of fish from capture fisheries, of
which 77,636 tonnes were for commodity trade and production (FAO
2008).  Another 72,300 tonnes were taken by traditional fishermen -
however, this catch is not necessarily mutually exclusive of the
commodity sector.  Subtracting the commodity catch from the total
catch leaves 60,841 tonnes of fish, which we assume goes toward local
consumption.  Assuming 71.6% of the locally consumed fish are
"non-identified marine pelagic fishes," these would account for 43,562
tonnes in 2005.  Assuming that each of the three marine pelagic fish
species for which we have distribution data (L. mahsena,
L. variegatus, L. argentimaculatus) accounted for 20% of that total
(leaving 40% of the catch from other species), this would give 8,712
tonnes of fish caught for each of these species.  We omit southern
meagre (A. hololepidotus) from the model because it is a demersal
species and we lack data on the catch of non-identified marine
demersal fish species.  We then divide the total catch for each
species according to their relative abundance along the Madagascar
coast in order to produce a map of subsistence fish production for
each species under the above assumptions (Equation 1).  A similar
equation holds for subsistence fisheries use (Equation 2).

        (1)  S = a1S1 + a2S2 + a3S3 + ... + anSn
        (2)  D = a1S1 + a2S2 + a3S3 + ... + anSn
        
        Where  S  = the total source or supply of subsistence fisheries (kg)
               D  = the total demand for subsistence fisheries (kg)
               an = the percentage of the total demand met with species n
               Sn = the total mass of species n caught (kg)
{: .equation }

Given better data on the relative use of different species, we need
only adjust the model coefficients in order to more accurately
quantify human dependence on Madagascar's fisheries.  The unit of
measure for the fisheries source/supply and use/demand models is kg of
fish biomass.  This allows us to use a common unit in the flow models
to determine the accessibility between catch areas and the places
where fish are consumed.

**Subsistence fisheries sink models.** As an ecosystem good,
subsistence fisheries do not have a sink that depletes the quantity of
the good as it moves along flow paths from ecosystems to people.  In
other words, there are no anthropogenic or biophysical features on the
landscape that deplete the quantity of caught fish as they are moved
from the point of extraction to the point of consumption.  Thus, fish
harvest implies use of the resource.

**Subsistence fisheries use models.** People are more likely to access
fisheries for subsistence purposes when they lack other sources of
nutrition (e.g., in poorer regions) and when they have access to a
fishery.  We used distance to the coast, poverty, and population
density as determinants of the degree of subsistence fisheries use. We
assigned prior probabilities for distance to the coast, poverty, and
population density based on reviews of available GIS data for
Madagascar.  We discretized population density by natural breaks,
percent poverty by equal intervals, and distance to the coast based on
easily walkable distances (<1 km, 1-5 km, >5 km).  In the use model's
contingent probability table, we expect greater subsistence fishery
use to occur at greater levels of poverty, closer proximity to the
coast, and moderate to low population densities (i.e., versus large
cities there is too much crowding, water pollution, and lack of access
to fisheries to enable widespread subsistence fishing).

This model is only addresses coastal and marine subsistence fishing.
We currently do not account for subsistence fisheries from rivers and
other inland water bodies.  We note that fish could also be traded to
groups located farther from the coast, with the benefits thus
extending further inland.  However, modeling of such trade networks is
beyond the scope of this assessment and may be handled by a separate
family of models to be developed.

The Bayesian network returns likelihood values for four classes of
subsistence marine fisheries use.  To convert this to total demand, we
note that the average Malagasy consumes 6.8 kg of fish per year (FAO
2008).  In areas with high subsistence use, we assume 100% of this per
capita use to come from the oceanic subsistence fishery.  In areas
with moderate subsistence use, we assume 67% of this total to come
from the oceanic subsistence fishery (4.6 kg/capita), and in areas
with low subsistence use we assume 33% of this total to come from the
oceanic subsistence fishery (2.3 kg/capita).  We assume that the
remaining unsatisfied demand from moderate and low subsistence users
comes from either trade or inland fisheries in rivers and lakes.
Similarly to mapping the supply or source of subsistence fisheries, we
assume that each of the three valuable species supplies 20% of the
fish use for subsistence users (Equation 2).

[![Bayesian network model for subsistence fisheries use](/images/bn/fishuse.gif)](/downloads/FisheriesSubsistenceUseMg.xdsl)
{: .bayesnet }

**Subsistence fisheries flow models.** Subsistence fisheries flow
models are designed to show the expected spatial dependence of
specific fisheries users on particular fisheries areas.  Subsistence
fisheries users are assumed to move from a point of origin (their
homes) to an oceanic fishery, harvest fish, and return to their homes,
where fish are consumed, via road or path networks. Thus the flow
models move a given quantity of fish (in kg) from the ocean to areas
of demand along roads or paths.  Each coastal ocean pixel has an
estimated potential source of fish, as described above for the source
model.  Each pixel on land has an estimated potential use for oceanic
fish, as described above for the use model.

We model the flow of subsistence fisheries using a distance decay
function, assuming that flow is greatest close to the coast and
declines relatively quickly moving inland.  This takes the shape of a
Gaussian curve with high subsistence use within 1 km of the coast,
steep decline at distances of 2-3 km of the coast, and slowly
declining subsistence use out to a distance of 5 km of the coast.
Along with proximity, users must have some form of access (e.g.,
roads, paths) to access the coastal fisheries.

Key model outputs from the flow models include: 

1. Subsistence fish supply: The supply of harvestable fish.
2. Subsistence fish demand: The demand for fish from subsistence users.
3. Subsistence fish flow: The movement of fish from areas where they
   are caught to communities where they are consumed, based on
   transportation networks, supply, demand, and distance decay.
4. Utilized subsistence fish: The quantity of fish harvested for subsistence use.
5. Satisfied subsistence fish demand: The portion of demand for fish
   satisfied by flows of fish to people from a fishery.
6. Unutilized subsistence fish: Fisheries that are not used due to
   lack of proximity or pathways to users.  This value may also be
   positive if some of the fish supply remains after all demand is
   satisfied.
7. Unsatisfied fish demand: The portion of demand for fish not
   satisfied due to inadequate size of the fishery or a lack of
   proximity to a fishery.  If this is zero, some unutilized fish may
   be a result of a true surplus and not just a lack of proximity.  If
   this is greater than zero, there is no surplus within range.

### Spatial data

|---------------------+-------------------------------------------------------------------+----------------------------------------+----------------+--------------------------------+---------------|
| Model               | Layer                                                             | Source                                 | Spatial Extent | Data type/Spatial resolution   |          Year |
|---------------------+-------------------------------------------------------------------+----------------------------------------+----------------+--------------------------------+---------------|
| Source - Madagascar | L. borbonicus, L. mahsena, L. argentimaculatus relative abundance | Sea Around Us Project                  | Global         | Raster/0.5 degrees<sup>2</sup> |     1950-2003 |
|---------------------+-------------------------------------------------------------------+----------------------------------------+----------------+--------------------------------+---------------|
| Use - Madagascar    | Distance to coast                                                 | Derived from global SRTM data          | Madagascar     | 90 x 90 m                      |           n/a |
| <span />            | Population density                                                | FAO soils                              | Global         | 0.5 min<sup>2</sup>            |     1970-1978 |
| <span />            | Poverty                                                           | Kew Gardens Madagascar vegetation map  | Madagascar     | 30 x 30 m                      |     1999-2003 |
|---------------------+-------------------------------------------------------------------+----------------------------------------+----------------+--------------------------------+---------------|
| Flow - Madagascar   | Paths                                                             | BD500 (Madagascar infrastructure data) | Madagascar     | Vector line data               | Not available |
|---------------------+-------------------------------------------------------------------+----------------------------------------+----------------+--------------------------------+---------------|

<div id="module-spec-references" markdown="1">

### Selected references

Close, C., et al. 2006.  Distribution ranges of commercial fishes and invertebrates.  Fisheries Centre 
Research Reports 14 (4): 27-37.

Cooley, S.R. and S.C. Doney.  Anticipating ocean acidification's economic consequences for commercial 
fisheries.  Environmental Research Letters 4: 024007.

Diaz, R.J. and R. Rosenberg.  2008.  Spreading dead zones and consequences for marine ecosystems.  
Science 321: 926-929.

Elvidge, C.D., et al.  2009.  A global poverty map derived from satellite data.  Computers and Geosciences 
35 (8): 1652-1660.

Fabricus, K.E.  2005.  Effects of terrestrial runoff on the ecology of corals and coral reefs: review and 
synthesis.  Marine Pollution Bulletin 50: 125-146.

Food and Agriculture Organization of the United Nations (FAO).  2008.  Fishery Country Profile: The Republic 
of Madagascar. http://www.fao.org/fishery/countryprofiles/search/en.

Froese, R. and D. Pauly. Editors. 2010.  FishBase.  World Wide Web electronic publication. www.fishbase.org, 
version (01/2010).

Hoegh-Guldberg, O. and J.F. Bruno.  2010.  The impact of climate change on the world's marine ecosystems.  
Science 328: 1523-1528.

Johnson, G., et al.  2010.  Service Path Attribute Networks (SPANs): Spatially quantifying the flow of 
ecosystem services from landscapes to people.  Lecture Notes in Computer Science 6016: 238-253.

McCulloch, M., et al.  2003.  Coral record of increased sediment flux to the inner Great Barrier Reef since 
European settlement.  Nature 421: 727-730.

Millennium Ecosystem Assessment (MA).  2005. Millennium Ecosystem Assessment: Living beyond our means - 
Natural assets and human well-being.  Washington, D.C.: World Resources Institute.

Potter, P., et al.  2010.  Characterizing the spatial patterns of global fertilizer application and manure 
production.  Earth Interactions 14 (2): 1-22.

Silvestri S. and F. Kershaw (eds.).  2010.  Framing the flow: Innovative Approaches to Understand, Protect 
and Value Ecosystem Services Across Linked Habitats. UNEP World Conservation Monitoring Centre, Cambrdige, UK.

TEEB.  2008.  The Economics of Ecosystems and Biodiversity (TEEB): An Interim Report.  European Communities, 
Welzel+Hardt: WEsseling, Germany.

The Sea Around Us Project.  2010.  Data and visualization, EEZ waters of Madagascar.  
http://www.seaaroundus.org/eez/450.aspx.

Worm, B., et al.  2009.  Rebuilding global fisheries.  Science 325: 578-585. 

</div>

### Additional contributors

William Cheung provided fisheries datasets.  UNEP-WCMC provided
funding for development of marine ecosystem services models in ARIES
and supplied other marine biotic datasets.  Liz Selig and Carmen
Lacambra provided helpful guidance in obtaining additional global
marine datasets.

</div>
