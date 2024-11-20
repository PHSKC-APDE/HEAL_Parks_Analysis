# HEAL Parks: 2024 Playground Analysis
Ronald W. Buie

# Front Matter

This document outlines procedures, technical considerations, and
analytic results for a 2024 analysis of playgrounds within parks
participating in the HEAL Park Analysis for Park Equity Study. The
primary purpose of this PDF is technical review by analysts and project
managers to confirm the process and data quality.

For general information about the project please review the [GitHub -
PHSKC-APDE/HEAL Parks
Analysis](https://github.com/PHSKC-APDE/HEAL_Parks_Analysis) or contact
Seth Schromen-Wawrin.

## Goal

Identify differences in park use and share findings with parks agencies
to inform their planning and investments.

## Objective

Test the ability of park use observation data to compare utilization
between parks. Use the results from this analysis to inform the
understanding of facility access and quality. This pilot will focus on
comparing use of playground features.

## Partners

Public Health – Seattle & King County

King County Parks

Tukwila Parks and Recreation

Burien Parks, Recreation, and Cultural Services

King County Play Equity Coalition

## Geography

The contiguous area of Burien, North Highline, Skyway, Tukwila, and
White Center

# Background

The Healthy Eating Active Living (HEAL) program aims to identify the
availability and impact of parks on King County residents. This effort
includes an annual study measuring who is using the parks, when they are
using them, and what they are doing. In 2024, parks’ managers identified
playground use as an area of possible interest to focus data analysis.
The below analysis has been conducted in response to research questions
proposed by the parks’ managers. These exploratory analyses are intended
to inform further discussion of how we may pursue research and reporting
of playground use that supports parks’ and the county’s interest in the
public health and our broader equity and social justice goals.

## Research questions

The below research questions were proposed by the parks’ managers in
collaboration with the HEAL team.

- How does the observed use of playgrounds differ between parks located
  in opportunity areas and parks not located in opportunity areas?
- How does the observed use of playgrounds differ between parks of
  similar park categories?
- How does the observed use of playgrounds differ between playgrounds
  with different complexities of playgrounds?
- How does the observed use of playgrounds compare to the age of the
  playground?
- How does the observed use of playgrounds differ when a park includes
  certain features?
- How does the age of observed playground users differ between park
  groups (size, feature qualities, etc.)?
- How accessible is the park by transportation?

# Analytical Methods

## Major inputs

The following inputs to this script are contained at ./inputs/*.* and
include

- A file of park meta data, including address, zip, city, neighborhood,
  official name, and REDCap name for each park
- A file of collected SOPARC observations, aggregated to the period
  level, currently updated for 2022-2024
- An accompanying file of SOPARC activities, currently updated for
  2022-2024

In addition, access to Public Health – Seattle & King County’s
Assessment Policy Development and Evaluation (APDE) Division’s
population estimates, or calculated population estimates for children
living within 1/2 mile for all parks included in the analysis.

## Output categories

- documentation - this documentation and analysis results as document
  files
- tables - tabular outputs of analysis, generally in xlsx format
- charts - chart outputs of analysis, generally in pdf and/or png format

## Setup & environment

This script was last executed using R version 4.4.1 (2024-06-14 ucrt).

# Data Preparation

This analysis relies on the below data sources. Please contact Ronald W.
Buie (rbuie@kingcounty.gov) or Seth Schromen-Wawrin
(seth.schromen-wawrin@kingcounty.gov)for details.

- 2022-2024 park observation data (conducted by PHSKC)
- Park features, category, and age data (provided by Burien, Tukwila,
  and KC Parks)
- Play Elements (assessed by PHSKC)
- Opportunity areas (assess by KC Parks)
- Walkscore/Transitscore of park (from walkscore.com)
- Census data on population surrounding park (from Census data
  calculated by PHSKC)

## Variable definitions

- “Park Category”: category of park”s intended reach, set by Parks
  Department
  - “Mini Park” = park intended to draw from immediate neighbors
  - “Community Park” = park intended to draw from more local area,
    includes schools
  - “Regional Park” = park intended to draw from the entire city or
    region
- “Opportunity Areas”: indicator of field for if park is located in an
  Opportunity Area for health and economics, per King County Parks
  analysis.
- “Restroom”: indicator of if park has restroom facility (permanent or
  temporary)
- “Picnic Area”: indicator of if park has area with tables and benches
- “Sport Fields”: indicator of if park has area designated for organized
  team sports (all conditions).
- “Play Elements”: number of unique opportunities in playground for a
  type movement/activity. Movement/activities include: climbing,
  sliding, spinning, crawling, swinging, balancing, playing with sand,
  and water play (e.g., splash pads).
- “Playground Age”: Year that the playground was installed or last
  significantly updated.
- “Primary Age Group”: Category of “2-5 years old” or “5-12 years old”.
  Swing features included in 5-12; a playground is not fit 2-5 if it
  only has toddler bucket swings. Can be both categories.
- “Average Playground Use”: Average number of observed users across all
  observation days.
- “Peak Playground Use”: Most number of observed users found during a
  single observation day.
- “Median Playground Use”: The median daily number of users of a
  playground.
- “Playground Popularity”: Proportion of park users observed in
  playground.
- “Park Catchment”: Population within ½ mile of park.
- “Youth Park Catchment”: Population less than 15 years of age within ½
  mile of park.
- “Park Name”: for this study we used abbreviated names with an appended
  jurisdiction acronym. Jurisdictions include:
  - “T” = Managed by Tukwila Parks and Recreation
  - “B” = Managed by City of Burien – Parks, Recreation, and Cultural
    Services Department \* “KCHA” = Managed by King County Housing
    Authority
  - “KC” = Managed by King County Department of Natural Resources and
    Parks
  - “HSD” = Managed by Highline Public Schools

Currently unused variables include:

- “Play Structures”: number of unique play structures that are
  physically separated and designed for use by more than one person at a
  time.
- “Water” = indicates if target area includes water play area /
  splashpad.
- “Inclusive” = Indicates if design goes beyond ADA compliance for
  different physical, sensory, social, and intellectual abilities to
  play together

### park catchment

Some analyses require park catchment information. We use the population
within .5 miles of a central coordinate for the park. All ages
population is provided in the data set generated by our annual analysis.
For this playground study we also calculate the population of 0-14 year
olds within 0.5 miles of each park.

# Analyses

The below analyses are exploratory and descriptive statistics to support
investigation into data and reporting systems that support the equitable
use and maintenance of municipal parks across King County. In providing
these results we hope to facilitate discussion around this work and how
to proceed going forward.

Some important questions these results are meant to solicit or
facilitate are:

- Do the results appear reasonable, or do the numbers for some parks
  appear unlikely to be accurate?
- Do the proposed questions seem valuable to ask?
- For a given analysis, is it well defined and are the data accurate?
- For a given analysis, is this a helpful way to present the results?
- Do any results suggest that we should investigate further, if
  possible?
- Do any results suggest that we should not investigate further?

Notes:

- Multiple park characteristics in the supplemental information file
  have n/a or tbd status. Depending on the analysis, these may be
  suppressed, or show up as NA, tbd, or 0



## Analyses of park catchment and status

These analyses explore the relationship between category, funding
status, and the surrounding population (catchment) of a park. Park
catchment may, additionally, provide context for later analyses below.



### chart of park catchment

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-3-1.png)



### chart of 0-14 park catchment

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-4-1.png)



### chart of park catchment by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-5-1.png)



### chart of 0-14 park catchment by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-6-1.png)



### chart of park catchment by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-7-1.png)

Notes:

The following parks were excluded for not having category status:



### chart of 0-14 park catchment by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-8-1.png)

Notes:

The following parks were excluded for not having category status:



## Analyses of playground structure and classifications



### chart of playground equipment age by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-9-1.png)

Notes:

The following parks were excluded for not having a playground
installation date: Beverly Park El Sch (HSD), Cedarhurst El Sch (HSD),
GB: N Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave Playground
(KCHA), GB: W Playground (KCHA), Gregory Heights El Sch (HSD), Hazel
Valley El Sch (HSD), Mount View El Sch (HSD), Roxhill Park (SPR), Seola
Gardens: N Playground (KCHA), Seola Gardens: Park (KCHA), Seola Gardens:
S Playground (KCHA), Shorewood El Sch (HSD)



## Analyses of playground use

The below analyses explore relationships of the number of people
observed in playgrounds and other characteristics or status of the park.
We refer to this number of observed users as “use”. For several of these
analyses, use is provided in three forms, the average number of users
observed across all observed days, the median number of users across all
days, and the peak number of users across all days.

Notes:

- Analyses of “average playground use” aggregate all playground target
  areas within the park (effectively calculated as one large playground)



### playground use by opportunity area status



#### chart of average playground use by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-10-1.png)



#### chart of median playground use by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-11-1.png)



#### chart of peak playground use by opportunity area status

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-12-1.png)



### playground use by park category



#### chart of average playground use by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-13-1.png)

Notes:

The following parks were excluded for not having category status:



#### chart of median playground use by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-14-1.png)

Notes:

The following parks were excluded for not having category status:



#### chart of peak playground use by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-15-1.png)

Notes:

The following parks were excluded for not having category status:



### playground use by number of play elements



#### chart of average playground use by number of play elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-16-1.png)



#### chart of median playground use by number of playground elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-19-1.png)



#### chart of peak playground use by number of playground elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-20-1.png)



### playground use by playground equipment age



#### chart of average playground use by playground equipment age

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-21-1.png)

Notes:

The following parks were excluded for not having playground equipment
age: Beverly Park El Sch (HSD), Cedarhurst El Sch (HSD), GB: N
Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave Playground (KCHA),
GB: W Playground (KCHA), Gregory Heights El Sch (HSD), Hazel Valley El
Sch (HSD), Mount View El Sch (HSD), Roxhill Park (SPR), Seola Gardens: N
Playground (KCHA), Seola Gardens: Park (KCHA), Seola Gardens: S
Playground (KCHA), Shorewood El Sch (HSD)



#### chart of median playground use by playground equipment age

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-22-1.png)

Notes:

The following parks were excluded for not having playground equipment
age: Beverly Park El Sch (HSD), Cedarhurst El Sch (HSD), GB: N
Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave Playground (KCHA),
GB: W Playground (KCHA), Gregory Heights El Sch (HSD), Hazel Valley El
Sch (HSD), Mount View El Sch (HSD), Roxhill Park (SPR), Seola Gardens: N
Playground (KCHA), Seola Gardens: Park (KCHA), Seola Gardens: S
Playground (KCHA), Shorewood El Sch (HSD)



#### chart of peak playground use by playground equipment age

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-23-1.png)

Notes:

The following parks were excluded for not having playground equipment
age: Beverly Park El Sch (HSD), Cedarhurst El Sch (HSD), GB: N
Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave Playground (KCHA),
GB: W Playground (KCHA), Gregory Heights El Sch (HSD), Hazel Valley El
Sch (HSD), Mount View El Sch (HSD), Roxhill Park (SPR), Seola Gardens: N
Playground (KCHA), Seola Gardens: Park (KCHA), Seola Gardens: S
Playground (KCHA), Shorewood El Sch (HSD)



### playground use by restroom status and park category



#### chart of average playground use by restroom status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-24-1.png)

Notes:

The following parks were excluded for not having category status:



#### chart of median playground use by restroom status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-25-1.png)

Notes:

The following parks were excluded for not having category status:



### playground use by picnic area status and park category



#### chart of average playground use by picnic area status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-26-1.png)

Notes:

The following parks were excluded for not having category status:



#### chart of median playground use by picnic area status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-27-1.png)

Notes:

The following parks were excluded for not having category status:



### playground use by sports field status and park category



#### chart of average playground use by sports field status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-28-1.png)

Notes:

The following parks were excluded for not having category status:



#### chart of median playground use by sports field status and by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-29-1.png)

Notes:

The following parks were excluded for not having category status:



### play use by number of play elements and primary age groups

Primary age group is a status provided by parks managers that designates
the age groups that the playground is intended to be used by. The two
age groups are 5-12 and 2-5. A playground may be designed to serve both.



#### chart of average playground use by number of play elements and by primary age group, population as color

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-30-1.png)

Notes:

The following parks were excluded for not having element status:



#### chart of median playground use by number of play elements and by primary age group

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-33-1.png)

Notes:

The following parks were excluded for not having element status:



#### chart of peak playground use by number of playground elements and by primary age group

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-34-1.png)

Notes:

The following parks were excluded for not having element status:



### playground use by walkscore



#### chart of average playground use by walkscore of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-35-1.png)



#### chart of median playground use by walkscore of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-37-1.png)



### playground use by transit score



#### chart of average playground use by transit score of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-38-1.png)

Notes:

The following parks were excluded for not having a transit score:
Beverly Park El Sch (HSD), Dick Thurnau Park (KC), Five Mile Lake Park
(KC), GB: N Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave
Playground (KCHA), GB: W Playground (KCHA), Lake Geneva Park (KC), Maple
Valley Heights Park (KC), Maplewood Park (KC), North Shorewood Park
(KC), Seola Gardens: N Playground (KCHA), Seola Gardens: Park (KCHA),
Seola Gardens: S Playground (KCHA), Skyway Park (KC), S County
Ballfields (KC)



#### chart of median playground use by transit score of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-39-1.png)

Notes:

The following parks were excluded for not having a transit score:
Beverly Park El Sch (HSD), Dick Thurnau Park (KC), Five Mile Lake Park
(KC), GB: N Playground (KCHA), GB: W4 Playground (KCHA), GB: Wave
Playground (KCHA), GB: W Playground (KCHA), Lake Geneva Park (KC), Maple
Valley Heights Park (KC), Maplewood Park (KC), North Shorewood Park
(KC), Seola Gardens: N Playground (KCHA), Seola Gardens: Park (KCHA),
Seola Gardens: S Playground (KCHA), Skyway Park (KC), S County
Ballfields (KC)



## Analyses of playground popularity

These analyses explore the relationship between popularity of a park’s
playground relative to other characteristics of the park. Playground
popularity is defined as the proportion of users who are observed in the
playground versus all users. For example, if 20 users were observed in
the park, and 10 of those were in the playground, the playground
popularity would be 50%. Popularity is based on the total users observed
across all days, rather than a daily average.



### chart of playground popularity by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-40-1.png)

Notes:

The following parks were excluded for not having category status:



### chart of playground popularity by play elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-41-1.png)

Notes:

The following parks were excluded for not having category status:



### chart of playground popularity by number of play elements and by primary age group

Primary age group is a status provided by parks managers that designates
the age groups that the playground is target for. The two age groups are
5-12 and 2-5. A playground may be designed to serve both.

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-44-1.png)

Notes:

The following parks were excluded for not having element status:



### chart of playground popularity among children and teens by number of play elements and by primary age group

Here, popularity is:

$\frac{\text{num of children and teens in playground}} {\text{num of children and teens in park}}$

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-45-1.png)

Notes:

The following parks were excluded for not having element status:
