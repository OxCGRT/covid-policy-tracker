# Methodology for calculating indices

The Oxford Covid-19 Government Response Tracker (OxCGRT) tracks individual policy measures, we also calculate several indices to give an overall impression of government activity.

All of our indexes are simple averages of the individual component indicators. Described in formula 1 below where _k_ is the number of component indicators in an index and _I<sub>j</sub>_ is the sub-index score for an individual indicator.

![overall mean equation](https://latex.codecogs.com/png.latex?%281%29%5Cqquad%20I%3D%5Cfrac%7B1%7D%7Bk%7D%5Csum_%7Bj%3D1%7D%5E%7Bk%7DI_%7Bj%7D)

The different indices are comprised as follows:

| Index name | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | E1 | E2 | E3 | E4 | H1 | H2 | H3 | H4 | H5 | M1 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Government response index | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | `x` | `x` | `x` | | | |
| Containment and health index | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | `x` | `x` | | | |
| Stringency index | `x` | `x` | `x` | `x` | `x` | `x` | `x` | `x` | | | | | `x` | | | | | |
| Economic support index | | | | | | | | | `x` | `x` | | | | | | | | |

### Calculating sub-index scores for each indicators

All of the indices use ordinal indicators where policies a ranked on a simple numerical scale. The non-ordinal indicators in the OxCGRT – E3, E4, H4, H5 and M1 – are not used in our index calculations.

Some indicators – C1-C7, E1 and H1 – have an additional binary flag that can be either 0 or 1. For C1-C7 and H1 this corresponds to the geographic scope of the policy. For E1, this flag corresponds to the sectoral scope of income support.

The codebook has details about what the different values represent. Because different indicators _j_ have different maximum values _N<sub>j</sub>_ in their ordinal scales, each sub-index score must be calculated separately. The different indicators are:

| Indicator | _N<sub>j</sub>_ | _F<sub>j</sub>_ |
| --- | --- | --- |
| C1 | `3 (0, 1, 2, 3)` | `1` |
| C2 | `3 (0, 1, 2, 3)` | `1` |
| C3 | `2 (0, 1, 2)` | `1` |
| C4 | `4 (0, 1, 2, 3, 4)` | `1` |
| C5 | `2 (0, 1, 2)` | `1` |
| C6 | `3 (0, 1, 2, 3)` | `1` |
| C7 | `2 (0, 1, 2)` | `1` |
| C8 | `4 (0, 1, 2, 3, 4)` | `0` |
| E1 | `2 (0, 1, 2)` | `1` |
| E2 | `2 (0, 1, 2)` | `0` |
| H1 | `2 (0, 1, 2)` | `1` |
| H2 | `3 (0, 1, 2, 3)` | `0` |
| H3 | `2 (0, 1, 2)` | `0` |

Each sub-index score (_I_) for any given indicator (_j_) on any given day (_t_), is calculated by the function described in equation 2 based on the following parameters:

- the maximum value of the indicator (_N<sub>j</sub>_)
- whether that indicator has a flag (_F<sub>j</sub>_)
- the recorded policy value on the ordinal scale (_v<sub>j,t</sub>_)
- the recorded binary flag for that indicator (_f<sub>j,t</sub>_)

![sub-index score equation](https://latex.codecogs.com/png.latex?%282%29%5Cqquad%20I_%7Bj%2Ct%7D%3D100%5Cfrac%7Bv_%7Bj%2Ct%7D&plus;0.5%28F_%7Bj%2Ct%7D-f_%7Bj%2Ct%7D%29%7D%7BN_%7Bj%7D%7D)

This normalises the different ordinal scales to produce a sub-index score between 0 and 100 where a lack of a flag represents a half-step between points on the ordinal scale.

Note that the index only reports flag values if the indicator has a non-zero value. If the indicator is reporting that there is no policy in place (zero) then the corresponding flag is left blank. For the purposes of calculating the index, this is equivalent to _I<sub>j,t</sub>_=0.

We make the conservative assumption that an absence of data corresponds to a sub-index score (_I<sub>j,t</sub>_) of zero.

Here is an explicit example of the calculation:

| Indicator | _v<sub>j,t</sub>_ | _f<sub>j,t</sub>_ | | _N<sub>j</sub>_ | _F<sub>j</sub>_ | | _I<sub>j,t</sub> |
| --- | --- | --- | --- | --- | --- | --- | ---: |
| C1 | No data | No data | | 3 | 1 | | 0 |
| C2 | 2 | 1 | | 3 | 1 | | 66 |
| C3 | 2 | 1 | | 2 | 1 | | 100 |
| C4 | 3 | 0 | | 4 | 1 | | 62.5 |
| C5 | 0 | N/A | | 2 | 1 | | 0 |
| C6 | 3 | 0 | | 3 | 1 | | 83.3 |
| C7 | 2 | 0 | | 2 | 1 | | 75 |
| C8 | 2 | N/A | | 4 | 0 | | 50 |
| E1 | 1 | 1 | | 2 | 1 | | 50 |
| E2 | 1 | N/A | | 2 | 0 | | 50 |
| H1 | 1 | 0 | | 2 | 1 | | 25 |
| H2 | 2 | N/A | | 3 | 0 | | 66.6 |
| H3 | 2 | N/A | | 2 | 0 | | 100 |
| --- | --- | --- | --- | --- | --- | --- | ---: |
| | | | | | | | | 56.09 |

![sub-index score equation with flag](https://latex.codecogs.com/png.latex?I_%7Bj%7D%3D%5Cfrac%7BC_%7Bj%7D&plus;0.5%28f_%7Bj%7D%29%7D%7BN_%7Bj%7D&plus;0.5%7D)

![sub-index score equation without flag](https://latex.codecogs.com/png.latex?I_%7Bj%7D%3D%5Cfrac%7BC_%7Bj%7D%7D%7BN_%7Bj%7D%7D)

### Dealing with gaps in the data for display purposes

Because data are updated on twice-weekly cycles, but not every country is updated in every cycle,recent dates may be prone to missing data. If fewer than _k-1_ indicators are present for an index on any given day, the index calculation is rejected and no value is returned.

To increase consistency of recent data points which are perhaps mid contribution, index values pertaining to the past seven days are rejected if they have fewer policy indicators than another day in the past seven days, i.e. if there is another recent data point with all _k_ indicators included, then no index will be calculated for dates with _k-1_.

Further, we produce two versions of each index. One with the raw calculated index values, plus we produce a "display" version which will "smooth" over gaps in the last seven days, populating each date with the last available "good" data point.

For example, the date at the time of writing was 22 May. The table below gives an example of which index calculations would be rejected based on the number of policy indicators with data on each data. In this table, we will consider the government response index where _k_=13.

| Date | No. of valid indicators | No. of indicators in index (_k_) | Raw index | "Display" index |
| --- | --- | --- | --- | ---: |
| 10/05/2020 | 11 | 13 | `null` | `null` |
| 11/05/2020 | 12 | 13 | 60 | 60 |
| 12/05/2020 | 10 | 13 | `null` | `null` |
| 13/05/2020 | 13 | 13 | 65 | 65 |
| 14/05/2020 | 10 | 13 | `null` | `null` |
| 15/05/2020 | 10 | 13 | `null` | `null` |
| 16/05/2020 | 10 | 13 | `null` | 65 |
| 17/05/2020 | 13 | 13 | 70 | 70 |
| 18/05/2020 | 13 | 13 | 75 | 75 |
| 19/05/2020 | 12 | 13 | `null` | 75 |
| 20/05/2020 | 12 | 13 | `null` | 75 |
| 21/05/2020 | 6 | 13 | `null` | 75 |
| 22/05/2020 (today) | 4 | 13 | `null` | 75 |

### Legacy stringency index

We also report a legacy stringency index that approximates the logic of the former version of the Stringency Index, which only had seven components under our old database structure. This legacy indicator should only be used for continuity purposes.

The legacy indicator only uses seven indicators, and it chooses a single indicator between C3 and C4, and between C6 and C7, selecting whichever of those pairs provides a higher sub-index score. This is because C3 and C4 aim to measure the information previously measured by S3, and similarly for C6, C7 and the old S6. This method faithfully recreates the logic of the old stringency index.

![legacy stringency equation](https://latex.codecogs.com/png.latex?%283%29%5Cqquad%20SI_%7Blegacy%7D%3D%5Cfrac%7B1%7D%7B7%7D%20%5Cleft%20%28I_%7BC1%7D&plus;I_%7BC2%7D&plus;max%28I_%7BC3%7D%2CI_%7BC4%7D%29&plus;I_%7BC5%7D&plus;max%28I_%7BC6%7D%2CI_%7BC7%7D%29&plus;I_%7BC8%7D&plus;I_%7BH1%7D%20%5Cright%20%29)
