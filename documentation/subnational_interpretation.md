# Interpretation for subnational data 

***version 1.0 <br/>06 August 2020***

This document describes how national and subnational policies are reported in the [/data](../data/) folder in our primary OxCGRT dataset [(OxCGRT/covid-policy-tracker)](https://github.com/OxCGRT/covid-policy-tracker), and how this differs from secondary subnational-only data products found in other repositories.

## Relationship to national policies in this repo

In the primary OxCGRT dataset described in this repository, we represent the overall policy environment that applies to residents of the given jurisdiction. Subnational units coded in this dataset therefore account for those policies 'inherited' from higher levels of government where applicable. 

To do this, we record policies made at the state level and below (eg we also include decisions of county or city governments), and this is termed "STATE_ALL". We then also record policies made by the national government, and this is termed NAT_GOV. The subnational data reported in our primary dataset is a combination of the two. We first start with STATE_ALL indicators, and then replace an indicator with the NAT_GOV counterpart if both of the following conditions are true:
1. The corresponding NAT_GOV policy is not geographically targeted, but rather applies nationwide
2. The corresponding NAT_GOV policy is equal to or greater than the STATE_ALL indicator on the ordinal scale for that indicator

Subnational data in this repo use this method to account for interaction of state and national policies. Data for US states is available in this form in the [data folder](../data/).

_Note: NAT_GOV and STATE_ALL are not reported in our primary dataset, and NAT_GOV is different to the national country-level data reported in our primary dataset. Our primary dataset reports on the entire policy environment in a country, and so includes decisions of national governments, state governments, and local governments all in one.

## More detailed data is published in subnational repositories

The above method is distinct from the data reported in the separate [OxCGRT/USA-covid-policy](https://github.com/OxCGRT/USA-covid-policy) and [OxCGRT/Brazil-covid-policy](https://github.com/OxCGRT/Brazil-covid-policy) subnational repos.

Unlike our primary dataset in this repository, these two subnational-only data products report the measures taken by individual levels of government, without including relevant measures from higher levels of government. That is to say, we have published NAT_GOV and STATE_ALL without combining them into a single measure (note: for Brazil we have further split STATE_ALL into STATE_GOV and city-level data).

## A concrete example

In many countries, the national government sets international travel restrictions that apply country-wide (indicator C8). This would not be registered in the C8 indicator of a state's policy (unless they took additional measures beyond that of the national government), and so our secondary datasets would not report any international travel controls for STATE_ALL.

However, in our primary dataset in this [OxCGRT/covid-policy-tracker](https://github.com/OxCGRT/covid-policy-tracker) repository, we would report the national governemnt's border controls against each state, as the policy is in force in those state.

## Further interpretation

Indicator meanings and interpretation of targeted/general distinctions for subnational data products are consistent with those in the existing OxCGRT [codebook](documentation/codebook.md). 

## Changelog of subnational guidance

- 06 August 2020: published v1 to GitHub
