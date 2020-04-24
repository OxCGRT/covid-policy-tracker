# IMPORTANT NOTE: 24-30 April database update

The OxCGRT is undergoing a major update and will be offline from Friday 24 April. ***The data here on GitHub and served through our API will no longer be "live" and updated in real time.*** It will be the data that was available on Friday 24 April.

Further, the dataset is already out of date for several countries. In preparation for this database update, we had to move resources away from data collection, so some countries have not been updated since mid-April.

We hope to be back online by Monday 27 April with a fresh back-end database, up-to-date data, and several new indicators. Some aspects of the update will continue into next week.

OxCGRT team, 24 April 2020

---

# Oxford Covid-19 Government Response Tracker (OxCGRT)

The Oxford Covid-19 Government Response Tracker (OxCGRT) collects systematic information on which governments have taken which measures, and when. This can help decision-makers and citizens understand the stringency of governmental responses in a consistent way, aiding efforts to fight the pandemic. The OxCGRT systematically collects information on several different common policy responses governments have taken, scores the stringency of such measures, and aggregates these scores into a common Stringency Index.

This is a project from the [Blavatnik School of Government](www.bsg.ox.ac.uk). More information on the OxCGRT is available on the school's website: https://www.bsg.ox.ac.uk/covidtracker. This README contains information about using the database.

---

__Cite as:__ Thomas Hale, Sam Webster, Anna Petherick, Toby Phillips, and Beatriz Kira. (2020). _Oxford COVID-19 Government Response Tracker_. Blavatnik School of Government.

---

## The database

OxCGRT collects publicly available information on 13 indicators of government response (S1-S13). This information is collected by a team of over 100 volunteers from the Oxford community and is updated continuously.

