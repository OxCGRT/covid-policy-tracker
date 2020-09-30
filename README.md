**UPDATE:** SUBNATIONAL DATA<br/>**25 August 2020 update**

This coming Thursday evening UK time (**27 August**) we will integrate sub-national data into our two main CSVs: [data/OxCGRT_latest.csv](data/OxCGRT_latest.csv) and [data/OxCGRT_latest_withnotes.csv](OxCGRT_latest_withnotes.csv).

This may affect how you use our data. For example, for any given date, there will be 53 entries where `CountryCode==USA` (the existing national entry will now be accompanied by 50 states, Washington DC, and the US Virgin Islands). This may break your workflow if you assume there will be a single entry for each date with `CountryCode==USA`.

To distinguish between these rows in the dataset, there will be two new variables: `RegionName` and `RegionCode`. If you wish to select just for national-level data, the simplest way would be to exclude any rows where `RegionCode` contains any text (in other words: filter just for rows where `RegionCode` is null).

Once this update is complete, we will delete the temporary CSV ([data/OxCGRT_US_states_temp.csv](data/OxCGRT_US_states_temp.csv)) with US state data that was uploaded on 06 August 2020.

<br/>
<br/>

Previous update **06 August 2020**

Today (6 August) we have published USA state level data. Our [/data](data/) folder has a separate [CSV](data/OxCGRT_US_states_temp.csv) with data for all US states, presented in a way that is comparable to our country-level data. We have also published individual state charts in the [/images/US states](images/US_states/) folder, and a [working paper](https://www.bsg.ox.ac.uk/research/publications/variation-us-states-responses-covid-19) with more detailed analysis.
For additional data on US states, we have a separate [OxCGRT/USA-covid-policy](https://github.com/OxCGRT/USA-covid-policy) repository.

---
---

# Oxford Covid-19 Government Response Tracker (OxCGRT)

The Oxford Covid-19 Government Response Tracker (OxCGRT) collects systematic information on which governments have taken which measures, and when. This can help decision-makers and citizens understand governmental responses in a consistent way, aiding efforts to fight the pandemic. The OxCGRT systematically collects information on several different common policy responses governments have taken, records these policies on a scale to reflect the extent of government action, and aggregates these scores into a suite of policy indices.

This is a project from the [Blavatnik School of Government](www.bsg.ox.ac.uk). More information on the OxCGRT is available on the school's website: https://www.bsg.ox.ac.uk/covidtracker. This README contains information about using the database.

---

__Cite as:__ Thomas Hale, Sam Webster, Anna Petherick, Toby Phillips, and Beatriz Kira. (2020). _Oxford COVID-19 Government Response Tracker_. Blavatnik School of Government.

---

## The database

OxCGRT collects publicly available information on 17 indicators of government response. This information is collected by a team of over 200 volunteers from the Oxford community and is updated continuously.

We also include statistics on the number of reported Covid-19 cases and deaths in each country. These are taken from the European Centre for Disease Prevention and Control ([ECDC](https://www.ecdc.europa.eu/en)) for most countries, and from the [JHU CSSE data repository](https://github.com/CSSEGISandData/COVID-19) for US states and the Chinese special administrative regions of Hong Kong and Macau.

### Individual policy measures

Full descriptions of the policy indicators and their meaning can be found in our [codebook](documentation/codebook.md). For more detailed guidance about the codebook and how we interpret the indicators, see the [coding interpretation guide](coding_interpretation_guide.md). This ensures consistency, and standardizes coding across the database.

Eight of the policy indicators (C1-C8) record information on [_containment and closure_ policies](documentation/codebook.md#containment-and-closure-policies), such as school closures and restrictions in movement. Four of the indicators (E1-E4) record [_economic_ policies](documentation/codebook.md#economic-policies) such as income support to citizens or provision of foreign aid. And five indicators (H1-H5) record [_health system_ policies](documentation/codebook.md#health-system-policies) such as the Covid-19 testing regime or emergency investments into healthcare.

Finally, we have a [miscellaneous indicator (M1)](documentation/codebook.md#miscellaneous-policies) for notes that do not fit elsewhere.

### Policy indices

To help make sense of the data, we have produced four indices that aggregate the data into a single number. Each of these indices report a number between 0 to 100 that reflects the level of the governments response along certain dimensions. This is a measure of how many of the relevant indicators a government has acted upon, and to what degree. The index cannot say whether a government's policy has been implemented effectively.

- overall government response index (all indicators)
- containment and health index (all C and H indicators)
- stringency index (all C indicators, plus H1 which records public information campaigns)
- economic support index (all E indicators)

(_Note: these only include indicators recorded on ordinal scales, so they all exclude E3, E4, H4, H5, and M1._)

The [documentation folder](documentation/) contains an [index methodology](documentation/index_methodology.md) page explaining how the different indexes are calculated and how they are reported for days with incomplete data. This also describes the methodology for the [legacy stringency index](documentation/index_methodology.md#legacy-stringency-index) which is based on the [old](#legacy-database-structure-from-before-25-April-2020) database structure in place prior to 25 April 2020.

### Subnational data

In addition to country-level data, our primary dataset additionally includes some subnational data. So far we have incorporated data for US states and UK devolved nations into the primary dataset on this covid-policy-tracker repository. These subnational entities are included in our [/data/OxCGRT_latest.csv](data/OxCGRT_latest.csv) and [/data/OxCGRT_latest_withnotes.csv](data/OxCGRT_latest_withnotes.csv). But no other CSVs at this stage.

Subnational data can be interpreted using the main [codebook](documentation/codebook.md), with additional guidance on subnational-specific interpretation available in the [documentation folder](documentation/subnational_interpretation.md). The state data included in our primary dataset aims to describe the overall policy environment that applies to residents of the state, and so includes policies set by the national government where those values are more stringent than state-level action. For data that focuses only on subnational policies, see our additional datasets in the [OxCGRT/USA-covid-policy](https://github.com/OxCGRT/USA-covid-policy) and [OxCGRT/Brazil-covid-policy](https://github.com/OxCGRT/Brazil-covid-policy) respositories.

### Our documentation and working papers have more information

The most up-to-date description of database components is here in the [documentation folder](documentation/) of this GitHub repo, which contains a detailed [codebook](documentation/codebook.md), [index methodology](documentation/index_methodology.md), a [coding interpretation guide](coding_interpretation_guide.md), and notes on [subnational interpretation](documentation/subnational_interpretation.md).

We have also published a national [working paper](https://www.bsg.ox.ac.uk/research/publications/variation-government-responses-covid-19) with our national methodology, data collection protocols, and description of the individual indicators. 

### Legacy database structure (from before 25 April 2020)

Prior to 25 April 2020 the OxCGRT had a structure of 13 indicators (labelled S1-S13). Data up until this point is archived and still available in the [/legacy_data_20200425](legacy_data_20200425/) folder.

## Using OxCGRT data

The OxCGRT is updated continuously in real time. There are numerous ways you can access the raw data.

### Getting data from this GitHub repository
![Data link to OxCGRT](https://github.com/OxCGRT/covid-policy-tracker/workflows/Data%20link%20to%20OxCGRT/badge.svg) <-- status of connection to OxCGRT database

The [/data](data/) folder in this repo contains recent exports from the OxCGRT database. You are welcome to build applications that draw directly from this repository.
- The CSV file [/data/OxCGRT_latest.csv](data/OxCGRT_latest.csv) reports country- and state-level data presented in "country-day" format (or "state-day" as the case may be), with a list of all indicators for each country as a single row each day. This CSV is updated every hour from the main database, and the badge above shows whether this data link is functioning correctly.
- The CSV file [/data/OxCGRT_latest_withnotes.csv](data/OxCGRT_latest_withnotes.csv) reports country- and state-level data in "country-day" format _with_ a column of notes from our data collectors for each indicator. This is also updated every hour from the main database. Please note that some of the comments contain commas and other characters interpreted as a delimiter, and so may cause problems when parsing this CSV file.
- The CSV file [/data/OxCGRT_latest_allchanges.csv](data/OxCGRT_latest_allchanges.csv) reports country-level data with a list of every _change_ to the database. Every time a policy value changes, or every time a note is added to an indicator, it is represented with it's own new row. (This does not include subnational data.)
- The [/data/timeseries](data/timeseries/) folder reports country-level data as individual timeseries for each indicator (except for the non-ordinal indicators E3, E4, H4, H5 and M1) in CSV format, as well as a combined Excel file with a tab for each indicator. This is updated periodically – usually daily – and the date will be listed in the commit description and at the bottom of each sheet. (This does not include subnational data.)
- The CSV file [/data/OxCGRT_US_states_temp.csv](data/OxCGRT_US_states_temp.csv) is a temporary CSV that presents _only US state-level data_ in "state-day" format, with a column of notes from our data collectors for each indicator. This is updated manually. **This has now been integrated into the two primary CSVs at the top of this list, and this temporary CSV will be deleted from the repo in September 2020.** 

### Getting data through our API
You can also get OxCGRT through our API. Documentation for this is [published here](https://covidtracker.bsg.ox.ac.uk/about-api).

### Data quality

It is important to understand the limitations of this dataset, most of which stem from the "live" nature of data collection. Our first goal is to publish a real-time dataset; but this carries risks. For instance, you may get a version of the database that was exported just as our team was half-way through entering new data, or that was exported in the window between an error being made and being fixed.

For details on how these issues around patchy or missing data affect our index calculations, please see our [documentation on calculating indices](documentation/index_methodology.md).

- **Be skeptical of reductions in index values**. Incomplete or missing data will sometimes cause a dip in the calculated  index (we conservatively treat some missing values as 0). For most countries, a reduction in index level that is recent, relatively small (less than 10 points), or only lasts a couple of days, is more likely the result of missing data rather than a legitimate reduction in the underlying policy.
- **Not all countries are equally up to date**. We try to ensure that all countries and relevant subnational units are updated at least once a week, and most countries are updated more frequently. But there will inevitably be "patchiness" within the last week.
- **For each country, some indicators will be missing in some days**. As our data collectors find information, they will update a country in real time. This means a country may only have up-to-date information for some indicators, but not all.
- **Some indicators (and therefore, index values) will be changed retroactively.** We aim to have a second pair of eyes review every data point in the OxCGRT. As at 19 May 2020, the majority of our 400,000 data points are yet to be reviewed. Inevitably, some things may be tweaked in this review process, leading to changes to past dates. We recommend you frequently download fresh data from OxCGRT, rather than relying on an old export.
- **Null values are not the same as 0**. The gaps described above – where countries are not up to date, or where some indicators are missing – will be represented as null values. These should not be interpreted as a 0, although for the purposes of calculating our indices, we conservatively treat them as such.
- **Fiscal and monetary indicators are not evenly covered**. We do not yet have comprehensive and high quality coverage of our indicators E3, E4, H4, and H5. You should check the data carefully before using these indicators.

## Sample analysis

Here are several examples of the type of analysis enabled by OxCGRT:

### Analysis of specific countries

An individual chart of each country is in the [/images/country charts](images/country_charts/) folder.

<img src="images/OxCGRT_six_countries.png" width=80%>

<img src="images/OxCGRT_sixin1_bycases.png" width=80%>

<img src="images/OxCGRT_govresponse_vs_cases.png" width=80%>

### Global comparisons

<img src="images/OxCGRT_indices_vs_time.png" width=80%>

![World map of current government responses](images/OxCGRT_worldmap_govresponse.png)

![World map of school closures](images/OxCGRT_worldmap_schools.png)
