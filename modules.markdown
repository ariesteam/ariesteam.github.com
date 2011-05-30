---
layout: master

title: Module overview
---
# Module overview

<div id="module-sidebar" markdown="1">

## At a glance
---------------

### Completed modules

* [Carbon sequestration and storage](/modules/carbon.html)
* [Flood regulation](/modules/flood.html)
* [Coastal flood regulation](/modules/coast.html)
* [Aesthetic views and open space proximity](/modules/aesth.html)
* [Freshwater supply](/modules/water.html)
* [Sediment retention](/modules/soil.html)
* [Subsistence fisheries](/modules/fish.html)
* [Recreation](/modules/rec.html)

### Under development

* [Nutrient regulation](/modules.html)

### Beneath the surface

ARIES terms, module specifications, assumptions and resources are
available by clicking **Detailed module information** at the top of
each module page.

</div>

<div id="module-content" markdown="1">

### Overview
-------------

ARIES maps the potential provision locations of ecosystem services
("sources"), their users ("use"), and biophysical features that can
deplete service flows ("sinks") using deterministic ecological process
models or ad hoc Bayesian models.  ARIES then uses a family of
agent-based flow algorithms to map actual service flow from ecosystems
to people (e.g., via hydrologic or transportation networks, proximity,
or lines of sight).  Source, sink, and use models quantify these
values in common units, either concrete (e.g., tons of CO<sub>2</sub>,
mm of water, kg of fish) or abstract (e.g., aesthetic value or
recreation site quality, measured from 0-100).

Each ecosystem service is either a "provisioning service<sup>1</sup>"
with a "beneficial carrier" (i.e., the carrier of that benefit
provides something useful to people, such as drinking water, fish, or
aesthetic value) or a "preventive service" with a "detrimental
carrier" (i.e., the carrier is something damaging to people, e.g.,
excess sediment, nutrients, or flood water).  For provisioning
services, the source value provides the ecosystem service and sinks
limit the amount of service received, while for preventive services,
sinks are beneficial (i.e., areas that absorb flood water, sediment,
or nutrients).  The benefits of some services like sediment regulation
may be both provisioning and preventive - in some cases excess
sediment or excessively turbid waters damage human well-being, while
in other cases naturally delivered sediment provides benefits, such as
in maintaining soil fertility or natural coastal processes.

The flow model for each ecosystem service moves according to the
spatial scale and movement process specific to that service, which may
or may not include a decay function.  Finally, knowing whether the
benefit is rival or non-rival lets us know whether the use of that
service depletes the quantity available to other potential users on
the landscape.  When provided with all the information in the table
below, ARIES' flow models can fully illustrate the ecosystem services
connections between people and their surrounding environment.

<sup>1</sup>Note that this is a different use of the term
"provisioning service" than the popular Millennium Ecosystem
Assessment term for provisioning services, which indicate ecosystem
goods that are physically extracted from the ecosystem and used for
human benefit.

### Source, sink, use, and flow characteristics for ARIES ecosystem services modules
-------------------------------------------------------------------------------------

|----------------------+-----------------------------------------------+-------------------------------------------------------|
| Service              | Carbon sequestration and storage              | Open space proximity                                  |
|----------------------+-----------------------------------------------+-------------------------------------------------------|
| Service/carrier type | Provisioning/Beneficial                       | Provisioning/Beneficial                               |
| Medium/units         | Tons CO<sub>2</sub> absorbed/emitted          | Open space (abstract units, 0-100)                    |
| Scale                | Global                                        | Walking distance                                      |
| Movement             | Atmospheric mixing                            | Walking simulation                                    |
| Decay                | None                                          | Gaussian                                              |
| Rivalness            | Rival                                         | Nonrival                                              |
| Source               | Vegetation and soil carbon sequestration      | Open spaces, particularly in urban and suburban areas |
| Sink                 | Stored carbon release (fire, land use change) | Obstructions (highways)                               |
| Use                  | CO<sub>2</sub> emitters                       | Housing/housing value                                 |
|----------------------+-----------------------------------------------+-------------------------------------------------------|
{: rules="groups"}