We also include statistics on the number of reported Covid-19 cases and deaths in each country. These are taken from the European Centre for Disease Prevention and Control ([ECDC](https://www.ecdc.europa.eu/en)) for most countries, and from the [JHU CSSE data repository](https://github.com/CSSEGISandData/COVID-19) for the Chinese special administrative regions of Hong Kong and Macau.

### Individual policy measures

Seven of the indicators (S1-S7) record policies around containment and social isoaltion, such as school closures and restrictions in movement. These are recorded on an ordinal scale that represents the level of strictness of the policy. Two of the indicators (S12 and S13) represent policies around testing and contact tracing, also recorded on an ordinal scale. The remainder (S8-S11) are financial indicators such as fiscal or monetary measures.

Six of the indicators (S1-S6) also have a flag for whether they are targeted to a specific geographical region (isgeneral=0) or whether they are a "general" policy that is applied countrywide (isgeneral=1).

- S1 - school closures (plus targeted/genral flag)
- S2 - workplace closures (plus targeted/gemeral flag)
- S3 - cancellation of public events (plus targeted/general flag)
- S4 - public transport closures (plus targeted/general flag)
- S5 - public information campaign (plus targeted/general flag)
- S6 - restrictions on domestic/internal movement (plus targeted/general flag)
- S7 - restrictions on international travel
- S8 - economic stimulus measures
- S9 - central bank interest rate
- S10 - emergency investment in healthcare
- S11 - investment in vaccines
- S12 - testing policy
- S13 - contact tracing policy

### Our working paper has more information

We have published a [working paper](https://www.bsg.ox.ac.uk/research/publications/variation-government-responses-covid-19) with our methodology, data collection protocols, and description of the individual indicators.

### Stringency index

The Stringency Index is an aggregation of the first seven indicators, S1 to S7. It reports a number between 0 to 100 that reflects the overall stringency of the governments response. This is a measure of how many of the first seven indicators (mostly around social isolation) a government has acted upon, and to what degree.

It does not take into account any fiscal or monetary responses (indicators S8-S11) or policies around testing and contact tracing (S12 and S13).

We have published a [short note with a detailed explanation](https://www.bsg.ox.ac.uk/sites/default/files/Calculation%20and%20presentation%20of%20the%20Stringency%20Index.pdf) of how the stringency index is calculated, and also how it is reported for days with incomplete data are handled.

## Using OxCGRT data

The OxCGRT is updated continuously in real time. There are numerous ways you can access the raw data.

### Getting data through our API
The most direct way to get real-time data from the OxCGRT is through our API. Documentation for this is [published here](https://covidtracker.bsg.ox.ac.uk/about-api).

### Getting data from this GitHub repository
<!-- ![Data link to OxCGRT](https://github.com/OxCGRT/covid-policy-tracker/workflows/Data%20link%20to%20OxCGRT/badge.svg) <-- status of connection to OxCGRT database -->

The [/data](data/) folder in this repo contains recent exports from the OxCGRT database. You are welcome to build applications that draw directly from this repository.
- The CSV file [/data/OxCGRT_latest.csv](data/OxCGRT_latest.csv) is a full export from the database presented in "list" format with each country-day as a single row. This CSV is updated every hour from the main database, and the badge above shows whether this data link is functioning correctly.
- The CSV file [/data/OxCGRT_latest_withnotes.csv](data/OxCGRT_latest_withnotes.csv) is a full export from the database in "list" format _with_ a column of notes from our data collectors for each indicator. This is also updated every hour from the main database. Please note that some of the comments contain commas and other characters interpreted as a delimiter, and so may cause problems when parsing this CSV file.
- The [/data/timeseries](data/timeseries/) folder contains individual timeseries for each indicator (except S8-S11, for which our data coverage is not consistent) in CSV format, as well as a combined Excel file with a tab for each indicator. This is updated periodically – usually daily – and the date will be listed in the commit description and at the bottom of each sheet.

### Data quality

It is important to understand the limitations of this dataset, most of which stem from the "live" nature of data collection. Our first goal is to publish a real-time dataset; but this carries risks. For instance, you may get a version of the database that was exported just as our team was half-way through entering new data, or that was exported in the window between an error being made and being fixed.

For details on how these issues around patchy or missing data affect our Stringency Index, please see our [short note on calculating the Stringency Index](https://www.bsg.ox.ac.uk/sites/default/files/Calculation%20and%20presentation%20of%20the%20Stringency%20Index.pdf).

- **Be very skeptical of reductions in stringency**. Incomplete or missing data will sometimes cause a dip in the calculated stringency index (we conservatively treat some missing values as 0). For most countries, a recent or short-term reduction in stringency level is the result of a data error, not a legitimate reduction in stringency.
- **Not all countries are equally up to date**. We try to ensure that all countries are updated at least once a week, and most are updated more frequently. But there will inevitably be "patchiness" within the last week.
- **For each country, some indicators will be missing in some days**. As our data collectors find information, they will update a country in real time. This means a country may only have up-to-date information for some indicators, but not all.
- **Some indicators and Stringency Index values will be changed retroactively.** We aim to have a second pair of eyes review every data point in the OxCGRT. As at 12 April 2020, the majority of our 150,000 data points are yet to be reviewed. Inevitably, some things may be tweaked in this review process, leading to changes to past dates. We recommend you frequently download fresh data from OxCGRT, rather than relying on an old export.
- **Null values are not the same as 0**. The gaps described above – where countries are not up to date, or where some indicators are missing – will be represented as null values. These should not be interpreted as a 0, although for the purposes of calculating our Stringency Index, we conservatively treat them as such.
- **You should ignore some values recorded for *isgeneral* variables**. Indicators S1-S6 are accompanied by an "isgeneral" variable to describe the geographical scope of the policy. Sometimes, due to data entry errors, we have isgeneral=1 when the underlying indicator is 0 or null. These cases should be disregarded. Only use isgeneral=1 values when the underlying indicator is 1 or higher.
- **Fiscal and monetary indicators are not evenly covered**. We do not yet have comprehensive and high quality coverage of our indicators S8-S11. Apart from missing data, there are also frequent duplicate entries. You should check the data carefully before using these indicators.

## Sample analysis

Here are several examples of the type of analysis enabled by OxCGRT:

### Analysis of specific countries

An individual chart of each country is in the [/images/country charts](images/country%20charts/) folder.

<img src="images/OxCGRT_six_countries.png" width=80%> 

<img src="images/OxCGRT_sixin1_bycases.png" width=80%>

<img src="images/OxCGRT_stringency_vs_cases.png" width=80%>

### Global comparisons

![World map of current stringency](images/OxCGRT_worldmap_stringency.png)

![World map of school closures](images/OxCGRT_worldmap_schools.png)
