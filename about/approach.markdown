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

### Introduction to probabilistic modeling
-------------------------------------------

Bayesian statistical approaches have been used to address a variety of
issues in environmental valuation and value transfer (Brundson and
Willis 2002), including determination of which independent variables
to include in regression models (Moeltner and Rosenberger 2007,
Leon-Gonzalez and Scarpa 2008), accounting for the "n vs. k" problem
in function transfer, and in handling the effects of methodological
independent variables when using a transfer function (Moeltner et
al. 2007, Moeltner and Woodward 2009). Bayesian methods are a general
approach to statistical problems in meta analysis and function
transfer rather than a one-size-fits-all solution to the problems of
ecosystem service valuation. Despite the use of Bayesian approaches to
meta analysis and function transfer, the ARIES project is the first to
use Bayesian models to map ecosystem services provision, use, and
spatial dynamics.

Basic principles of Bayesian models in ecology are described well by
McCann et al. (2006), part of a special issue of the Canadian Journal
of Forest Research dealing with Bayesian modeling in ecology.Marcot et
al. (2006) provide a number of basic principles for Bayesian modeling
that we have followed in our work regarding model construction,
development of prior and conditional probabilities, and testing and
review of the models.  Per Marcot et al.'s recommendations on keeping
conditional probability tables tractable and transparent, we generally
use no more than 3-5 discrete states for each variable (often
classified as "high-moderate-low" or "very high-high-moderate-low-very
low"), make each variable a function of no more than 3-5 other
variables, and use intermediate variables where appropriate. We direct
readers with further interest in Bayesian networks and stronger
backgrounds in probability theory to Pearl (1988).

We note that some readers who are unfamiliar with Bayesian approaches
may feel uncomfortable with the perceived subjectivity of assigning
prior and conditional probabilities in our models. We feel that
Brundson and Willis (2002) address this point quite well:

"Some would argue that incorporating beliefs about models other than
those implied by empirical measurement is a subjective, or
unscientific, approach. In response, it could be stated that,
certainly, Bayesianism has the potential for this problem to arise,
and so one must have a strict 'code of conduct' for prior distribution
specification.  For example, making use of the outcomes off previous
studies to provide prior beliefs is a reasonable scientific
standpoint. Indeed, it could be argued that it is unscientific to
ignore these prior results! Another way of avoiding subjectivity is to
use non-informative priors in cases where prior information is
unavailable or unobserved.  Of course, one could argue that even a
non-informative prior gives us *some* form of information about the
distribution of an unknown parameter: after all, a specific
distribution is being supplied rather than the information that *any*
distribution might apply.  However, in many cases non-informative
priors do make reasonable models for a state of no subjective
knowledge. In several 'text-book' examples of Bayesian analysis, for
example multiple linear regression analysis assuming normal error
terms, the adoption of non-informative priors results in tests
algebraically identical to classical inferential procedures. In most
cases, analysts are reasonably satisfied with regarding such classical
approaches as 'objective'."

As described for each model, we incorporate model elements from the
literature and conversations with local experts on each ecosystem
service, facilitated by our case study partners - Conservation
International in Madagascar, CI and INECOL in Veracruz, Mexico, Earth
Economics in Western Washington, and the U.N. Environmental
Program-World Conservation Monitoring Center (UNEP-WCMC) for marine
ecosystem services.

Users should note that ad hoc Bayesian models are not always
appropriate or necessary in the ARIES system - where well-accepted,
peer-reviewed ecological process models can provide input data or
values for the source, sink, or use of an ecosystem service, these
models can be incorporated instead of probabilistic models. The ARIES
system is then instructed as to which cases to use the probabilistic
versus deterministic model (e.g., in a particular part of the world or
at a particular spatial scale). Also, in some cases (particularly for
the beneficiary or use models), a single spatial data layer or a
simple GIS operation on two or more layers may suffice to map
beneficiaries, rather than requiring a Bayesian network.

### Next steps
---------------

Like all ecological models, ARIES remains a work in progress as we
continue to add the latest ecological knowledge and spatial datasets,
incorporate existing process-based models where these can better
inform ecosystem services modeling, build new probabilistic models for
additional ecosystem services, and customize existing probabilistic
models to provide useful estimates for new case study regions. Further
testing of these models and review with local experts and decision
makers for the case studies is a critical next step for the ARIES
system in order to move it from a position of demonstrating the
spatial dynamics of ecosystem services to being able to quantitatively
inform conservation, restoration, land use, development, and resource
extraction choices.

The economic valuation system in ARIES is currently limited in scope.
Services are expressed in either biophysical units (i.e., for carbon,
sediment, or flood water) or relative units (e.g., for view quality or
recreational value).  Longer-range plans include integration of ARIES
with the Ecosystem Services Database (ESD, Villa et al.  2002). This
will enable users to view primary economic valuation studies from
their region of interest. Since ARIES is capable of mapping ecosystem
service flows - the connection between ecosystems and their human
beneficiaries, spatial determinants of supply and demand, and in
handing data probabilistically, future additions to the system can
enable more sophisticated forms of value transfer that incorporate
benefit flows and Bayesian approaches.  In the interim, an economic
valuation system in ARIES links land use-land cover types to per-area
economic value derived from studies like Costanza et al. (1997). The
drawbacks of this approach are quite well known, and users are advised
to interpret such results with a full understanding of their
limitations.

ARIES is an open-source project that strives for transparency in its
use of data and models. We encourage all ARIES users to submit
suggestions, edits, and additions to our library of models and spatial
data, and to this modeling guide, as we continue working to improve
the system.  Thank you for your interest as we work to build a system
for improved environmental management built on the principles of
environmental sustainability, socially just access to resources, and a
more efficient allocation between market and non-market goods and
services.

<div id="about-references" markdown="1">

### References
---------------

Brunsdon, C. and Willis, K.G.  2002. Meta-analysis, a Bayesian
perspective. In: R.J.G.M. Florax, et al. (Eds.), Comparative
Environmental Economic Assessment, Edward Elgar, Cheltenham, UK.

Chan, K.M.A., et al. 2006.  Conservation planning for ecosystem
services. PLOS Biology 4 (11): 2138-2152.

Costanza, R, et al.  1997. The value of the world&#39;s ecosystem
services and natural capital. Nature 387: 253-260.

Eade, J.D.O. and D. Moran.  1996. Spatial economic valuation: Benefits
transfer using geographical information systems.  Journal of
Environmental Management 48: 97-110.

Fisher, B., et al.  2008. Ecosystem services and economic theory:
Integration for policy-relevant research.  Ecological Applications 18
(8): 2050-2067.

Johnson, G., et al. 2010.  Service Path Attribute Networks (SPANs):
Spatially quantifying the flow of ecosystem services from landscapes
to people. Lecture Notes in Computer Science 6016: 238-253.

Leon-Gonzalez, R. and R. Scarpa 2008.  Improving multi-site benefit
functions via Bayesian model averaging: A new approach to benefit
transfer. Journal of Environmental Economics and Management 56: 50-68.

Marcot, B.G., et al. 2006.  Guidelines for developing and updating
Bayesian belief networks applied to ecological modeling and
conservation. Canadian Journal of Forest Research 36: 3063-3074.

McCann, R.K., et al.  2006. Bayesian belief networks: applications in
ecology and natural resource management. Canadian Journal of Forest
Research 36: 3053-3062.

Moeltner, K. and R.S. Rosenberger.  2007. Meta-regression and benefit
transfer: Data space, model space, and the quest for 'optimal scope.'
UNR Joint Economics Working Paper Series Working Paper No. 07-011.
Department of Resource Economics, University of Nevada, Reno.

Moeltner, K., et al.  2007. Meta-analysis and benefit transfer for
resource valuation, addressing classical challenges with Bayesian
modeling. Journal of Environmental Economics and Management 53:
250-269.

Moeltner, K. and Woodward, R.  2009. Meta-functional benefit transfer
for wetland valuation: Making the most of small samples. Environmental
and Resource Economics 42: 89-108.

Pearl, J. 1988.  Probabilistic reasoning in intelligent systems:
Networks of plausible inference.  Morgan-Kaufmann: San Francisco.

Raudsepp-Hearne, C., et al.  2010. Ecosystem service bundles for
analyzing tradeoffs in diverse landscapes.  Proceedings of the
National Academy of Sciences 107 (11): 5242-5247.

Ruhl, J.B., et al.  2007. The law and policy of ecosystem
services. Island Press: Washington, DC.

Tallis, H., et al.  2008. An ecosystem services framework to support
both practical conservation and economic development. Proceedings of
the National Academy of Sciences 105 (28): 9457-9464.

Tallis, H.T., et al. 2010.  InVEST 1.004 beta User's Guide. The
Natural Capital Project, Stanford.

Villa, F., et al. 2002.  Designing an integrated knowledge base to
support ecosystem services valuation. Ecological Economics 41:
445-456.

Villa, F., et al.  2009. ARIES (Artificial Intelligence for Ecosystem
Services): A new tool for ecosystem services assessment, planning, and
valuation.  Proceedings of the 11<sup>th</sup> Annual BIOECON
Conference on Economic Instruments to Enhance the Conservation and
Sustainable Use of Biodiversity, Venice, Italy, September, 2000

</div>

</div>
