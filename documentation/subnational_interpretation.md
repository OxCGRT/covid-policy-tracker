# Interpretation for subnational data 

***version 2.3 <br/>11 June 2021***

This document describes how national and subnational policies are reported in the [/data](../data/) folder in our primary OxCGRT dataset [(OxCGRT/covid-policy-tracker)](https://github.com/OxCGRT/covid-policy-tracker), and how this differs from secondary subnational-only data products found in other repositories.

## Relationship to national policies in this repo

In the primary OxCGRT dataset described in this repository, we represent the overall policy environment that applies to residents of the given jurisdiction. Subnational units coded in this dataset therefore account for those policies 'inherited' from higher levels of government where applicable. 

To do this, we record policies made at the state level or equivalent and below (eg we also include decisions of county or city governments), and this is termed STATE_WIDE. We then also record policies made by the national government, and this is termed NAT_GOV. The subnational data reported in our primary dataset is a combination of the two. We first start with STATE_WIDE indicators, and then replace an indicator with the NAT_GOV counterpart if both of the following conditions are true:
1. The corresponding NAT_GOV policy is not geographically targeted, but rather applies nationwide
2. The corresponding NAT_GOV policy is equal to or greater than the STATE_WIDE or STATE_GOV indicator on the ordinal scale for that indicator
The resulting observations are marked with a_TOTAL suffix. For example, observations labelled BRA NAT_TOTAL describe Brazil as a whole, and observations labelled with USA as the country/territory code, US_TX as the region code, and STATE_TOTAL as the jurisdiction describe the US state of Texas as a whole. In this way, NAT_TOTAL and STATE_TOTAL measures in the core dataset are comparable, in that they show the totality of policies in effect within a given jurisdiction. 

If a state robustly institutionalises a national recommendation or requirement under their own policy, for example by republishing national guidance as the state’s own, this can be coded as a state policy intervention, as well as one introduced by the national government, and thus coded independently under the subnational jurisdiction coding.

Subnational data in this repo use this method to account for interaction of state and national policies. 

_Note: NAT_GOV and STATE_WIDE are not reported in our primary dataset, and NAT_GOV is different to the national country/territory-level data reported in our primary dataset. Our primary dataset reports on the entire policy environment in a country/territory, and so includes decisions of national governments, state governments, and local governments all in one._

## More detailed data is published in subnational repositories

The above method is distinct from the data reported in the separate [OxCGRT/USA-covid-policy](https://github.com/OxCGRT/USA-covid-policy) and [OxCGRT/Brazil-covid-policy](https://github.com/OxCGRT/Brazil-covid-policy) subnational repos.

Unlike our primary dataset in this repository, these two subnational-only data products report the measures taken by individual levels of government, without including relevant measures from higher levels of government. That is to say, we have published NAT_GOV and STATE_WIDE without combining them into a single measure (note: for Brazil we have further split STATE_WIDE into STATE_GOV and city-level CITY_WIDE data).

## A concrete example

In many countries, the national government sets international travel restrictions that apply country/territory-wide (indicator C8). This would not be registered in the C8 indicator of a state's policy (unless they took additional measures beyond that of the national government), and so our secondary datasets would not report any international travel controls for STATE_WIDE.

However, in our primary dataset in this [OxCGRT/covid-policy-tracker](https://github.com/OxCGRT/covid-policy-tracker) repository, we would report the national government's border controls against each state as part of STATE_TOTAL, as the policy is in force in those state.

## Further interpretation

Indicator meanings and interpretation of targeted/general distinctions for subnational data products are consistent with those in the existing OxCGRT [codebook](documentation/codebook.md). 

## Changelog of subnational guidance
- 11 June 2021: added 'state level or equivalent' and replaced 'federal' with 'national'
- 5 May 2021: added guidance regarding how to code states institutionalising federal policies at the subnational level
- 14 January 2021: replaced 'country' with 'country/territory'
- 09 December 2020: published v2 to GitHub
- 06 August 2020: published v1 to GitHub
