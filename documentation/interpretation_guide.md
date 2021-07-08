# OxCGRT Coding Interpretation Guide
***Version 1.10 <br/>Date: 8 July 2021***

This guide details the resolutions of frequently asked [codebook](codebook.md) interpretation queries, where indicators may be interpreted in different ways. This is in order to ensure consistency, and standardize coding across the database. Queries related specifically to subnational data are labelled as such.

Updates to this coding interpretation are recorded in the [changelog](#Interpretation-Guide-changelog) below.

## Guidance by codebook indicator

### C1 - School Closures

- In October 2020 the definition of C1 was expanded at level 1, to include both recommendations and significant differences compared to non-COVID 19 operations. This means even in the absence of a recommendation to close, we may report a jurisdiction at C1=1 if they impose social distancing, capacity limitations or other substantial public health precautions that result in significant differences as compared to usual, non-Covid-19 operations. For example, hybrid in-person/online learning models to reduce the number of individuals in a classroom could justify a code of 1. 
- School closures *and* university closures are captured in C1. 
- Different governments use different wording (e.g. soft-closing, recommend, strongly recommend, recommend without restricting civil liberty), so we standardize what these mean in practice. If the situation is that all schools are closed, or policies in place make it impossible for them to open and meet these requirements, then that would count as a full closure. 
- Childcare, nurseries, language courses, and driving schools, do not count as educational closures. These are recorded as workplaces under C2
- If schools are closed, and this same closure policy then rolls into school holidays, we keep the code the same, for example ‘all levels of education remain closed’. This coding would only go down only once students actually return, when schools reopen
- If only children of essential workers are allowed in schools, this is reported as a closure for the general public
- If in-person teaching is suspended and all  instruction is online, this is reported as closed (physically closed).
- Some schools only open for exams, but not for classes. In this case, if schools are open for a one-off exam, for example one that is an hour long, or on one day only, this would not change the coding, so school closures would remain at a 3 if all levels are otherwise closed.If exams are running for multiple sessions, on multiple days, or even over multiple weeks, this is a similar situation to classes being open for some groups (2). Note that after the exam period ends, schools may jump back up to a 3 if all levels of education are then closed.
- If teachers are back in school to prepare for the new school year, but no students are allowed back, this would not alter the coding, as no students are present in person for education.
- If the situation is that schools are in theory allowed to open, but all schools remain closed, or policies in place make it impossible for them to open and meet these requirements, then that would count as a full closure.
- If individual school districts have the authority to decide closures/openings, we generally record policies conservatively with a ’targeted’ flag, as recording ‘general’ policies would require a high level of confidence that all schools in a jurisdiction are closed. If the state/nation is transitioning from a period of state or nationally induced total closure (3G) to giving individual districts the authority to choose, and some districts still follow the stricter policy, this would usually be represented as 3T. 
- We take account of summer school openings. If schools have been closed (3) but then some summer school is allowed, the value would change (likely 3T if some school districts remain totally closed, or a 2G if summer school has a ‘general’ country/territory wide scope). Summer school or other vacation-based programming includes substantial school-run educational programming such as entrance examination classes, remedial classes, or summer term courses, but does not include more peripheral activities such as recreational summer camps. 
- If a narrowly defined list of university courses which rely on essential in-person teaching, for example medical programs, are permitted to operate as an exemption, but all other in-person university teaching is cancelled, we treat this as a closure of universities.

###  C2- Workplace closing

- When non-essential workplaces are meant to be closed but many people are still going to work regardless, we report the official government policy. In these cases we make a note that people may not be complying with the policy.
- If workplaces can reopen under sanitation and social distancing requirements – e.g. up to 30% of capacity, and only outdoor seats – this is a 1 (recommend closing). Restrictions are still in place, and the 1 (recommend) captures the extent of these. 
- Voluntary closures are not the same thing as closures mandated by government policy. If a workplace voluntarily closes their business or makes their staff work from home – even if that employer is the government – this does not count under C2.  
- If a government publishes a list of essential business, we almost always defer to this list. Where the official list of 'essential activities' is very long, particularly expansive or contains unusual inclusions, to the point the policy could be reasonably interpreted as a 2, it is up to the coder’s best judgement on a case-by-case basis, and this is recorded in detail in the note. We try to be mindful of cases where governments may declare every business ‘essential’ or use other terminology that is inconsistent with general practice. In the absence of a list we code based on the below list of essential businesses.
- Businesses usually considered to be essential are: Healthcare, groceries, take-out food, hardware stores, plumbers/electricians, legal services, education preparations (teachers planning courses), limited business operations support (tiny staff capacity to ensure remote working can continue).
- Some businesses that are not essential: In-person retail, personal grooming (salons, spas, barbers etc), dine-in restaurants, movie theaters, entertainment/theme parks, nightclubs.
- For phased reopening of businesses, if there are new workplaces being added to the list of places allowed to open every week, but some places remain closed, we report 2 for the period, adding notes explaining which sectors/businesses are allowed to open each week. If some sectors remain closed, the coding would remain a 2 (some sectors required to close).
- Airports and schools would not count as "some businesses" in the C2 indicator here. If these workplaces have been closed by government policy decisions, this will be captured in other indicators (eg C1 School Closures and C8 International Travel Controls). Therefore, if all businesses are open, but schools remain closed, the school closing is not considered in C2. 

### C3- Cancel Public Events

- When private gatherings of only 10 or less are permitted (e.g. C4=4), this restriction would prevent public events from taking place, so they are recorded as required to cancel, unless there is a specific policy in place permitting public gatherings to go ahead.
- When all public gatherings are cancelled, but people can still go to church, we record this as a 2 (all gatherings cancelled), but make a note about the exception for religious gatherings. 
- There is no explicit cut off point for a ‘mass gathering’. If really large events, such as political protests, can go ahead, but with strict social distancing and hygiene measures in place, this could be reported as 'recommended'. 
- If a venue for public events is able to open (eg. a concert hall), but with a specified percentage of original capacity, this is reported at the 1 level. 
- If public events are banned, but one large event was able to go ahead with stringent social distancing measures as a one off (e.g. the F1 Grand Prix), this is recorded as a 2. This is consistent with the logic where if people are able to attend religious gatherings, but in general all other events were cancelled we do not change the code, but record this with a detailed note. This captures the dominant trend in place in a country/territory or state.

### C4- Restrictions on gatherings 

- When there are variations in numbers for gatherings (e.g. gatherings are banned for more than 5 people with the exceptions of funerals/weddings/outdoor gatherings where it is 30 people) we report the stricter (in this case 5 people indoor) policy while including the less strict outdoor/wedding/funeral gathering limit in the notes.
- A ban on any gatherings outside of the house would be a 4, as most households are reasonably assumed to be of 10 or less people.
- If there are restrictions in gatherings based on the capacity of indoor spaces (e.g. up to 30% of the capacity), but there is no mention of any clear cut-off point, we record as 0 adding a note explaining the restriction. If the indoor place is also a workplace (eg restaurant) we would include the note under C2 as well.
 
### C5- Public Transportation

- *Some examples that could indicate a 0 (no policy):*
    - Public transport is open but with social distancing and mask wearing requirements.
- *Some examples that could indicate a 1 (recommended):* 
    - Encouraging public transport usage only by essential workers, and discouraging use by members of public, closing major routes, closing all but specific service routes (ex: services for persons with disabilities and the elderly), number of services running is significantly reduced. If an increased number of buses have been put on the roads in order to dilute capacity, and enable greater social distancing, the rationale of the C5 indicator would capture this by coding ‘recommended’, as the spirit of the indicator is to reflect reduced capacity in any transportation unit, and the intention of limiting the numbers of people present.
- *Some examples that could indicate a 2 (required):*
    - The general public are prohibited from public transport (exceptions allowed for essential workers or some other specific category), total shutdowns of services to align with other movement restrictions.
- If closures of transport seem to be primarily the result of decreasing demand rather than deliberate government policy to prevent spreading, this is judged by our coders on a case-by-case basis, but if there are substantial changes to schedules we would consider coding a 1.

### C6- Stay at Home Order

- If the government policy is that people should stay home, but people don’t seem to be actually doing this in reality, we still report the official government policy. This would usually be accompanied by note that people may not be complying with this in reality.
- We record curfews (eg. where people are not allowed out between 6pm and 6am, or people only allowed for 1 hour a day) as a 2. If people cannot leave the house for multiple days at a time (eg can only go out on a specific day of the week), this would be reported as a 3 for total confinement. 
- If during non-curfew hours people can go out of the house for non-essential trips, this is still reported as a 2 to fully represent the requirement to limit movement as a result of the curfew hours.
- For clinically vulnerable groups of people strongly recommended or required to shield at home, we record this as a 1 (recommended) with a ‘general’ flag (if nationwide).

### C7- Restrictions on Internal Movement

- Unless made explicit in a policy, a stay at home order (C6) should not be interpreted as a requirement not to travel (C7), as domestic travel could still be permitted. If there was an explicit restriction on travel (eg. stay-at-home and only allowed within 5km radius for exercise or groceries) then this could also be coded under C7.
- **For subnational (state-level) data:** C7 is used to record state-level border closures where a state restricts entry from other states from another state, as well as recording restrictions on movement within the state.
- *Some examples that could indicate a 1:* 
    - Voluntary quarantines, non-intrusive checks at the state border (ex: asking where you will be quarantining but not following up extensively), asking residents of one specific city to not cross the border with a neighboring city  
- *Some examples that could indicate a 2:* 
    - Closing interstate highways/waterways, prohibiting or banning travel from certain regions, requirement of negative test result,  intensive checks on quarantine, requiring quarantine in a hotel or other standardized state-run facility
If there are restrictions for the circulation of private cars based on certain criteria (e.g. ending of the license number) to reduce the number of vehicles on the streets, we also report it as restriction of internal movement.


### C8-  International Travel Controls

- This indicator does not have a binary flag variable to reflect geographic variation in policies. Therefore, we generally record the level of policy that applies everywhere across the jurisdiction - the highest common value of policy nationwide or statewide. We do not report any policies of a higher value that are only available in limited areas.  *For example* if one airport is screening passenger arrivals, but the majority of them are not, this would not be recorded as a 1. All airports across the country/territory would need to be screening before this policy could be seen to apply generally and be recorded.
- If visitors are meant to self quarantine/isolate after travelling to certain areas, but there are no enforcement or tracking measures in place, we record the official policy accordingly, and make a note that the situation on the ground may not reflect this.
- If a country/territory is still repatriating citizens from overseas, but otherwise has closed borders, this still counts as a full border closure (4). This indicator focuses largely on requirements for foriegn passengers, in the sense that even during “total closure”, countries will still let their citizens cross the border to return home (although may subject them to quarantine).
- **For subnational (state-level) data:** As international travel is usually an issue for the national government, subnational governments will rarely implement relevant policies for C8. The sorts of state-level activity that would be recorded under C8 include when individual airports proactively screen passengers, or if states created their own mandatory quarantines for international travelers.
- If country/territory borders are completely closed, but it is because of a civil war, or other non-covid related reasons, this will still be reported as a 4. While this is not a covid-specific policy, in practice the border is still closed so we want to best represent the lived reality of people living there, in order to understand the effect this could have on COVID-19.
- A requirement for a negative PCR test before entering a country is recorded under 1- screening, as all passengers could circumvent the requirement to undergo a two week quarantine by testing negative.
- C8 refers to incoming international travellers. Bans on people travelling internationally due to stay at home requirements are not recorded here.
- If land borders are closed, but international flights are permitted, then still we record C8 based on whether there is a total ban on entry from some countries, and if not, based on screening or quarantine requirements. If residents of the closed border countries could still get on a flight, then this does not constitute a full ban. If the policy would prevent *most* people from a certain country from entering, representing a ban on entry from that country, then this could be considered an edge case for recording a 3 - ban on entry from some countries.
- This indicator is to record policies relating to incoming travellers to the jurisdiction being coded, not restrictions on outbound travel.
- **Constituent countries**: For constituent countries/regions/territories where the international travel restrictions may be determined by another country/region/territory, we record the policies and rules that apply to the jurisdiction being coded, in order to reflect the de facto lived reality of citizens there. This may mean coding a C8 that is set by another government if they control the international travel of a constituent country. If the jurisdiction being coded has a more stringent C8 policy imposed by another country/region/territory, we code the most stringent policy in place. For example- Puerto Rico’s international travel restrictions are set by the government or PRI, and the US federal government, meaning C8 can be seen as both a national and subnational unit. We code the most stringent C8 policy applying to PRI, even if this is from another country/region/territory (in this case, the USA). Constituent  countries/regions/territories to consider this for C8 are: Aruba, American Samoa, Bermuda, Greenland, Guam, New Caledonia, Puerto Rico, French Polynesia, and the United States Virgin Islands.


### E1- Income Support

-  This indicator does not have a binary flag variable to reflect geographic variation in policies. Therefore, we generally record the level of policy that applies everywhere across the jurisdiction - the highest common value of policy nationwide or statewide. We do not report any policies of a higher value that are only available in limited areas.  *For example*  if income support is only being provided by some cities, and not across the whole country/territory or state, we would not report it. It is only recorded when the support recorded applies nationally or statewide.
- Formal sector workers are people who are employed with contracts, and pay taxes. Informal workers may be roadside vendors, work on markets, and do not have a formal contract for their work. 
- If benefits in kind are being given (e.g. dry rations, or school meals), this is recorded as a 0 with a note. It is not recorded as a non-zero value as it is not money being given or salaries replaced.
-  Financial support given to private sector employers to ensure that people returning to a country or state are still paid while completing the mandatory 14 day self-isolation requirement, is too niche to credit the entire state/country/province for. It is only recorded if ALL the employees in the formal sector who cannot work are being covered. 
-  A one time grant, for example just for those working in state institutions is recorded as a note, but is not universal enough in scope to record in E1. 
- Edge cases and marginal examples
    - *Widening eligibility for unemployment benefit:* For example, if a nation or state had worked within the existing unemployment scheme to offer expanded eligibility during the COVID-affected period, for example giving benefits to those who wouldn’t normally be paid leave. This expands unemployment benefits to a wider group , and would therefore be recorded as the appropriate non-zero value depending on the value/coverage.
    - *Expedited access to unemployment benefit:* If a state takes policy action to make it faster and easier to access nation or  state/federal unemployment benefits during the COVID-affected period, but doesn’t expand eligibility criteria, this is only recorded as a note. The underlying policy hasn’t changed or expanded to reach more people.

### E2- Debt/contract relief for households
- This indicator does not have a binary flag variable to reflect geographic variation in policies. Therefore, we generally record the level of policy that applies everywhere across the jurisdiction - the highest common value of policy nationwide or statewide. Any policies of a higher value that are only available in limited areas are not recorded.  *For example*  if debt relief is only being provided by some cities, and not across the whole country/territory or state, we would not report it. It is only recorded when the support recorded applies nationally or statewide.
- Debt relief for business and corporations is not recorded here, as E2 only records debt relief to private households.

### E3- Fiscal Measures

- If the specific monetary value is undisclosed or unclear, we make a note recording the announcement, but don’t record the monetary value. 
Sometimes governments make ambiguous funding announcements (where it is not clear what the money is for), or they announce multiple programmes under a single number (eg, fiscal stimulus, plus hospital funding, plus vaccine investment, plus support for other countries, in one number). In these cases, the spending is recorded in this E3 category, and not in the other monetary categories (E4, H4, and H5).
- If the state is providing support to specific groups, for example funding children’s school meals, handing out staple goods, or providing grants to single parents, this is recorded under E3.
- If specific numbers of spending announced are available, but not a specific date on which this policy was brought into effect, we record the numbers and the exchange rate when it is mentioned, and note that this may not have been the exact day that spending began.


### E4- Providing Support to other countries

- We only record money here that a country/territory/subnational unit DONATES to another country/territory/subnational unit, not that is received. We do not record in-kind support, for example donations of medical equipment, as a monetary equivalent; but we would still record a note of the in-kind support.
- We record donations to international organisations, such as  WHO, WFP, as long as the country being recorded is the donor and it is to a specific relief fund specifically related to COVID. Donations to a generic WHO fund which might not be used specifically for COVID related issues is not specific enough to record.

### H1- Public Information Campaigns

- Evidence for the beginning of a coordinated campaign includes a website being launched, an official announcement or press release of a campaign, or government and health department social media announcements of a campaign. 
- There have been very few cases where we record the end of a public information campaign. These are rarely announced officially, but evidence for the end of a campaign can be seen through a very out of date web page and a lack of any COVID-related communications, policies, or announcements from the government. The context of the broader policy environment should corroborate the idea that the government has stopped communicating about COVID-19 to citizens. A detailed note with evidence will be included to explain this.

### H2 - Testing Policy

- While government policies are recorded, capacity issues affect implementation. This therefore requires judgment, about how aspirational a policy is versus how practical it is to see if it is able to meet its propositions. We will sometimes record a lower code than the official announced policy, but will provide sources that demonstrate that there is not capacity on the ground to meet this testing policy.
- This indicator does not have a binary flag variable to reflect geographic variation in policies. Therefore,  the level of policy that applies everywhere across the jurisdiction is recorded - the highest common value of policy nationwide or statewide. We do not record any policies of a higher value that are only available in limited areas. *For example* if there is not testing available to anyone symptomatic across the whole country/territory or state, but only in certain areas, this would not be reported as a 2 as this does not apply generally. Therefore the highest common value nationwide or statewide is a 1, and this is what we record. 
- In some countries, most testing is coordinated by private companies, with little oversight or coordination from the government (eg in the USA). In this cases, we report as follows:
    - When the state/nation is clearly putting resources towards making testing available, we record this as a 1 (only symptomatic and eligible)
    - If the government implements a statewide/nationwide plan to fund and procure local testing facilities, with the intention of widespread public accessibility, we report a - 2 (all symptomatic eligible)
- We do not record testing policy as generally available (3) unless it is country/territory wide and there is also evidence of capacity to meet this. If countries are reporting severe shortage of tests, we assume the low capacity is rationed/prioritised for symptomatic people or high-risk people (and therefore not generally available). 
- The main purpose for H2 is to record PCR testing (tests that detect people with a current active infection). Antibody tests (for people who have been infected in the past) are not usually reported under H2. The only rare case where we would report other types of tests was where, say, widespread antibody testing was used to identify individuals for follow-up PCR tests. As this served the same function as a PCR test, and advanced the goal of determining current infection. These exceptions will be explained in a note.
- *Some examples that could indicate a 1:*
    - Declaring COVID testing capacity before first case
    - Announcing the first identified case in a country/territory and that testing is available for that first case and others (if needed)
    - A policy announced to begin scaling up testing capacity (if the above have not already occurred)
    - Announcing partnerships with private pharmacies/other partnerships (if the above have not already occurred)
- *Some examples that could indicate a 2:*
    - Announcement of a broader plan that includes funding and mobilizing resources to support local testing
    - Testing announced as available for all symptomatic people or all people in suspicion of being in contact with a case
- *Some examples that could indicate a 3*:
    - Widespread testing capacity reported for whoever wants it (ie not just in one big city) and good evidence that there is capacity on the ground to meet this
    - Announcing that anyone interested in getting a test will receive one
-  Widespread lateral flow testing (LFT) can result in a 3 code for H2 only if follow up PCR tests are available for everyone who could test positive. If lateral flow tests are available, but there is no further connection to PCR testing for positive tests, this would not be coded. In this instance we would not consider LFT and only record the state of PCR testing in the country/region/territory. Some examples of LFT and PCR interactions are below:
- *Some examples that could indicate a 0:*
    - No testing policy in place
    - Lateral Flow Tests available but no PCR tests available at all
- *Some examples that could indicate a 1:*
    - Lateral flow tests backed up by PCR tests only available to those who have symptoms and meet specific criteria
- *Some examples that could indicate a 2:*
    - Lateral flow tests backed up by PCR tests, but LFTs are available only to those showing symptoms
- *Some examples that could indicate a 3:*
    - Widespread lateral flow testing available to everyone (including asymptomatic people), and all positive LFTs will be followed up by a PCR test


### H3 - Contact tracing

- We are only interested in manual contact tracing that is intended to reach all people known to an newly-diagnosed case. Contact tracing apps do not achieve this goal, and the presence of a contact tracing app in a country/territory would not be recorded here under H3 (although it may be recorded in a note). The difference between the levels here is considering whether this top-notch manual contact tracing is done for some COVID-19 cases (1) or for all cases (2).
- *Some examples that could indicate a 1*:
    - Declaring that a country/territory has COVID-19 contact tracing capacity before its first case
    - Reporting first case and saying that the government is tracing contacts of that first case (if the above hasn’t occurred)
    - A policy to resource and recruit contact tracing capacity
    - Announcement of first case is insufficient to assume contact tracing.
- *Some examples that could indicate a 2*:
    - Declaring increased resources to contact tracing capacity and the intention to do contact tracing for all identified cases, PLUS evidence that this is actually happening on the ground and there is capacity to do so.
    - We will sometimes downgrade a country/territory from a 2 to a 1 if there is evidence that their contact tracing resources have been overwhelmed. In this cases the official policy of the country/territory is often still to say that they conduct ‘comprehensive’ contact tracing. But if there are very high daily case numbers, and credible reports of newly-diagnosed cases whose recent contacts were not traced, we will not report this as a 2.
    
 ### H5 - Investment in vaccines
- This indicator record spending on vaccines procurement as well as vaccine development spending- therefore covering all vaccine related spending
    
 ### H4 - Emergency investment in healthcare
 - If specific numbers of spending announced are available, but not a specific date on which this policy was brought into effect, we record the numbers and the exchange rate when mentioned, and explain in the note that this may not have been the exact day that spending began.

 ### H6 - Facial coverings
 - The difference between the 3 and the 4 levels here is that at 4, a mask is required at all times when leaving the house with no exception. Even if people are in a street and more than the recommended social distance from other people, a mask is still required. 
- *Some examples that could indicate a 2*
     -  In England it is compulsory to wear masks in shops and some other specific locations (not all)
- *Some examples that could indicate a 3*
     - In New York it is compulsory to wear a mask on crowded street/ shared space, but not empty street, and at all times in an indoor setting where they at not at home, even if social distancing possible
- *Some examples that could indicate a 4*
     - In Spain it is compulsory to wear a mask outside at all times
     
 ### H7 Vaccination policy
- Geographic coverage needs to be national before this is coded, as we code the lowest common value if there is geographic variation
- These three criteria regarding availability MUST be met to code a non-zero value
 - 1. There is a de jure policy to vaccinate a population group
 - 2. There are enough vaccine doses on order and reasonably expected to be delivered, in order to vaccinate 20% of the target population 
 - 3. There is de facto capacity and evidence that this is being met on the ground. For example, vaccines are actually being administered.
- Elderly groups are as they are defined locally for the specific country/territory being coded
- Key workers are broadly defined according to local conditions, and may also be described as essential, frontline, and high risk employees.
- Broad groups may include a large group of adults (eg. all those aged over 40), or other broadly defined population groups (eg. students)
- A policy recorded as “no cost to individual” may also include a very small nominal cost to the individual, such as the small pharmaceutical co-payments (eg. $5) in some public health systems
- Vaccines are defined as having passed Phase 3 clinical trials and approved by the government for use in that country, region, or territory. The brands of vaccine being administered are recorded in the notes.
- The ‘clinically vulnerable groups’ category does not record the elderly as they are recorded in the ‘elderly’ category.
- Vaccinations for residents of Long Term Care Facilities (LTCFs) are coded under the ‘Elderly’ category as the majority of people living in such homes are elderly residents.
- When there is a vaccine shortage and there are not enough doses to vaccinate the target population, we reduce the value to reflect this reduction, based on the three criteria listed above
- We code a 5 (Universal Coverage) when the vaccine is available to everyone 16+ or 18+ (the lowest age permitted by the vaccine brand currently), and there is evidence that this is taking place on the ground. 

 ### H8 Protection of elderly people
 - This indicator focuses mainly on institutions where elderly people live, but also has scope to record restrictions that form the equivalent level of protection in settings where elderly people are cared for in the home or community, especially in countries, regions, and territories where institutions are not used.
 - Elderly people are defined here relative to the country, region, or territory being coded, for example the local retirement age, and no absolute chronologic age is defined.
 - Long Term Care Facilities (LTCF) here are used only to refer to institutions for elderly people. Policies for other vulnerable groups are not recorded here- this indicator does not cover vulnerable populations other than specifically elderly people, and does not cover prison populations .
 - The provision of guidance and specific information campaign material for LTCFs for elderly people is coded as a 1. Public officials urging caution regarding the protection of elderly  people can also be coded here, for example on social media platforms- in the same way as the H1 indicator.
 - If the C6 indicator is 2 or a 3, this can count as a 2 or a 3 for H8, because as the elderly are a subset of the general population, orders for all to stay at home therefore require elderly people to stay at home.
 - If there are both policies recommending or requiring elderly people to stay at home, and also policies in place regarding Long Term Care Facilities , the most stringent policy is coded. While the priority is to record policies in LTCFs, if these are not in place, policies regarding stay at home requirements specifically for elderly people are equally valid. 
 - If masks are required to be worn generally in the country/region/territory, including in elderly care homes, this does not warrant a 1 coding for H8. 
- *Some examples that could indicate a 1:*
  - In Santa Catarina, Brazil (SC), the state government issued a Decree recommending elderly people to stay home and only go outside for necessary activities
  - Sanitation, hygiene, and distancing recommendations are made for elderly care homes
  - Encouragement from a state agency to restrict visitors.
- *Some examples that could indicate a 2:*
   - In New Zealand, staff and visitors were “to stay away from aged care facilities” if they felt ill, and to be symptom free from any flu and cold for 48 hours before visiting
   - Restrictions on movements within nursing facility visits or when visiting nursing facilities, such as requiring outdoor visits only.
   - Requiring screening for fever/COVID-19 symptoms before entrance to a nursing facility or testing requirements when visiting a facility.
   - Substantial limits to visitor volume (ex: to a single family member).
   - Substantial sanitation or health precautions such as frequent testing of staff and visitors, decreased capacity of rooms or facility space, significantly altered care schedules, or significant PPE requirements. Increased cleaning or mask wearing alone would not qualify.
   - A general stay at home order
- *Some examples that could indicate a 3*:
    - Under its Emergency Powers Act, the Finnish government used its emergency powers to ban visitors from care institutions, health care units and hospitals, with some family exceptions on a case-by-case basis
    - Ban on visitation from all non-essential personnel. No visitors are allowed unless in exceptional circumstances such as compassionate or end of life scenario

### V1- Vaccine prioritisation

- We code this from when the official priority groups plan is published, not from when potential categories are discussed informally.

### V2- Vaccine eligibility/availability 

- We select categories in V2 when there is evidence from anywhere within a country/region/territory that this group is being vaccinated. This logic **differs** from the logic currently used to code H7, where we only code a new ordinal level when this is the situation nationally, for at least 20% of the target group. We may re-code H7 in the future in order to align these two approaches.
- If V2 eligibility/availability and therefore access to vaccines is universal, we select all general ages above 16 in V2. if the vaccine is approved for additional groups, such as `0-4 yrs infants` this can then be added when the policy comes into effect.
- If vaccination centres are offering vaccinations to people who walk in, if there is excess capacity, and there is evidence of this being a widespread policy occurring in multiple locations in a consistent manner, we code this under V2 using the relevant age category. If this is open to anyone, we code this as all of the 16+ general age categories. If this is only available to a specific group, we code that group. If this is very sparse and ad-hoc, with only evidence for example from one centre only, we do not code this, but add detail in the note.

### V3- Vaccine financial support

- If people receive the vaccine from their private healthcare insurance-run organisations (e.g. Israel’s HMO members) we code this depending on whether the government is still fully funding the vaccine, or requires copayment from the insurer (therefore not fully government funded). 
- If full government funding is available for a certain group, we code this as the default. We only code other options if they are the only ones available to individuals of that group.

### V1 and V2- Category specific guidance 

- Primary and secondary students, Tertiary education students- If a country specifies that students will be targeted, and **not** `5-15 yrs young people`, we only record the `Primary and secondary school students` or `Tertiary education students` categories
    - If all young people in an age group are prioritised, we would report the age group (eg. `0-4 yrs infants`, `5-15 yrs young people`) and would not record anything for the students categories. We only include the students categories if they are specifically prioritised separately- not inferring one from the other
- Frontline workers- We **only** record `Frontline/essential workers (when subcategories not specified)` if there has been a vague/ambiguous reference to frontline or essential workers without specifying discrete groups. If specific groups (e.g. `Police`) _are_ listed, we select the best fitting category for them based on the ‘Best fit’ table, and include in the notes section which groups specifically were targeted. 
- Other high contact professions- if this category is used we include in the notes section which groups specifically were targeted under this category- for example taxi drivers or public transport operators. 
- Clinically vulnerable and At risk- `Clinically vulnerable/chronic illness/significant underlying health condition (excluding elderly and disabled)` represents people who live with illnesses and conditions which place them on the prioritisation list. These may include those who have had an organ transplant, people undergoing chemotherapy, or have a severe lung condition, for example. Where these cases and examples are clearly defined and evidence shows that some of these groups are being vaccinated -  we select the `Clinically Vulnerable/chronic illness/significant underlying health condition` category, even if the eligible conditions are different from the examples given above.  The age-related `At risk` categories are used for groups that are not extremely vulnerable, but still have comorbidities and underlying health conditions that make them eligible for vaccination sooner. 
- We report the age ranges which are mentioned in the plan. If the lowest age that can receive a vaccine (age floor) is mentioned, we record all ages above this which are part of this (e.g. if all over 70s are eligible, we report `General 70-74`, `General 75-79`, and `General 80+`). If specific age ranges are mentioned, we only select these- e.g. `General 25-29` and `General 40-44`
- If the vaccine is only available to people `at risk` in a certain age group, but then becomes generally available to all people in that age group, we stop recording the `At risk` variable and start recording the `General` variable. E.g. If `General 60+` is recorded we do not record `At risk 60+` as it is a subset of the ‘general’ population. However if the V3 funding arrangements are different for `At risk` people compared to the `General` population, then we will still report both separately at V2. 
- Missing categories- If there is a missing category (that is, a country specifies a priority group that does not obviously fit into our list of groups), our data collectors have two options:
  - *Option A*: Best Fit - Use the ‘Best fit’ table below to decide which category to use as a proxy for this to ensure standardization. We will also record this in detail in the notes.
  - *Option B*: Do not record - If the group is not on the list in the portal, and there is not a suitable best fit, we exclude it from V1/V2  but ensure the note contains the true list

### Vaccination best fit table for categories
 
Here we record where categories have been substituted when category not listed in V1/2 for standardization of ‘best fit’ 

| OxCGRT Category  | Examples of country-designated categories that have resulted in this box being ticked  | 
| --- | --- | 
| `Police/ first responders` | Occupations important to functioning of society (IRL) <br/> Groups of persons who are of critical importance to the functioning of Singapore (SGP) <br/> Ambulance and paramedic staff (AUS) <br/> Emergency health  staff (FIN) <br/> Firefighters (FRA) <br/> Fire (AUS)
| `Disabled people`  | People with a learning or neurological disability (GBR) <br/> People with Down’s Syndrome (PRT) <br/>  People in communal facilities with an increased risk of infection and outbreaks (for example homes for the handicapped) (CHE)
| `Border staff`  | Key workers in essential jobs who cannot avoid high risk of exposure (IRL) <br/> Maritime and aviation (SGP)
| `Frontline retail workers`   | Restaurant workers 
| `Frontline workers (when not otherwise specified)`  | Other people aged 65-69 and key workers essential to the vaccine programme’ (IRL)  <br/> Workers identified as performing a critical function in society [unspecified] (DNK) <br/> Operators essential essential for the country's economic activities (FRA) <br/> Essential professions In this phase, people with essential social and/or economic profession are vaccinated (BEL) 
| `Tertiary education students`   | University, college, or technical trade schools 
| `Educators`  | University, college, or technical trade schools  <br/> Teachers in any level of school <br/> Instructors/professors in colleges and universities
| `Other high contact professions`   | Disability care staff (AUS)
| `Ethnic minorities`  | Aboriginal and Torres Strait Islander people > 55 (AUS) <br/> Indigenous populations (CAN)
| `Factory staff`   | Meat processing staff (AUS)
| `Crowded/communal living conditions (dormitories for migrant workers, temporary accommodations)`  | People in communal facilities with an increased risk of infection and outbreaks (with residents of mixed ages)  <br/> Migrant dormitories/crowded accommodation (SGP) <br/> People living or working in crowded settings (IRL)  <br/> Prison populations (ISR)  <br/> People who live in socially vulnerable situations, such as the homeless or the undocumented. (SWE) <br/>Homeless (KOR)  <br/> Vulnerable and precarious people (homeless…), living in communities (prisons, psychiatric establishments, homes) (FRA)  <br/> People in communal facilities with an increased risk of infection and outbreaks (with residents of mixed ages) (CHE) 

## General Interpretation Guidance 
 
There are a few general rules our coders follow while collecting data:
 
- **Implementation not announcement:** We start coding a policy from the day the policy was implemented in practice, not the day it was announced.
- **We report the most stringent government policy** with the highest ordinal value. If the most stringent policy is only present in a limited geographic area or sector, we use a binary flag variable to describe this scope and reflect whether the policy is targeted or general the binary flag model is described in detail here in the [codebook](codebook.md)
- **Notes and Web Archived links:** For every change we make in the database, we add a note, with a website link to where the information was found. In order to save the webpage that we gained the information from, we webarchive the link. This saves the page on the date that it was accessed to prevent it being lost. These may look like this http://web.archive.org/web/20200517163106/https://covid19.govt.nz/, or http://archive.vn/XifX8. 
 - The index methodology can be found [here](index_methodology.md)  detailing how the different indices are calculated
 - **If there are stricter restrictions on a weekend**, we record these stricter policies for just the Saturday and Sunday dates, and the less stringent ones on weekdays, so each data point accurately reflects the situation in that country on that given day
 - **If coding a country with a contested government or multiple ruling parties**, we follow the guidance to code the dominant tendency, and record the policies of the more formalised government, or the one which governs the larger proportion of the population
 - **We do not code non-COVID policies for other indicators besides the guidance for C8**, such as those resulting from civil war or natural disasters.
 - **Where vaccination and testing exemptions are in place we report the most stringent policy**. Exemptions may include less stringent restrictions for people who have evidence of COVID-19 vaccination, a negative PCR test, or of immunity). Therefore the coding reflects the more stringent government policies applied to people who do not have an exemption (ie. usually a required closure or behaviour). The only time we would report the lower policy is if anyone can arrive and get tested onsite with a rapid test to gain entry. We would not code this as a required closure, as anyone can ‘test out’ of restrictions easily. Such at-the-door testing must apply to all sectors within the indicator, and be a government policy, not that of a private business. 

 ## Interpretation guide changelog
- 8 July 2021: V1.10 added guidance for vaccination/exemptions coding, added Vaccination policy interpretation guidance, edits to C1 for school holidays
- 14 June 2021: V1.9 replaced 'federal government' with 'national government' in C8 detail about subnational data, and added guidance on LFT to H2
- 24 May 2021: V1.8 added in new guidance for non-COVID policies to General
- 5 May 2021: V1.7 added in new guidance for C8, C4, H7, H8, and General 
- 15 March 2021: V1.6 added H8 guidance
- 04 March 2021: V1.5 added in new guidance for C1, C2, C3, H7
- 14 January 2021: V1.4 replaced 'country' with 'country/territory', and additions to C7, C8, E1, E2, E4, H5, and General Interpretation Guidance
- 17 December 2020: V1.3 added in detail regarding availability for H7
- 09 December 2020: V1.2 added in new guidance for H7
- 04 November 2020: v1.1 added in new guidance for C1, C3, C8, E1, E3, H2, added E2,H4 and H6 sections
- 01 October 2020: v1.0 created the interpretation guide
