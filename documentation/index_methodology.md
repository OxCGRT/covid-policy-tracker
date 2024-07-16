# Methodology for calculating indices

***Index methodology version 4.0 <br/>27 July 2022***

| **Major update, July 2022** |
| --- |
| In July 2022 the OxCGRT implemented data changes which incorporate different policies applying to vaccinated and non-vaccinated people. We now publish eight versions of each index, including versions that take averages between the policies that apply to vaccinated and non-vaccinated people. The documentation in this GitHub repository reflects these changes, and we have also published a [PDF summary](https://www.bsg.ox.ac.uk/sites/default/files/OxCGRT%20–%C2%A0What%27s%20changed%20summary%2022%20Jul%202022.pdf). <br/><br/>Our [legacy repo](https://github.com/OxCGRT/covid-policy-tracker-legacy) also publishes the original indices. |

The Oxford Covid-19 Government Response Tracker ([GitHub repo](https://github.com/OxCGRT/covid-policy-tracker), [university website](https://www.bsg.ox.ac.uk/covidtracker)) tracks individual policy measures across 21 indicators. We also calculate several indices to give an overall impression of government activity, and this page describes how these indices are calculated. Changes to this methodology are recorded in the [changelog](#index-methodology-changelog) below.

This document is structured as follows:

- [Indices](#indices), which gives a high-level overview of the components of each of our 4 types of indices (the Government Response Index, Containment and Health Index, Stringency Index, and Economic Support Index), as well as the different variations of each.
- [Index calculation](#index-calculation), which describes the formulas used to calculate each variation of an index from its component indicators.
- [Calculating sub-index scores for each indicator](#calculating-sub-index-scores-for-each-indicator), describes the process we go through to normalise each indicator into a sub-index
- [Dealing with gaps for display purposes](#dealing-with-gaps-in-the-data-for-display-purposes), summarises how we deal with missing data when calculating our indices.

## Indices

The different indices are comprised as follows:

| Index name | _k_ | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | E1 | E2 | E3 | E4 | H1 | H2 | H3 | H4 | H5 | H6 | H7 | H8 | M1 |
| --- | ---: | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |--- |--- |--- |
| Government response index | 16 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | `x` | `x` | `x` | | | `x` | `x` | `x` | | | |
| Containment and health index | 14 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | `x` | `x` | | |`x` | `x` | `x` | | | |
| Stringency index | 9 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | | | | | | |
| Economic support index | 2 | | | | | | | | | `x` | `x` | | | | | | | | | |
| [Legacy stringency index](#legacy-stringency-index) | 7 | `x` | `x` | `?` | `?` | `x` | `?` | `?` | `x` | | | | | `x` | | | | | | |

We now publish 8 versions of each index – four different versions with different treatment of vaccine-differentiated policies, and then for each of those four, two different versions that handle gaps in data differently.

The four versions with substantial differences are denoted as follows:
- `_Nonvax` – constructs the index using policies that apply to non-vaccinated people (either `non-vaccinated` (NV) policies if present, or otherwise using `everyone` (E) policies).
- `_Vax` – constructs the index using policies that apply to vaccinated people (either `vaccinated` (V) policies if present, or otherwise using `everyone` (E) policies).
- `_SimpleAverage` – takes the sum of `_Nonvax` and `_Vax` indices and divides them by 2.
- `_WeightedAverage` – takes an average of the `_Nonvax` and `_Vax` indices and weights this by the proportion of the population that are fully vaccinated.

In our simple [`OxCGRT_latest.csv`](/data) CSVs we report indices with the suffix `_Average` (eg. `StringencyIndex_Average`). This is alwauys the weighted average, except for the few jurisdictions for which we do not have vaccinated rate data (and thus cannot calculate a weighted average), in which case it is the simple average.

For each of these four versions of each index, we then publish two versions:
- A regular version which will return `null` values if there is not enough data to calculate the index.
- A `_ForDisplay` version which will extrapolate the index to smooth over the last seven days where there is incomplete data. This is described further in our discussion below on [dealing with gaps for display purposes](#dealing-with-gaps-in-the-data-for-display-purposes).

In our [legacy repo](https://github.com/OxCGRT/covid-policy-tracker-legacy), we publish indices as simple averages of the individual component indicators. Calculations of these indices can be found [below](#index-calculation) 



## Index calculation

In this section, we explore how indices are calculated following differentiation of policies.

#### Non-vaccinated and Vaccinated Indices

For a given jurisdiction, our non-vaccinated and vaccinated indices are simple averages of the individual sub-indices, one for each indicator that comprises the index. This is described in equation 1 below where _k_ is the number of component indicators in an index and _I<sub>j</sub>_ is the [sub-index score](#calculating-sub-index-scores-for-each-indicator) for an individual indicator. If a component indicator is one of the ten for which we record differentiated policy, then we will use either:
- the NV or V version of the policy (in the non-vaccinated or vaccinated index respectively) where there is a differentiated policy
- the E (everyone) version of the policy for both the non-vaccinated and vaccinated index where there is no differentiated policy

![non vac vac equation](https://latex.codecogs.com/png.latex?%281%29%5Cqquad%20index%3D%5Cfrac%7B1%7D%7Bk%7D%5Csum_%7Bj%3D1%7D%5E%7Bk%7DI_%7Bj%7D)

This results in two versions of each index that report the overall policy settings that apply to, respectively, non-vaccinated people and vaccinated people.

#### Simple Average Indices

For a given jurisdiction, our simple average indices are the sum of the vaccinated and the non-vaccinated indices divided by two. This is described in equation 2 below where _v_ is the index for the vaccinated, and _nv_ is the index score for the non-vaccinated.

![simple avg equation](https://latex.codecogs.com/svg.image?(2)index&space;=&space;(index_{v}&space;&plus;&space;index_{nv})/2)


#### Weighted Average Indices

This weights the index value using the non-vaccinated/vaccinated values based on the proportion of the population that are vaccinated with a complete initial protocol using the data from Our World in Data vaccination dataset's 'fullyvaccinatedperhundred' (with gaps filled) dataset available [here](https://ourworldindata.org/covid-vaccinations).
- This value is also published in the csv in a column labelled "Population Vaccinated", next to the cases/deaths columns.

Dealing with gaps for display purposes. The population-weighted average uses the following display logic:
- If no data available before or equal to date -> 0% vaccination is assumed
- If no "fully_vaccinated_per_hundred" for a specific date -> pull forward the value from the last day it was present

For a given jurisdiction, we first calculated indices for the vaccinated and the non vaccinated. We then weight these values by the percent of the population which are fully vaccinated. This is described in equation 3 below where _v_ is the index for the vaccinated, _nv_ is the index score for the non-vaccinated, _W<sub>v</sub>_ is the weight of population vaccinated (i.e., % vaccinated), and  _W<sub>nv</sub>_ is the weight of population who are non-vaccinated (i.e., % non-vaccinated). Note that the denominator always adds up to 100 (i.e., sum of % of vaccinated and non-vaccinated people in a given country).

![weighted avg equation](https://latex.codecogs.com/svg.image?(3)index&space;=&space;[(index_{v}&space;*&space;W_{v})&space;&plus;&space;(index_{nv}&space;*&space;W_{nv})]/100)


#### Legacy Repo Indices

All of our indices in our legacy folder are simple averages of the individual component indicators. This is described in equation 4 below where _k_ is the number of component indicators in an index and _I<sub>j</sub>_ is the sub-index score for an individual indicator.


![legacy_repo](https://latex.codecogs.com/svg.image?(4)index%3D%5Cfrac%7B1%7D%7Bk%7D%5Csum_%7Bj%3D1%7D%5E%7Bk%7DI_%7Bj%7D)

## Calculating sub-index scores for each indicator

All of the indices use ordinal indicators where policies a ranked on a simple numerical scale. The project also records five non-ordinal indicators – E3, E4, H4, H5 and M1 – but these are not used in our index calculations. As of August 2021, E3, E4, and H4 will no longer be updated. The data remains present in the CSV files.

Some indicators – C1-C7, E1, H1, H6 and H7 – have an additional binary flag variable that can be either 0 or 1. For C1-C7, H1 and H6 this corresponds to the geographic scope of the policy. For E1, this flag variable corresponds to the sectoral scope of income support. For H7, this flag variable corresponds to whether the individual or government is funding the vaccination.

The [codebook](codebook.md) has details about each indicator and what the different values represent.

Because different indicators (_j_) have different maximum values (_N<sub>j</sub>_) in their ordinal scales, and only some have flag variables, each sub-index score must be calculated separately. The different indicators are:

| Indicator | Max. value (_N<sub>j</sub>_) | Flag? (_F<sub>j</sub>_) |
| --- | --- | --- |
| C1 | 3 (0, 1, 2, 3) | yes=1 |
| C2 | 3 (0, 1, 2, 3) | yes=1 |
| C3 | 2 (0, 1, 2) | yes=1 |
| C4 | 4 (0, 1, 2, 3, 4) | yes=1 |
| C5 | 2 (0, 1, 2) | yes=1 |
| C6 | 3 (0, 1, 2, 3) | yes=1 |
| C7 | 2 (0, 1, 2) | yes=1 |
| C8 | 4 (0, 1, 2, 3, 4) | no=0 |
| E1 | 2 (0, 1, 2) | yes=1 |
| E2 | 2 (0, 1, 2) | no=0 |
| H1 | 2 (0, 1, 2) | yes=1 |
| H2 | 3 (0, 1, 2, 3) | no=0 |
| H3 | 2 (0, 1, 2) | no=0 |
| H6 | 4 (0, 1, 2, 3, 4) | yes=1 |
| H7 | 5 (0, 1, 2, 3, 4, 5) | yes=1 |
| H8 | 3 (0, 1, 2, 3) | yes=1 |

Each sub-index score (_I_) for any given indicator (_j_) on any given day (_t_), is calculated by the function described in equation 2 based on the following parameters:

- the maximum value of the indicator (_N<sub>j</sub>_)
- whether that indicator has a flag (_F<sub>j</sub>_=1 if the indicator has a flag variable, or 0 if the indicator does not have a flag variable)
- the recorded policy value on the ordinal scale (_v<sub>j,t</sub>_)
- the recorded binary flag for that indicator (_f<sub>j,t</sub>_)

This normalises the different ordinal scales to produce a sub-index score between 0 and 100 where each full point on the ordinal scale is equally spaced. For indicators that do have a flag variable, if this flag is recorded as 0 (ie if the policy is geographically _targeted_ or for E1 if the support only applies to _informal sector workers_) then this is treated as a half-step between ordinal values.

Note that the database only contains flag values if the indicator has a non-zero value. If a government has no policy for a given indicator (ie. the indicator equals zero) then the corresponding flag is blank/null in the database. For the purposes of calculating the index, this is equivalent to a sub-index score of zero. In other words, _I<sub>j,t</sub>_=0 if _v<sub>j,t</sub>_=0.

![sub-index score equation](https://latex.codecogs.com/svg.image?(5)I_%7Bj%2Ct%7D%3D100%5Cfrac%7Bv_%7Bj%2Ct%7D-0.5%28F_%7Bj%7D-f_%7Bj%2Ct%7D%29%7D%7BN_%7Bj%7D%7D)

(_if v<sub>j,t</sub>=0 then the function F<sub>j</sub>-f<sub>j,t</sub> is also treated as 0, see paragraph above._)

Our data is not always fully complete and sometimes indicators are missing. We make the conservative assumption that an absence of data corresponds to a sub-index score (_I<sub>j,t</sub>_) of zero.

Here is an explicit example of the calculation for a given country/territory on a single day:

| Indicator | _v<sub>j,t</sub>_ | _f<sub>j,t</sub>_ | | _N<sub>j</sub>_ | _F<sub>j</sub>_ | | _I<sub>j,t</sub>_ |
| --- | ---: | ---: | --- | ---: | ---: | --- | ---: |
| C1 | 2 | 1 | | 3 | yes=1 | | 66.67 |
| C2 | `no data` | `no data` | | 3 | yes=1 | | 0.00 |
| C3 | 2 | 0 | | 2 | yes=1 | | 75.00 |
| C4 | 2 | 0 | | 4 | yes=1 | | 37.50 |
| C5 | 0 | `null` | | 2 | yes=1 | | 0.00 |
| C6 | 1 | 0 | | 3 | yes=1 | | 16.67 |
| C7 | 1 | 1 | | 2 | yes=1 | | 50.00 |
| C8 | 3 | N/A | | 4 | no=0 | | 75.00 |
| E1 | 2 | 0 | | 2 | yes=1 | | 75.00 |
| E2 | 2 | N/A | | 2 | no=0 | | 100.00 |
| H1 | 2 | 0 | | 2 | yes=1 | | 75.00 |
| H2 | 3 | N/A | | 3 | no=0 | | 100.00 |
| H3 | 2 | N/A | | 2 | no=0 | | 100.00 |
| H6 | 2 | 0 | | 4 | yes=1 | | 37.50 |
| H7 | 2 | 1 | | 5 | yes=1 | | 40.00|
| H8 | 2 | 1 | | 3 | yes=1 | | 66.66|
| **Index** | | | | | | | |
| Government response | | | | | | | 57.18 |
| Containment and health | | | | | | | 52.86 |
| Stringency | | | | | | | 43.98 |
| Economic support | | | | | | | 87.50 |

## Dealing with gaps in the data for display purposes

Because data are updated on twice-weekly cycles, but not every country/territory is updated in every cycle,recent dates may be prone to missing data. If fewer than _k-1_ indicators are present for an index on any given day, the index calculation is rejected and no value is returned. For the economic support indicator, where _k_=2, the index calculation is rejected if either of the two indicators are missing.

To increase consistency of recent data points which are perhaps mid contribution, index values pertaining to the past seven days are rejected if they have fewer policy indicators than another day in the past seven days, ie if there is another recent data point with all _k_ indicators included, then no index will be calculated for dates with _k-1_.

Further, we produce two versions of each index. One with the raw calculated index values, plus we produce a "display" version which will "smooth" over gaps in the last seven days, populating each date with the last available "good" data point.

For example, the date at the time of writing was 22 October. The table below gives an example of which index calculations would be rejected based on the number of policy indicators with data on each data. In this table, we will consider the overall government response index where _k_=13.

| Date | No. of valid indicators | No. of indicators in index (_k_) | Raw index | "Display" index |
| --- | :---: | :---: | ---: | ---: |
| 10/10/2020 | 12 | 14 | `null` | `null` |
| 11/10/2020 | 13 | 14 | 60 | 60 |
| 12/10/2020 | 11 | 14 | `null` | `null` |
| 13/10/2020 | 14 | 14 | 65 | 65 |
| 14/10/2020 | 11 | 14 | `null` | `null` |
| 15/10/2020 | 11 | 14 | `null` | `null` |
| 16/10/2020 | 11 | 14 | `null` | 65 |
| 17/10/2020 | 14 | 14 | 70 | 70 |
| 18/10/2020 | 14 | 14 | 75 | 75 |
| 19/10/2020 | 13 | 14 | `null` | 75 |
| 20/10/2020 | 13 | 14 | `null` | 75 |
| 21/10/2020 | 7 | 14 | `null` | 75 |
| 22/10/2020 (today) | 5 | 14 | `null` | 75 |

## April 2020 legacy stringency index

We also report a pre-April 2020 legacy stringency index that approximates the logic of the original version of the Stringency Index, which only had seven components under our old database structure with the old indicators S1-S7 (you can access this data on our [legacy repo](https://github.com/OxCGRT/covid-policy-tracker-legacy)). We generally do not recommend using this legacy index, but it may be useful for continuity purposes.

The legacy indicator only uses seven indicators, and it chooses a single indicator between C3 and C4, and between C6 and C7, selecting whichever of those pairs provides a higher sub-index score. This is because C3 and C4 aim to measure the information previously measured by S3, and similarly for C6, C7 and the old S6. This method, shown in equation 6, faithfully recreates the logic of the old stringency index.

![legacy stringency equation](https://latex.codecogs.com/svg.image?(6)SI_%7Blegacy%7D%3D%5Cfrac%7B1%7D%7B7%7D%20%5Cleft%20%28I_%7BC1%7D&plus;I_%7BC2%7D&plus;max%28I_%7BC3%7D%2CI_%7BC4%7D%29&plus;I_%7BC5%7D&plus;max%28I_%7BC6%7D%2CI_%7BC7%7D%29&plus;I_%7BC8%7D&plus;I_%7BH1%7D%20%5Cright%20%29)

The individual sub-index scores for the legacy index are calculated through a slightly different formula to the one described in equation 2 above. This formula is described in equation 7 below (with a seperate formula for C8, the only indicator in this index without a flagged variable).

![legacy stringency sub-index equation](https://latex.codecogs.com/svg.image?(7)I_%7Bj%2Ct%7D%3D100%5Cleft%20%28%5Cfrac%7Bv_%7Bj%2Ct%7D&plus;f_%7Bj%2Ct%7D%7D%7BN_%7Bj%7D&plus;1%7D%5Cright%29%5Cquad%5Cmid%5Cquad%20I_%7BC8%2Ct%7D%3D100%5Cleft%28%5Cfrac%7Bv_%7B%20_%7BC8%2Ct%7D%7D%7D%7BN_%7BC8%7D%7D%20%5Cright%29)

Please note that this is NOT present in the differentiated vaccination coding csv. The legacy folder contains the two previous versions of the OxCGRT data structure.

## Index methodology changelog

- 27 July 2022: differentiated data structure incorporated
- 27 September 2021: note to state no longer updating E3, E4 and H4
- 5 May 2021: replaced '19 indicators' with '20 indicators'
- 15 March 2021: added H8 Protection of elderly people 
- 14 January 2021: replaced 'country' with 'country/territory'
- 09 December 2020: added H7 Vaccination Policy and edited format of x for H7 column for Government response index and Containment health index rows to 'x'
- 29 October 2020: edited format of x for H6 column for Government response index and Containment and health index rows to `x`
- 22 October 2020: added H6 Facial Coverings indicator
- 25 May 2020: implemented v3 of index methodology. Altered sub-index forumula, created new indices (overall government response, containment & health, and economic support) and moved documentation to GitHub here
