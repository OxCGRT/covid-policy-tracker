# Codebook for the Oxford Covid-19 Government Response Tracker

***Codebook version 2.11 <br/>11 June 2021***

This document is the authoritative codebook for the Oxford Covid-19 Government Response Tracker ([GitHub repo](https://github.com/OxCGRT/covid-policy-tracker), [university website](https://www.bsg.ox.ac.uk/covidtracker)). The dataset contains 23 indicators and a miscellaneous notes field organised into five groups:
- [C - containment and closure policies](#containment-and-closure-policies)
- [E - economic policies](#economic-policies)
- [H - health system policies](#health-system-policies)
- [V - vaccination policies](#vaccination-policies)
- [M - miscellaneous policies](#miscellaneous-policies)

For more detailed guidance about the codebook and how we interpret the indicators, see the [coding interpretation guide](interpretation_guide.md). This ensures consistency, and standardizes coding across the database.

Updates to this codebook are recorded in the [changelog](#codebook-changelog) below.

Most indicators are recorded on an ordinal scale that represents the level of strictness of the policy. Four of the indicators (E3, E4, H4 and H5) are recorded as a US dollar value of fiscal spending. V1 and V2 record categorical data on eligible groups for vaccination in a population.

Government coronavirus policies often vary by region within countries. We code the most stringent government policy that is in place in a country/territory, as represented by the highest ordinal value. Sometimes the most stringent policy in a country/territory will only apply to a small part of the population. If the most stringent policy is only present in a limited geographic area or sector (eg perhaps only one state has implemented policies at a high level), we use a binary flag variable to denote this limited scope. Ten of the indicators (C1-C7, H1, H6 and H8) have a flag for whether they are "targeted" to a specific geographical region (flag=0) or whether they are a "general" policy that is applied across the whole country/territory (flag=1).) E1 has a flag to describe whether income support is for just formal sector workers (flag=0) or whether it includes informal workers as well (flag=1). H7 has a flag to describe whether vaccine policy is funded at cost to the individual (flag=0) or by government (flag=1).

As explained in our [index methodology documentation](index_methodology.md), an indicator with flag=0 is weighted lower than flag=1 when calculating overall index values. 

### Containment and closure policies

| ID | Name | Description | Measurement | Coding |
| --- | --- | --- | --- | --- |
| C1 | `C1_School closing` | Record closings of schools and universities | Ordinal scale | 0 - no measures <br/>1 - recommend closing or all schools open with alterations resulting in significant differences compared to non-Covid-19 operations <br/>2 - require closing (only some levels or categories, eg just high school, or just public schools) <br/>3 - require closing all levels <br/>Blank - no data |
| | `C1_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C2 | `C2_Workplace closing` | Record closings of workplaces | Ordinal scale | 0 - no measures <br/>1 - recommend closing (or recommend work from home) or all businesses open with alterations resulting in significant differences compared to non-Covid-19 operation <br/>2 - require closing (or work from home) for some sectors or categories of workers <br/>3 - require closing (or work from home) for all-but-essential workplaces (eg grocery stores, doctors) <br/>Blank - no data |
| | `C2_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C3 | `C3_Cancel public events` | Record cancelling public events | Ordinal scale | 0 - no measures <br/>1 - recommend cancelling <br/>2 - require cancelling <br/>Blank - no data |
| | `C3_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C4 | `C4_Restrictions on gatherings` | Record limits on gatherings | Ordinal scale | 0 - no restrictions <br/>1 - restrictions on very large gatherings (the limit is above 1000 people) <br/>2 - restrictions on gatherings between 101-1000 people <br/>3 - restrictions on gatherings between 11-100 people <br/>4 - restrictions on gatherings of 10 people or less <br/>Blank - no data |
| | `C4_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C5 | `C5_Close public transport` | Record closing of public transport | Ordinal scale | 0 - no measures <br/>1 - recommend closing (or significantly reduce volume/route/means of transport available) <br/>2 - require closing (or prohibit most citizens from using it) <br/>Blank - no data |
| | `C5_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C6 | `C6_Stay at home requirements` | Record orders to "shelter-in-place" and otherwise confine to the home | Ordinal scale | 0 - no measures <br/>1 - recommend not leaving house <br/>2 - require not leaving house with exceptions for daily exercise, grocery shopping, and 'essential' trips <br/>3 - require not leaving house with minimal exceptions (eg allowed to leave once a week, or only one person can leave at a time, etc) <br/>Blank - no data |
| | `C6_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C7 | `C7_Restrictions on internal movement` | Record restrictions on internal movement between cities/regions | Ordinal scale | 0 - no measures <br/>1 - recommend not to travel between regions/cities <br/>2 - internal movement restrictions in place <br/>Blank - no data |
| | `C7_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |
| C8 | `C8_International travel controls` | Record restrictions on international travel <br/><br/>Note: this records policy for foreign travellers, not citizens | Ordinal scale | 0 - no restrictions <br/>1 - screening arrivals <br/>2 - quarantine arrivals from some or all regions <br/>3 - ban arrivals from some regions <br/>4 - ban on all regions or total border closure <br/>Blank - no data |

### Economic policies

| ID | Name | Description | Measurement | Coding |
| --- | --- | --- | --- | --- |
| E1 | `E1_Income support` <br/>(for households) | Record if the government is providing direct cash payments to people who lose their jobs or cannot work. <br/><br/>Note: only includes payments to firms if explicitly linked to payroll/salaries | Ordinal scale | 0 - no income support <br/>1 - government is replacing less than 50% of lost salary (or if a flat sum, it is less than 50% median salary) <br/>2 - government is replacing 50% or more of lost salary (or if a flat sum, it is greater than 50% median salary) <br/>Blank - no data |
| | `E1_Flag` | | Binary flag for sectoral scope | 0 - formal sector workers only or informal sector workers only <br/>1 - all workers
| E2 | `E2_Debt/contract relief` <br/>(for households) | Record if the government is freezing financial obligations for households (eg stopping loan repayments, preventing services like water from stopping, or banning evictions) | Ordinal scale | 0 - no debt/contract relief <br/>1 - narrow relief, specific to one kind of contract <br/>2 - broad debt/contract relief |
| E3 | `E3_Fiscal measures` | Announced economic stimulus spending <br/><br/>Note: only record amount additional to previously announced spending | USD | Record monetary value in USD of fiscal stimuli, includes any spending or tax cuts NOT included in E4, H4 or H5 <br/>0 - no new spending that day <br/>Blank - no data |
| E4 | `E4_International support` | Announced offers of Covid-19 related aid spending to other countries <br/><br/>Note: only record amount additional to previously announced spending | USD | Record monetary value in USD <br/>0 - no new spending that day <br/>Blank - no data |

### Health system policies

| ID | Name | Description | Measurement | Coding |
| --- | --- | --- | --- | --- |
| H1 | `H1_Public information campaigns` | Record presence of public info campaigns | Ordinal scale | 0 - no Covid-19 public information campaign <br/>1 - public officials urging caution about Covid-19 <br/>2- coordinated public information campaign (eg across traditional and social media) <br/>Blank - no data |
| | `H1_Flag` | | Binary flag for geographic scope |  0 - targeted <br/>1- general <br/>Blank - no data |
| H2 | `H2_Testing policy` | Record government policy on who has access to testing <br/><br/>Note: this records policies about testing for current infection (PCR tests) not testing for immunity (antibody test) | Ordinal scale | 0 - no testing policy <br/>1 - only those who both (a) have symptoms AND (b) meet specific criteria (eg key workers, admitted to hospital, came into contact with a known case, returned from overseas) <br/>2 - testing of anyone showing Covid-19 symptoms <br/>3 - open public testing (eg "drive through" testing available to asymptomatic people) <br/>Blank - no data |
| H3 | `H3_Contact tracing` | Record government policy on contact tracing after a positive diagnosis <br/><br/>Note: we are looking for policies that would identify all people potentially exposed to Covid-19; voluntary bluetooth apps are unlikely to achieve this | Ordinal scale | 0 - no contact tracing <br/>1 - limited contact tracing; not done for all cases <br/>2 - comprehensive contact tracing; done for all identified cases |
| H4 | `H4_Emergency investment in healthcare` | Announced short term spending on healthcare system, eg hospitals, masks, etc <br/><br/>Note: only record amount additional to previously announced spending | USD | Record monetary value in USD <br/>0 - no new spending that day <br/>Blank - no data |
| H5 | `H5_Investment in vaccines` | Announced public spending on Covid-19 vaccine development <br/><br/>Note: only record amount additional to previously announced spending | USD | Record monetary value in USD <br/>0 - no new spending that day <br/>Blank - no data |
| H6 | `H6_Facial Coverings` | Record policies on the use of facial coverings outside the home <br/> | Ordinal scale | 0 - No policy <br/>1 - Recommended <br/>2 - Required in some specified shared/public spaces outside the home with other people present, or some situations when social distancing not possible <br/>3 - Required in all shared/public spaces outside the home with other people present or all situations when social distancing not possible <br/>4 - Required outside the home at all times regardless of location or presence of other people |
| | `H6_Flag` | | Binary flag for geographic scope |  0 - targeted <br/>1- general <br/>Blank - no data |
| H7 | `H7_Vaccination Policy` | Record policies for vaccine delivery for different groups <br/> | Ordinal scale | 0 - No availability <br/>1 - Availability for ONE of following: key workers/ clinically vulnerable groups (non elderly) / elderly groups <br/>2 - Availability for TWO of following: key workers/ clinically vulnerable groups (non elderly) / elderly groups <br/>3 - Availability for ALL of following: key workers/ clinically vulnerable groups (non elderly) / elderly groups <br/>4 - Availability for all three plus partial additional availability (select broad groups/ages) <br/>5 - Universal availability | 
| | `H7_Flag` | | Binary flag for cost |  0 - At cost to individual (or funded by NGO, insurance, or partially government funded) <br/>1- No or minimal cost to individual (government funded or subsidised) <br/>Blank - no data |
| H8 | `H8_Protection of elderly people` | Record policies for protecting elderly people (as defined locally) in Long Term Care Facilities and/or the community and home setting | Ordinal scale | 0 - no measures <br/>1 - Recommended isolation, hygiene, and visitor restriction measures in LTCFs and/or elderly  people to stay at home <br/>2 - Narrow restrictions for isolation, hygiene in LTCFs, some limitations on external visitors and/or restrictions protecting elderly people at home <br/>3 - Extensive restrictions for isolation and hygiene in LTCFs, all non-essential external visitors prohibited, and/or all elderly people required to stay at home and not leave the home with minimal exceptions, and receive no external visitors <br/>Blank - no data | 
| | `H8_Flag` | | Binary flag for geographic scope | 0 - targeted <br/>1- general <br/>Blank - no data |

### Vaccination policies

| ID | Name | Description | Measurement | Coding |
| --- | --- | --- | --- | --- |
| V1 | `V1_Vaccine prioritisation` | Reports the existence of a prioritised plan for vaccine rollout | Ranked list of categories of eligible groups | 0 - no policy <br/>Universal/generally available <br/> -Infants 0-4 yrs <br/>- Young people 5-16 yrs <br/> - General 16+ yrs <br/>-General 20+ yrs <br/>-General 25+ yrs <br/>-General 30+ yrs <br/>-General 35+ yrs <br/>-General 40+ yrs <br/>-General 45+ yrs <br/>-General 50+ yrs <br/>-General 55+ yrs <br/>-General 60+ yrs <br/>-General 65+ yrs <br/>-General 70+ yrs <br/>-General 75+ yrs <br/>-General 80+ yrs <br/>-At Risk 16+ yrs <br/>-At Risk 20+ yrs <br/>- At Risk 25+ yrs <br/>-At Risk 30+ yrs <br/>-At Risk 35+ yrs <br/>-At Risk 40+ yrs <br/>-At Risk 45+ yrs <br/>- At Risk 50+ yrs<br/>- At Risk 55+ yrs<br/>- At Risk 60+ yrs <br/>- At Risk 65+ yrs<br/>-At Risk 70+ yrs <br/>- At Risk 75+ yrs <br/>- At Risk 80+ yrs <br/>- Airport/Border/Airline Staf <br/>- Clinically vulnerable/chronic illness/significant underlying health condition (excluding elderly and disabled) <br/>- Crowded/communal living conditions (dormitories for migrant workers, temporary accommodations <br/>- Disabled People <br/>- Educator <br/>- Ethnic minoritie <br/>- Factory worker <br/>- Frontline/essential workers (when subcategories not specified <br/>- Frontline retail workers <br/>- Healthcare workers/carers (excluding care home staff <br/>- Military <br/>- Other 'high contact' professions/groups (taxi drivers, security guards <br/>- People living with a vulnerable/shielding person or other priority grou <br/>- Police/ first responders <br/>- Pregnant people <br/>- Primary and secondary school students <br/>- Religious/Spiritual Leaders <br/>- Residents in an elderly care home <br/>- Staff working in an elderly care home <br/>- Tertiary education students



### Miscellaneous policies

| ID | Name | Description | Measurement | Coding |
| --- | --- | --- | --- | --- |
| M1 | `M1_Wildcard` | Record policy announcements that do not fit anywhere else | Free text notes field | Note unusual or interesting interventions that are worth flagging  |

### Vaccination policies summary CSV interpretation

## Codebook changelog

- 11 June 2021 v2.11 added vaccination policy data (V1-V3)
- 5 May 2021 v2.10 added 'or all businesses open with alterations resulting in significant differences compared to non-Covid-19 operations' to C2 level 1
- 18 March 2021 v2.9 added H8 'Protection of elderly people' indicator
- 05 March 2021 v2.8 added 'non elderly' to definition of Clinically vulnerable groups' for H7
- 14 January 2021 v2.7 changed 'country' to 'country/territory' and removed 'private' from C4 definition, replaced E1 flag 'formal sector workers only' to 'formal sector workers only or informal sector workers only', and 'informal workers too' to 'all workers'
- 09 December 2020 v2.6 added H7 Vaccination policy indicator
- 04 November 2020 v2.5 added C1 expanded definition of '1' and added targeted/general flag to H6 indicator
- 22 October 2020 v2.4 added H6 Facial Coverings indicator
- 05 July 2020: v2.3 add better explanation of targeted/general flags in intro
- 22 May 2020: v2.2 changed description of E1=2 from "replacing more than 50% of lost salary" to "replacing 50% or more of lost salary"
- 11 May 2020: moved v2 codebook to GitHub
