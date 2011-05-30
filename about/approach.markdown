---
layout: master

title: The ARIES approach
---
# The ARIES approach

<div id="about-sidebar" markdown="1">

## At a glance
---------------

### A modeling platform

ARIES is a modeling platform rather than a single model or collection
of models. ARIES is capable of incorporating existing ecological
process models where appropriate, and turns to ad hoc models where
existing process models do not exist or are inadequate for local
contexts. Agent-based models are used to simulate ecosystem service
flows.

### Ad hoc models

ARIES' ad hoc models are probabilistic, Bayesian models, which offer
the advantages of explicitly conveying uncertainty and being capable
of operating in data-scarce conditions. Rather than specifying the
equations that define the relationships between model variables, as is
done in deterministic modeling, ARIES is capable of using the data to
derive the relationships between variables, learning these
relationships, and applying results to data-scarce conditions.

### Spatial dynamics

Many researchers have noted that provision and use of ecosystem
services take place at different temporal and spatial scales. Yet
aside from hydrologic ecosystem service models, researchers have too
often ignored the fact that the location of ecosystems, their human
beneficiaries, and the biophysical nature of ecosystem service flows
affect how much of a service is actually used by people. ARIES
explicitly accounts for the spatial dynamics of ecosystem services.

### Accessibility

ARIES is accessible from any internet browser, with all functions
handled remotely and returned to the user via a web interface. Data
and model storage, data transformations, model runs, and reporting of
results take place behind the scenes without the need to purchase and
gain proficiency using commercial GIS or modeling software.

### Local models

ARIES includes models tailored to reflect local ecological and
socioeconomic conditions relevant to ecosystem service provision and
use. Local case studies typically include data at finer spatial
resolution or that better describes local conditions. Users interested
in developing new case studies will eventually be able to edit the
models and submit local GIS data for their case study directly to the
system. Until these features are available, users interested in
developing local case studies should [contact the ARIES development
team](mailto:info@ariesonline.org) to discuss potential partnership or
training opportunities in developing new case studies.

### Global model

ARIES will eventually include generalized global models for most
ecosystem services to describe their provision, use, and spatial
dynamics. Global models will be supported by corresponding pre-loaded
global datasets (typically ranging from 1 degree<sup>2</sup> to 1
km<sup>2</sup> in spatial resolution).

</div>

<div id="about-content" markdown="1">

### Overview
-------------

With growing interest in using ecosystem services for decision making,
demand has grown for systematic methods and tools to quantify
ecosystem service values. ARIES maps the potential provision of
ecosystem services (sources), their users (use), and biophysical
features that can deplete service flows (sinks) using ecological
process models or Bayesian models. ARIES then uses a series of
agent-based flow algorithms to map actual service flow from ecosystems
to people.

### Integrated modeling platform
---------------------------------

Through artificial intelligence and semantic modeling, ARIES assembles
the appropriate models - deterministic or probabilistic and spatial
data to quantify and map ecosystem services at the appropriate spatial
scale and ecological and socioeconomic context.

![](/images/integrated_modeling.png)

### A benefits- and beneficiaries-based approach to ecosystem services
-----------------------------------------------------------------------

Rather than relying on sometimes-abstract lists of ecosystem services,
ARIES maps concrete, spatially-explicit beneficiaries of ecosystem
services, and quantifies their demand for each service.  For instance,
rather than mapping "disturbance regulation," ARIES separately
considers cases for flooding on rivers, flooding in coastal zones, and
avalanches or mudslides.  Regulation of each of these disturbances
depends on different processes and patterns of water or soil flows.
Different beneficiary groups are explicitly identified (e.g., crops,
housing, lives at risk, privately-owned structures or public
infrastructure), as each of these groups will value the benefit
differently.  Conceptualizing ecosystem services as a concrete list of
benefits for concrete beneficiary groups avoids the problem of "double
counting" of benefits that has plagued past ecosystem service
valuation efforts.

![](/images/beneficiaries.png)

### Spatial dynamics of ecosystem services
-------------------------------------------

Researchers have long recognized that the ecosystems that provide
benefits to people and the beneficiaries of these services are not
always located in the same regions in space.  ARIES is the first
modeling tool to explicitly account for this spatial disconnect.
ARIES accomplishes this by first using deterministic or probabilistic
models to map provision, use, and sinks of ecosystem services.  We
then use agent-based models to move a carrier for each service (e.g.,
tons of carbon dioxide, tons of sediment, kg of fish, or abstract
units of view) across the landscape according to service-specific flow
paths (e.g., through atmospheric mixing, hydrologic flows,
transportation networks, or lines of sight).  While most past
ecosystem services mapping tools and projects have simply mapped the
potential provision of ecosystem services, ARIES maps actual
provision, use, and flows of services by accounting for flow paths and
rival use or "sink" regions that deplete or transform the carrier of a
service as it moves across the landscape.

![](/images/flows.png)

### Data and model integration
-------------------------------

Unlike manual approaches to ecosystem service mapping, where a user
must download, prepare, and manipulate spatial data directly, ARIES
stores hundreds of pre-loaded local through global scale GIS datasets
on the ARIES GeoServer.  These data are semantically annotated or
"tagged" with relevant concepts so that ecosystem service models
automatically call on, transform, and integrate the relevant data into
each model.  The open-source ARIES modeling language, written in Java
and Clojure, assembles, transforms, and processes data automatically
while running the appropriate set of probabilistic, deterministic, or
agent-based models for each ecosystem service.  Results are returned
to the user during an online ARIES session.  While full reporting of
results takes place online, the user can also export results as
netCDFs, which can be easily imported into external GIS or netCDF
viewing platforms for further display and analysis.

### A pluralistic approach to economic valuation
-------------------------------------------------

ARIES is capable of using several approaches for economic valuation of
ecosystem services. After computing values for a set of ecosystem
services of interest, multiple services can be paired with priority
weights stated by the user, in a multiple criteria analysis that will
yield maps of concordance of the computed flows of ES with the levels
of provision desired by the user. Such maps can be considered
"abstract" quantification of relative value. Alternatively, ES flow
information can be used to build a transfer function to translate
previously assessed economic values for specific benefits into
estimated valuation portfolios when required by the user.  The
transfer function operates on the agggregated values retrieved from
the Ecosystem Services Database with the help of a neural network
classification algorithm that identifies most likely candidates based
on ecological and economic similarities between source and destination
areas.

</div>
