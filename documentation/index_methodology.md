# Methodology for calculating indices

***Index methodology version 3.6 <br/>5 May 2021***

The Oxford Covid-19 Government Response Tracker ([GitHub repo](https://github.com/OxCGRT/covid-policy-tracker), [university website](https://www.bsg.ox.ac.uk/covidtracker)) tracks individual policy measures across 20 indicators. We also calculate several indices to give an overall impression of government activity, and this page describes how these indices are calculated. Changes to this methodology are recorded in the [changelog](#index-methodology-changelog) below.

All of our indices are simple averages of the individual component indicators. This is described in equation 1 below where _k_ is the number of component indicators in an index and _I<sub>j</sub>_ is the [sub-index score](#calculating-sub-index-scores-for-each-indicator) for an individual indicator.

![overall mean equation](https://latex.codecogs.com/png.latex?%281%29%5Cqquad%20index%3D%5Cfrac%7B1%7D%7Bk%7D%5Csum_%7Bj%3D1%7D%5E%7Bk%7DI_%7Bj%7D)

The different indices are comprised as follows:

| Index name | _k_ | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | E1 | E2 | E3 | E4 | H1 | H2 | H3 | H4 | H5 | H6 | H7 | H8 | M1 |
| --- | ---: | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |--- |--- |--- |
| Government response index | 16 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | `x` | `x` | `x` | | | `x` | `x` | `x` | | | |
| Containment and health index | 14 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | `x` | `x` | | |`x` | `x` | `x` | | | |
| Stringency index | 9 | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | | | | | | |
| Economic support index | 2 | | | | | | | | | `x` | `x` | | | | | | | | | |
| [Legacy stringency index](#legacy-stringency-index) | 7 | `x` | `x` | `?` | `?` | `x` | `?` | `?` | `x` | | | | | `x` | | | | | | |

Two versions of each indicator are present in the database. A regular version which will return `null` values if there is not enough data to calculate the index, and a "display" version which will extraploate to smooth over the last seven days of the index based on the most recent complete data. This is explained [below](#dealing-with-gaps-in-the-data-for-display-purposes).

## Calculating sub-index scores for each indicator

All of the indices use ordinal indicators where policies a ranked on a simple numerical scale. The project also records five non-ordinal indicators – E3, E4, H4, H5 and M1 – but these are not used in our index calculations.

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

Note that the database only contains flag values if the indicator has a non-zero value. If a government has no policy for a given indicator (ie the indicator equals zero) then the corresponding flag is blank/null in the database. For the purposes of calculating the index, this is equivalent to a sub-index score of zero. In other words, _I<sub>j,t</sub>_=0 if _v<sub>j,t</sub>_=0.

![sub-index score equation](https://latex.codecogs.com/png.latex?%282%29%5Cqquad%20I_%7Bj%2Ct%7D%3D100%5Cfrac%7Bv_%7Bj%2Ct%7D-0.5%28F_%7Bj%7D-f_%7Bj%2Ct%7D%29%7D%7BN_%7Bj%7D%7D)

(_if v<sub>j,t</sub>=0 then the function F<sub>j</sub>-f<sub>j,t</sub> is also treated as 0, see paragraph above._)

Our data is not always fully compelte and sometimes indicators are missing. We make the conservative assumption that an absence of data corresponds to a sub-index score (_I<sub>j,t</sub>_) of zero.

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

## Legacy stringency index

We also report a legacy stringency index that approximates the logic of the first version of the Stringency Index, which only had seven components under our [old database structure](../legacy_data_20200425) with the old indicators S1-S7. We generally do not recommend using this legacy index, but it may be useful for continuity purposes.

The legacy indicator only uses seven indicators, and it chooses a single indicator between C3 and C4, and between C6 and C7, selecting whichever of those pairs provides a higher sub-index score. This is because C3 and C4 aim to measure the information previously measured by S3, and similarly for C6, C7 and the old S6. This method, shown in equation 3, faithfully recreates the logic of the old stringency index.

![legacy stringency equation](https://latex.codecogs.com/png.latex?%283%29%5Cqquad%20SI_%7Blegacy%7D%3D%5Cfrac%7B1%7D%7B7%7D%20%5Cleft%20%28I_%7BC1%7D&plus;I_%7BC2%7D&plus;max%28I_%7BC3%7D%2CI_%7BC4%7D%29&plus;I_%7BC5%7D&plus;max%28I_%7BC6%7D%2CI_%7BC7%7D%29&plus;I_%7BC8%7D&plus;I_%7BH1%7D%20%5Cright%20%29)

The individual sub-index scores for the legacy index are calculated through a slightly different formula to the one described in equation 2 above. This formula is described in equation 4 below (with a seperate formula for C8, the only indicator in this index without a flagged variable).

![legacy stringency sub-index equation](https://latex.codecogs.com/png.latex?%284%29%5Cqquad%20I_%7Bj%2Ct%7D%3D100%5Cleft%20%28%5Cfrac%7Bv_%7Bj%2Ct%7D&plus;f_%7Bj%2Ct%7D%7D%7BN_%7Bj%7D&plus;1%7D%5Cright%29%5Cquad%5Cmid%5Cquad%20I_%7BC8%2Ct%7D%3D100%5Cleft%28%5Cfrac%7Bv_%7B%20_%7BC8%2Ct%7D%7D%7D%7BN_%7BC8%7D%7D%20%5Cright%29)

## Index methodology changelog

- 5 May 2021: replaced '19 indicators' with '20 indicators'
- 15 March 2021: added H8 Protection of elderly people 
- 14 January 2021: replaced 'country' with 'country/territory'
- 09 December 2020: added H7 Vaccination Policy and edited format of x for H7 column for Government response index and Containment health index rows to 'x'
- 29 October 2020: edited format of x for H6 column for Government response index and Containment and health index rows to `x`
- 22 October 2020: added H6 Facial Coverings indicator
- 25 May 2020: implemented v3 of index methodology. Altered sub-index forumula, created new indices (overall government response, containment & health, and economic support) and moved documentation to GitHub here
