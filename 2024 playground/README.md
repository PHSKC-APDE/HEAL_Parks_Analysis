# HEAL Parks: 2024 Playground Analysis
Ronald Buie

- [<span class="toc-section-number">1</span> Front
  Matter](#front-matter)
  - [<span class="toc-section-number">1.1</span> Major
    inputs](#major-inputs)
  - [<span class="toc-section-number">1.2</span> Output
    categories](#output-categories)
  - [<span class="toc-section-number">1.3</span> This is a quarto
    generated document](#this-is-a-quarto-generated-document)
- [<span class="toc-section-number">2</span> Setup &
  Environment](#setup--environment)
- [<span class="toc-section-number">3</span> Data
  Preperation](#data-preperation)
  - [<span class="toc-section-number">3.1</span> retrieving child
    populations within .5 mile
    radius](#retrieving-child-populations-within-5-mile-radius)
- [<span class="toc-section-number">4</span> Analyses](#analyses)
  - [<span class="toc-section-number">4.0.1</span> How does the observed
    use of playgrounds differ between parks located in opportunity areas
    and parks not located in opportunity
    areas?](#how-does-the-observed-use-of-playgrounds-differ-between-parks-located-in-opportunity-areas-and-parks-not-located-in-opportunity-areas)
  - [<span class="toc-section-number">4.1</span> Chart of Park
    Catchment, sorted by Opportunity
    Area](#chart-of-park-catchment-sorted-by-opportunity-area)
  - [<span class="toc-section-number">4.2</span> Chart of Youth Park
    Catchment, sorted by Opportunity
    Area](#chart-of-youth-park-catchment-sorted-by-opportunity-area)
    - [<span class="toc-section-number">4.2.1</span> Chart of Average
      Playground Use, sorted by Opportunity
      Area](#chart-of-average-playground-use-sorted-by-opportunity-area)
    - [<span class="toc-section-number">4.2.2</span> Chart of Median
      Playground Use, sorted by Opportunity
      Area](#chart-of-median-playground-use-sorted-by-opportunity-area)
    - [<span class="toc-section-number">4.2.3</span> Chart of Peak
      Playground Use, sorted by Opportunity
      Area](#chart-of-peak-playground-use-sorted-by-opportunity-area)
  - [<span class="toc-section-number">4.3</span> How does the observed
    use of playgrounds differ between parks of similar park
    categories?](#how-does-the-observed-use-of-playgrounds-differ-between-parks-of-similar-park-categories)
    - [<span class="toc-section-number">4.3.1</span> Chart of Park
      Catchment, sorted by Park
      Category](#chart-of-park-catchment-sorted-by-park-category)
    - [<span class="toc-section-number">4.3.2</span> Chart of Youth Park
      Catchment, sorted by Park
      Category](#chart-of-youth-park-catchment-sorted-by-park-category)
    - [<span class="toc-section-number">4.3.3</span> Chart of Average
      Playground Use, sorted by Park
      Category](#chart-of-average-playground-use-sorted-by-park-category)
    - [<span class="toc-section-number">4.3.4</span> Chart of Peak
      Playground Use, sorted by Park
      Category](#chart-of-peak-playground-use-sorted-by-park-category)
    - [<span class="toc-section-number">4.3.5</span> Chart of Average
      Playground Popularity, sorted by Park
      Category](#chart-of-average-playground-popularity-sorted-by-park-category)
  - [<span class="toc-section-number">4.4</span> How does the observed
    use of playgrounds differ between playgrounds with different
    complexities of
    playgrounds?](#how-does-the-observed-use-of-playgrounds-differ-between-playgrounds-with-different-complexities-of-playgrounds)
    - [<span class="toc-section-number">4.4.1</span> Chart of Average
      Playground Use, sorted by Play
      Elements](#chart-of-average-playground-use-sorted-by-play-elements)
    - [<span class="toc-section-number">4.4.2</span> Chart of Peak
      Playground Use, sorted by Play
      Elements](#chart-of-peak-playground-use-sorted-by-play-elements)
    - [<span class="toc-section-number">4.4.3</span> Chart of Average
      Playground Popularity, sorted by Play
      Elements](#chart-of-average-playground-popularity-sorted-by-play-elements)
  - [<span class="toc-section-number">4.5</span> How does the observed
    use of playgrounds compare to the age of the
    playground?](#how-does-the-observed-use-of-playgrounds-compare-to-the-age-of-the-playground)
    - [<span class="toc-section-number">4.5.1</span> Chart of Average
      Playground Use, sorted by Playground Installation
      Date](#chart-of-average-playground-use-sorted-by-playground-installation-date)
    - [<span class="toc-section-number">4.5.2</span> Chart of Peak
      Playground Use, sorted by Playground Installation
      Date](#chart-of-peak-playground-use-sorted-by-playground-installation-date)
    - [<span class="toc-section-number">4.5.3</span> Chart of Playground
      Installation Date and Opportunity Area (denoting differences in
      Park
      Category)](#chart-of-playground-installation-date-and-opportunity-area-denoting-differences-in-park-category)
  - [<span class="toc-section-number">4.6</span> How does the observed
    use of playgrounds differ when a park includes certain
    features?](#how-does-the-observed-use-of-playgrounds-differ-when-a-park-includes-certain-features)
    - [<span class="toc-section-number">4.6.1</span> Chart of Average
      Playground Use, based on if park contains a restroom, separated by
      park
      category](#chart-of-average-playground-use-based-on-if-park-contains-a-restroom-separated-by-park-category)
    - [<span class="toc-section-number">4.6.2</span> Chart of Average
      Playground Use, based on if park contains a picnic area, separated
      by park
      category](#chart-of-average-playground-use-based-on-if-park-contains-a-picnic-area-separated-by-park-category)
    - [<span class="toc-section-number">4.6.3</span> Chart of Average
      Playground Use, based on if park contains a sports field,
      separated by park
      category](#chart-of-average-playground-use-based-on-if-park-contains-a-sports-field-separated-by-park-category)
  - [<span class="toc-section-number">4.7</span> How does the age of
    observed playground users differ between park groups (size, feature
    qualities,
    etc.)?](#how-does-the-age-of-observed-playground-users-differ-between-park-groups-size-feature-qualities-etc)
    - [<span class="toc-section-number">4.7.1</span> Chart of Average
      Playground Use, sorted by Play Element, separated by Primary Age
      Group](#chart-of-average-playground-use-sorted-by-play-element-separated-by-primary-age-group)
    - [<span class="toc-section-number">4.7.2</span> Chart of Peak
      Playground Use, sorted by Play Element, separated by Primary Age
      Group](#chart-of-peak-playground-use-sorted-by-play-element-separated-by-primary-age-group)
    - [<span class="toc-section-number">4.7.3</span> Chart of Playground
      Popularity, sorted by Play Element, separated by Primary Age
      Group](#chart-of-playground-popularity-sorted-by-play-element-separated-by-primary-age-group)
    - [<span class="toc-section-number">4.7.4</span> Chart of Playground
      Popularity specifically of observed child and teen, sorted by Play
      Element, separated by Primary Age
      Group](#chart-of-playground-popularity-specifically-of-observed-child-and-teen-sorted-by-play-element-separated-by-primary-age-group)
  - [<span class="toc-section-number">4.8</span> How accessible is the
    park by
    transportation?](#how-accessible-is-the-park-by-transportation)
  - [<span class="toc-section-number">4.9</span> By walking: Chart of
    Playground Use by Walkscore of
    park](#by-walking-chart-of-playground-use-by-walkscore-of-park)
  - [<span class="toc-section-number">4.10</span> By transit: Chart of
    Playground Use by Transitscore of
    park](#by-transit-chart-of-playground-use-by-transitscore-of-park)

# Front Matter

This document outlines procedures, technical considerations, and
analytic results for a 2024 analysis of playgrounds within parks
participating in the HEAL Parks Study. The primary purpose of this PDF
is technical review by analyst and project managers to confirm the
process and data quality.

For general information about the project please review the
[git](https://github.com/PHSKC-APDE/HEAL_Parks_Analysis) or contact Seth
Schromen-Wawrin.

## Major inputs

Inputs to this script are contained at ./inputs/*.* and include

- A file of park meta data, including address, zip, city, neighborhood,
  official name, and REDCap name for each park
- A file of collected SOPARC observations, aggregated to the period
  level
- An accompanying file of SOPARC activities

## Output categories

- tables - tabular outputs of analysis, generally in xlsx format
- charts - chart outputs of analysis, generally in pdf and/or png format

## This is a quarto generated document

By rendering/knitting the qmd file, the analysis is re-executed, this
document rebuilt, and new outputs are generated. To learn more about
Quarto see \[https://quarto.org\].

# Setup & Environment

This script was last executed using R version 4.4.1 (2024-06-14 ucrt).

# Data Preperation

This analysis relies on park observations and park activity tables
created in the annual SOPARC study

Some parks were included in the data set because observers practiced
there. However these are not part of the playground study

Remove garfield Remove brighton \*no playgrounds Remoev steel lake
Remove midway

## retrieving child populations within .5 mile radius

# Analyses

Notes:

- Analyses of “average park use” aggregate all playground within the
  park (effectively calculated as one large playground)
- Multiple park characteristics in the supplamental information file
  have n/a or tbd for parks that, including for parks that have
  playgrounds. Depending on the analysis, these may show up as NA, tbd,
  or 0

### How does the observed use of playgrounds differ between parks located in opportunity areas and parks not located in opportunity areas?

## Chart of Park Catchment, sorted by Opportunity Area

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-1-1.png)

## Chart of Youth Park Catchment, sorted by Opportunity Area

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-2-1.png)

### Chart of Average Playground Use, sorted by Opportunity Area

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-3-1.png)

### Chart of Median Playground Use, sorted by Opportunity Area

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-4-1.png)

### Chart of Peak Playground Use, sorted by Opportunity Area

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-5-1.png)

## How does the observed use of playgrounds differ between parks of similar park categories?

### Chart of Park Catchment, sorted by Park Category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-6-1.png)

Notes:

The following parks were excluded for not having category status: Dick
Thurnau Memorial Park, North Shorewood Park, Skyway Park

### Chart of Youth Park Catchment, sorted by Park Category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-7-1.png)

Notes:

The following parks were excluded for not having category status: Dick
Thurnau Memorial Park, North Shorewood Park, Skyway Park

### Chart of Average Playground Use, sorted by Park Category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-8-1.png)

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-9-1.png)

### Chart of Peak Playground Use, sorted by Park Category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-10-1.png)

### Chart of Average Playground Popularity, sorted by Park Category

Average Popularity is the average of the daily popularity rate, where
popularity rate is the proportion of park users (in a day) who were in
the playground

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-11-1.png)

## How does the observed use of playgrounds differ between playgrounds with different complexities of playgrounds?

### Chart of Average Playground Use, sorted by Play Elements

Notes:

- Garfield is missing a value

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-12-1.png)

### Chart of Peak Playground Use, sorted by Play Elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-13-1.png)

### Chart of Average Playground Popularity, sorted by Play Elements

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-14-1.png)

## How does the observed use of playgrounds compare to the age of the playground?

### Chart of Average Playground Use, sorted by Playground Installation Date

garfield is missing data

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-15-1.png)

    <ScaleContinuousPosition>
     Range:  
     Limits:    0 --    1

### Chart of Peak Playground Use, sorted by Playground Installation Date

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-16-1.png)

    <ScaleContinuousPosition>
     Range:  
     Limits:    0 --    1

### Chart of Playground Installation Date and Opportunity Area (denoting differences in Park Category)

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-17-1.png)

## How does the observed use of playgrounds differ when a park includes certain features?

### Chart of Average Playground Use, based on if park contains a restroom, separated by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-18-1.png)

### Chart of Average Playground Use, based on if park contains a picnic area, separated by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-19-1.png)

### Chart of Average Playground Use, based on if park contains a sports field, separated by park category

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-20-1.png)

## How does the age of observed playground users differ between park groups (size, feature qualities, etc.)?

### Chart of Average Playground Use, sorted by Play Element, separated by Primary Age Group

garfield is missing, not actually “no”

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-21-1.png)

### Chart of Peak Playground Use, sorted by Play Element, separated by Primary Age Group

garfield is missing, not actually “no”

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-22-1.png)

### Chart of Playground Popularity, sorted by Play Element, separated by Primary Age Group

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-23-1.png)

### Chart of Playground Popularity specifically of observed child and teen, sorted by Play Element, separated by Primary Age Group

Here, popularity is parameterized as

$\frac{\text{num of children and teens in playground}} {\text{num of children and teens in park}}$

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-24-1.png)

## How accessible is the park by transportation?

## By walking: Chart of Playground Use by Walkscore of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-25-1.png)

    <ScaleContinuousPosition>
     Range:  
     Limits:    0 --    1

## By transit: Chart of Playground Use by Transitscore of park

![](01_Playground_Analysis_files/figure-commonmark/unnamed-chunk-26-1.png)

    <ScaleContinuousPosition>
     Range:  
     Limits:    0 --    1