|----------------------+--------------------------------------------+---------------------------------------|
| Service              | Aesthetic viewsheds                        | Flood regulation                      |
|----------------------+--------------------------------------------+---------------------------------------|
| Service/carrier type | Provisioning/Beneficial                    | Preventive/Detrimental                |
| Medium/units         | Scenic beauty (abstract units, 0-100)      | Water (runoff, mm/yr)                 |
| Scale                | Viewshed                                   | Watershed                             |
| Movement             | Line of sight                              | Hydrologic flow                       |
| Decay                | Inverse square                             | None                                  |
| Rivalness            | Nonrival                                   | Nonrival                              |
| Source               | Mountains, water bodies, scenic vegetation | Rainfall and snowmelt                 |
| Sink                 | Visual blight                              | Water absorbed by soil and vegetation |
| Use                  | Housing/housing value                      | Economic assets in floodplains        |
|----------------------+--------------------------------------------+---------------------------------------|
{: rules="groups"}

|----------------------+----------------------------------------+------------------------------------------|
| Service              | Sediment regulation                    | Water supply                             |
|----------------------+----------------------------------------+------------------------------------------|
| Service/carrier type | Provisioning or Preventive             | Provisioning/Beneficial                  |
| Medium/units         | Sediment (tons)                        | Surface or groundwater (mm/yr)           |
| Scale                | Watershed                              | Watershed                                |
| Movement             | Hydrologic flow                        | Hydrologic flow, surface and groundwater |
| Decay                | None                                   | None                                     |
| Rivalness            | Rival                                  | Rival                                    |
| Source               | Landscapes alonog waterways            | Precipitation, infiltration, and others  |
| Sink                 | Riparian zones where deposition occurs | Infiltration, evapotranspiration, others |
| Use                  | Multiple                               | Surface water withdrawals or wells       |
|----------------------+----------------------------------------+------------------------------------------|
{: rules="groups"}

|----------------------+----------------------------------------+----------------------------------------|
| Service              | Coastal flood regulation               | Subsistence fisheries                  |
|----------------------+----------------------------------------+----------------------------------------|
| Service/carrier type | Preventive/Detrimental                 | Provisioning/Beneficial                |
| Medium/units         | Storm surge (m)                        | Fish (kg)                              |
| Scale                | Coastal zones                          | Walking distance                       |
| Movement             | Wave runup                             | Walking simulation                     |
| Decay                | None                                   | Gaussian                               |
| Rivalness            | Nonrival                               | Rival                                  |
| Source               | Coastal zones prone to storms          | Fishing grounds                        |
| Sink                 | Vegetation and topographic features    | None                                   |
| Use                  | Economic assets in coastal flood zones | Subsistence communities near fisheries |
|----------------------+----------------------------------------+----------------------------------------|
{: rules="groups"}

|----------------------+--------------------------------------------------+------------------------------------------|
| Service              | Recreation                                       | Nutrient regulation                      |
|----------------------+--------------------------------------------------+------------------------------------------|
| Service/carrier type | Provisioning/Beneficial                          | Preventive/Detrimental                   |
| Medium/units         | Recreational enjoyment (abstract units, 0-100)   | Nutrients in water (kg N/P)              |
| Scale                | Driving distance                                 | Watershed                                |
| Movement             | Driving simulation (transportation model)        | Hydrologic flow                          |
| Decay                | Gaussian                                         | None                                     |
| Rivalness            | Nonrival but congestible                         | Nonrival                                 |
| Source               | Recreational areas suitable for a given activity | Landscapes along waterways               |
| Sink                 | None                                             | Filters in landscape and along waterways |
| Use                  | Recreationists interested in a given activity    | Multiple                                 |
|----------------------+--------------------------------------------------+------------------------------------------|
{: rules="groups"}

</div>
