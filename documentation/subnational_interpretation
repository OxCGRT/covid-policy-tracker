#Interpretation for subnational data 
This document describes how national and subnational policies relate in the primary OxCGRT [/data](data/) folder, and how this differs from secondary subnational-only data products found in other repos.

##Interaction with national policies
In the primary OxCGRT dataset described in this repo, we represent the overall policy impact on residents of the given jurisdiction. Subnational units coded in this dataset therefore account for those policies inherited from higher levels of government where applicable. 

To do this, Subnational-level responses are replaced with relevant NAT_GOV indicators when:
- The corresponding NAT_GOV indicator is general, not targeted 
- The corresponding NAT_GOV indicator is equal to or greater than the STATE_ALL indicator on the ordinal scale for that indicator
Subnational data in this repo use this method to account for interaction of state and national policies. Data for US states is available in this form.

##Relationship to subnational repos
The above method is distinct from that of the separate [USA](https://github.com/OxCGRT/USA-covid-policy) and [Brazil](https://github.com/OxCGRT/Brazil-covid-policy) subnational repos. These two subnational-only data products capture policies specific to a given jurisdiction and/or its sub-parts, and unlike this primary repo, do not include inherited policies from levels higher than the specified jurisdiction. This is the case even if those higher policies may supercede a jurisdiction's policy. For example, if a country has an international travel restriction that applies country-wide, this would not be registered in the C8 indicator of a US state's policy in the [USA](https://github.com/OxCGRT/USA-covid-policy) subnational repo, but would in this primary OxCGRT repo. 

##Further interpretation
Indicator meanings and interpretation of targeted/general distinctions for subnational data products are consistent with those in the existing OxCGRT [codebook](documentation/codebook.md). 

