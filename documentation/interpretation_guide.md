# OxCGRT Coding Interpretation Guide
***Version 1.0 <br/>Date: 01 October, 2020***

This guide details the resolutions of frequently asked [codebook](codebook.md) interpretation queries, where indicators may be interpreted in different ways. This is in order to ensure consistency, and standardize coding across the database. Queries related specifically to subnational data are labelled as such.

Updates to this coding interpretation are recorded in the [changelog](#Interpretation-Guide-changelog) below.

## Guidance by codebook indicator

### C1 - School Closures

- School closures and university closures are captured in C1. 
- Different governments use different wording (e.g. soft-closing, recommend, strongly recommend, recommend without restricting civil liberty), so we standardize what these mean in practice. If the situation is that all schools are closed, or policies in place make it impossible for them to open and meet these requirements, then that would count as a full closure. 
- Childcare, nurseries, language courses, and driving schools, do not count as educational closures. These are recorded as workplaces under C2
- If schools are closed, and this same closure policy then rolls into school holidays, we keep the code the same, for example ‘all levels of education remain closed’. This coding would only go down only once students actually return, when schools reopen
- If only children of essential workers are allowed in schools, this is reported as a closure for the general public
- If in-person teaching is suspended and all  instruction is online, this is reported as closed (physically closed).
- Some schools only open for exams, but not for classes. In this case, if schools are open for a one-off exam, for example one that is an hour long, or on one day only, this would not change the coding, so school closures would remain at a 3 if all levels are otherwise closed.If exams are running for multiple sessions, on multiple days, or even over multiple weeks, this is a similar situation to classes being open for some groups (2). Note that after the exam period ends, schools may jump back up to a 3 if all levels of education are then closed.
- If teachers are back in school to prepare for the new school year, but no students are allowed back, this would not alter the coding, as no students are present in person for education.
- If the situation is that schools are in theory allowed to open, but all schools remain closed, or policies in place make it impossible for them to open and meet these requirements, then that would count as a full closure.
- If individual school districts have the authority to decide closures/openings, we generally record policies conservatively with a ’targeted’ flag, as recording ‘general’ policies would require a high level of confidence that all schools in a jurisdiction are closed. If the state/nation is transitioning from a period of state or nationally induced total closure (3G) to giving individual districts the authority to choose, and some districts still follow the stricter policy, this would usually be represented as 3T. 
- We take account of summer school openings. If schools have been closed (3) but then some summer school is allowed, the value would change (likely 3T if some school districts remain totally closed, or a 2G if summer school has a ‘general’ countrywide scope). 

###  C2- Workplace closing

- When non-essential workplaces are meant to be closed but many people are still going to work regardless, we report the official government policy. In these cases we make a note that people may not be complying with the policy.
- If workplaces can reopen under sanitation and social distancing requirements – e.g. up to 30% of capacity, and only outdoor seats – this is a 1 (recommend closing). Restrictions are still in place, and the 1 (recommend) captures the extent of these. 
- Voluntary closures are not the same thing as closures mandated by government policy. If a workplace voluntarily closes their business or makes their staff work from home – even if that employer is the government – this does not count under C2.  
- For essential business closures, sometimes the official list of 'essential activities' is very long to the point the policy could be reasonably interpreted as a 2. In these cases, it is up to the coder’s best judgement on a case-by-case basis. Below are some examples of how we have made decisions in the past. We try to be mindful of governments who declare every business ‘essential’ or other political phrasing.
- Businesses usually considered to be essential are: Healthcare, groceries, take-out food, hardware stores, plumbers/electricians, legal services, education preparations (teachers planning courses), limited business operations support (tiny staff capacity to ensure remote working can continue).
- Some businesses that are not essential: In-person retail, personal grooming (salons, spas, barbers etc), dine-in restaurants, movie theaters, entertainment/theme parks, nightclubs.
- For phased reopening of businesses, if there are new workplaces being added to the list of places allowed to open every week, but some places remain closed, we report 2 for the period, adding notes explaining which sectors/businesses are allowed to open each week. If some sectors remain closed, the coding would remain a 2 (some sectors required to close).
- Airports and schools would not count as "some businesses" in the C2 indicator here. If these workplaces have been closed by government policy decisions, this will be captured in other indicators (eg C1 School Closures and C8 International Travel Controls). Therefore, if all businesses are open, but schools remain closed, the school closing is not considered in C2. 

### C3- Cancel Public Events

- When private gatherings of only 10 or less are permitted (e.g. C4=4), this restriction would prevent public events from taking place, so they are recorded as required to cancel.
- When all public gatherings are cancelled, but people can still go to church, we record this as a 2 (all gatherings cancelled), but make a note about the exception for religious gatherings. 
- There is no explicit cut off point for a ‘mass gathering’. If really large events, such as political protests, can go ahead, but with strict social distancing and hygiene measures in place, this could be reported as 'recommended'. 

### C4- Restrictions on gatherings 

- When there are variations in numbers for gatherings (e.g. gatherings are banned for more than 5 people with the exceptions of funerals/weddings/outdoor gatherings where it is 30 people) we report the stricter (in this case 5 people indoor) policy while including the less strict outdoor/wedding/funeral gathering limit in the notes.
- A ban on any gatherings outside of the house would be a 4, as most households are reasonably assumed to be of 10 or less people.
- If there are restrictions in gatherings based on the capacity of indoor spaces (e.g. up to 30% of the capacity), but there is no mention of any clear cut-off point, we record as 0 adding a note explaining the restriction. If the indoor place is also a workplace (eg restaurant) we would code include the note under C2 as well.
 
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
- For clinically vulnerable groups of people strongly recommended or required to shield at home, we code this as a 1 (recommended) with a ‘general’ flag (if nationwide).

### C7- Restrictions on Internal Movement

- **For subnational (state-level) data:** C7 is used to record state-level border closures where a state restricts entry from other states from another state, as well as recording restrictions on movement within the state.
- *Some examples that could indicate a 1:* 
    - Voluntary quarantines, non-intrusive checks at the state border (ex: asking where you will be quarantining but not following up extensively), asking residents of one specific city to not cross the border with a neighboring city  
- *Some examples that could indicate a 2:* 
    - Closing interstate highways/waterways, prohibiting or banning travel from certain regions, requirement of negative test result,  intensive checks on quarantine, requiring quarantine in a hotel or other standardized state-run facility
If there are restrictions for the circulation of private cars based on certain criteria (e.g. ending of the license number) to reduce the number of vehicles on the streets, we also report it as restriction of internal movement.


### C8-  International Travel Controls

- If visitors are meant to self quarantine/isolate after travelling to certain areas, but there are no enforcement or tracking measures in place, we record the official policy accordingly, and make a note that the situation on the ground may not reflect this.
- If a country is still repatriating citizens from overseas, but otherwise has closed borders, this still counts as a full border closure (4). This indicator focuses largely on requirements for foriegn passengers, in the sense that even during “total closure”, countries will still let their citizens cross the border to return home (although may subject them to quarantine).
- **For subnational (state-level) data:** As international travel is usually an issue for the federal government, subnational governments will rarely implement relevant policies for C8. The sorts of state-level activity that would be recorded under C8 include when individual airports proactively screen passengers, or if states created their own mandatory quarantines for international travelers.


### E1- Income Support

- Formal sector workers are people who are employed with contracts, and pay taxes. Informal workers may be roadside vendors, work on markets, and do not have a formal contract for their work. 
- If benefits in kind are being given (e.g. dry rations), this is recorded as a 0 with a note. It is not recorded as a non-zero value as it is not money being given or salaries replaced.
- Edge cases and marginal examples
    - *Widening eligibility for unemployment benefit:* For example, if a nation or state had worked within the existing unemployment scheme to offer expanded eligibility during the COVID-affected period, for example giving benefits to those who wouldn’t normally be paid leave. This expands unemployment benefits to a wider group , and would therefore be recorded as the appropriate non-zero value depending on the value/coverage.
    - *Expedited access to unemployment benefit:* If a state takes policy action to make it faster and easier to access nation or  state/federal unemployment benefits during the COVID-affected period, but doesn’t expand eligibility criteria, this is only recorded as a note. The underlying policy hasn’t changed or expanded to reach more people.


### E3- Fiscal Measures

- If the specific monetary value is undisclosed or unclear, we make a note recording the announcement, but don’t record the monetary value. 
Sometimes governments make ambiguous funding announcements (where it is not clear what the money is for), or they announce multiple programmes under a single number (eg, fiscal stimulus, plus hospital funding, plus vaccine investment, plus support for other countries, in one number). In these cases, the spending is recorded in this E3 category, and not in the other monetary categories (E4, H4, and H5).

### E4- Providing Support to other countries

- We only record money here that a country DONATES to another country, not that is received. We do not record in-kind support, for example donations of medical equipment, as a monetary equivalent; but we would still record a note of the in-kind support.

### H1- Public Information Campaigns

- Evidence for the beginning of a coordinated campaign includes a website being launched, an official announcement or press release of a campaign, or government and health department social media announcements of a campaign. 
- There have been very few cases where we record the end of a public information campaign. These are rarely announced officially, but evidence for the end of a campaign can be seen through a very out of date web page and a lack of any COVID-related communications, policies, or announcements from the government.. The context of the broader policy environment should corroborate the idea that the government has stopped communicating about COVID-19 to citizens. A detailed note with evidence will be included to explain this.

### H2 - Testing Policy

- In some countries, most testing is coordinated by private companies, with little oversight or coordination from the government (eg in the USA). In this cases, we report as follows:
    - When the state/nation is clearly putting resources towards making testing available, we record this as a 1 (only symptomatic and eligible)
    - If the government implements a statewide/nationwide plan to fund and procure local testing facilities, with the intention of widespread public accessibility, we report a - 2 (all symptomatic eligible)
- We do not record testing policy as generally available (3) unless it is country wide and there is also evidence of capacity to meet this. If countries are reporting severe shortage of tests, we assume the low capacity is rationed/prioritised for symptomatic people or high-risk people (and therefore not generally available). 
- The main purpose for H2 is to record PCR testing (tests that detect people with a current active infection). Antibody tests (for people who have been infected in the past) are not usually reported under H2. The only rare case where we would report other types of tests was where, say, widespread antibody testing was used to identify individuals for follow-up PCR tests. As this served the same function as a PCR test, and advanced the goal of determining current infection. These exceptions will be explained in a note.
- *Some examples that could indicate a 1:*
    - Declaring COVID testing capacity before first case
    - Announcing the first identified case in a country and that testing is available for that first case and others (if needed)
    - A policy announced to begin scaling up testing capacity (if the above have not already occurred)
    - Announcing partnerships with private pharmacies/other partnerships (if the above have not already occurred)
- *Some examples that could indicate a 2:*
    - Announcement of a broader plan that includes funding and mobilizing resources to support local testing
    - Testing announced as available for all symptomatic people or all people in suspicion of being in contact with a case
- *Some examples that could indicate a 3*:
    - Widespread testing capacity reported for whoever wants it (ie not just in one big city) and good evidence that there is capacity on the ground to meet this
    Announcing that anyone interested in getting a test will receive one


### H3 - Contact tracing

- We are only interested in manual contact tracing that is intended to reach all people known to an newly-diagnosed case. Contact tracing apps do not achieve this goal, and the presence of a contact tracing app in a country would not be recorded here under H3 (although it may be recorded in a note). The difference between the levels here is considering whether this top-notch manual contact tracing is done for some COVID-19 cases (1) or for all cases (2).
- *Some examples that could indicate a 1*:
    - Declaring that a country has COVID-19 contact tracing capacity before its first case
    - Reporting first case and saying that the government is tracing contacts of that first case (if the above hasn’t occurred)
    - A policy to resource and recruit contact tracing capacity
    - Announcement of first case is insufficient to assume contact tracing.
- *Some examples that could indicate a 2*:
    - Declaring increased resources to contact tracing capacity and the intention to do contact tracing for all identified cases, PLUS evidence that this is actually happening on the ground and there is capacity to do so.
    - We will sometimes downgrade a country from a 2 to a 1 if there is evidence that their contact tracing resources have been overwhelmed. In this cases the country’s official policy is often still to say that they conduct ‘comprehensive’ contact tracing. But if there are very high daily case numbers, and credible reports of newly-diagnosed cases whose recent contacts were not traced, we will not report this as a 2.


## General Interpretation Guidance 
 
There are a few general rules our coders follow while coding:
 
- **Implementation not announcement:** We start coding a policy from the day the policy was implemented in practice, not the day it was announced.
- **We report the most stringent government policy** with the highest ordinal value. If the most stringent policy is only present in a limited geographic area or sector, we use a binary flag variable to describe this scope and reflect whether the policy is targeted or general the binary flag model is described in detail here in the [codebook](codebook.md)
- **Notes and Web Archived links:** For every change we make in the database, we add a note, with a website link to where the information was found. In order to save the webpage that we gained the information from, we webarchive the link. This saves the page on the date that it was accessed to prevent it being lost. These may look like this http://web.archive.org/web/20200517163106/https://covid19.govt.nz/, or http://archive.vn/XifX8. 
 - The index methodology can be found [here](index_methodology.md)  detailing how the different indices are calculated
 
 
 
 ## Interpretation guide changelog
- 01 October 2020: v1.0 created the interpretation guide
