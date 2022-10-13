Mini Data-Analysis Deliverable 1
================

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.5 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

3.  Make a repository in the <https://github.com/stat545ubc-2022>
    Organization. You will be working with this repository for the
    entire data analysis project. You can either make it public, or make
    it private and add the TA’s and Lucy as collaborators. A link to
    help you create a private repository is available on the
    \#collaborative-project Slack channel.

# Instructions

## For Both Milestones

-   Each milestone is worth 45 points. The number of points allocated to
    each task will be annotated within each deliverable. Tasks that are
    more challenging will often be allocated more points.

-   10 points will be allocated to the reproducibility, cleanliness, and
    coherence of the overall analysis. While the two milestones will be
    submitted as independent deliverables, the analysis itself is a
    continuum - think of it as two chapters to a story. Each chapter, or
    in this case, portion of your analysis, should be easily followed
    through by someone unfamiliar with the content.
    [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
    is a good resource for what constitutes “good code”. Learning good
    coding practices early in your career will save you hassle later on!

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 45 points: 43 for your analysis, 1
point for having your Milestone 1 document knit error-free, and 1 point
for tagging your release on Github.

# Learning Objectives

By the end of this milestone, you should:

-   Become familiar with your dataset of choosing
-   Select 4 questions that you would like to answer with your data
-   Generate a reproducible and clear report using R Markdown
-   Become familiar with manipulating and summarizing your data in
    tibbles using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset (10 points)

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

-   *apt_buildings*: Acquired courtesy of The City of Toronto’s Open
    Data Portal. It currently has 3455 rows and 37 columns.

-   *building_permits*: Acquired courtesy of The City of Vancouver’s
    Open Data Portal. It currently has 20680 rows and 14 columns.

-   *cancer_sample*: Acquired courtesy of UCI Machine Learning
    Repository. It currently has 569 rows and 32 columns.

-   *flow_sample*: Acquired courtesy of The Government of Canada’s
    Historical Hydrometric Database. It currently has 218 rows and 7
    columns.

-   *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 10032 rows and 22 columns.

-   *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
    rows and 21 columns.

-   *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

-   We hope that this project will serve as practice for carrying our
    your own *independent* data analysis. Remember to comment your code,
    be explicit about what you are doing, and write notes in this
    markdown document when you feel that context is required. As you
    advance in the project, prompts and hints to do this will be
    diminished - it’ll be up to you!

-   Before choosing a dataset, you should always keep in mind **your
    goal**, or in other ways, *what you wish to achieve with this data*.
    This mini data-analysis project focuses on *data wrangling*,
    *tidying*, and *visualization*. In short, it’s a way for you to get
    your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 Out of the 7 datasets available in the `datateachr` package, choose
**4** that appeal to you based on their description. Write your choices
below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

1: building_permits 2: steam_games 3: vancouver_trees 4: flow_sample

<!----------------------------------------------------------------------------->

1.2 One way to narrowing down your selection is to *explore* the
datasets. Use your knowledge of dplyr to find out at least *3*
attributes about each of these datasets (an attribute is something such
as number of rows, variables, class type…). The goal here is to have an
idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

``` r
### EXPLORE HERE ###
glimpse(building_permits)
```

    ## Rows: 20,680
    ## Columns: 14
    ## $ permit_number               <chr> "BP-2016-02248", "BU468090", "DB-2016-0445…
    ## $ issue_date                  <date> 2017-02-01, 2017-02-01, 2017-02-01, 2017-…
    ## $ project_value               <dbl> 0, 0, 35000, 15000, 181178, 0, 15000, 0, 6…
    ## $ type_of_work                <chr> "Salvage and Abatement", "New Building", "…
    ## $ address                     <chr> "4378 W 9TH AVENUE, Vancouver, BC V6R 2C7"…
    ## $ project_description         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ building_contractor         <chr> NA, NA, NA, "Mercury Contracting Ltd", "08…
    ## $ building_contractor_address <chr> NA, NA, NA, "88 W PENDER ST  \r\nUnit 2069…
    ## $ applicant                   <chr> "Raffaele & Associates DBA: Raffaele and A…
    ## $ applicant_address           <chr> "2642 East Hastings\r\nVancouver, BC  V5K …
    ## $ property_use                <chr> "Dwelling Uses", "Dwelling Uses", "Dwellin…
    ## $ specific_use_category       <chr> "One-Family Dwelling", "Multiple Dwelling"…
    ## $ year                        <dbl> 2017, 2017, 2017, 2017, 2017, 2017, 2017, …
    ## $ bi_id                       <dbl> 524, 535, 539, 541, 543, 546, 547, 548, 54…

``` r
class(building_permits)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
dim(building_permits)
```

    ## [1] 20680    14

``` r
#Confirmed tibble with 20680 rows and 14 columns. 

head(steam_games)
```

    ## # A tibble: 6 × 21
    ##      id url          types name  desc_…¹ recen…² all_r…³ relea…⁴ devel…⁵ publi…⁶
    ##   <dbl> <chr>        <chr> <chr> <chr>   <chr>   <chr>   <chr>   <chr>   <chr>  
    ## 1     1 https://sto… app   DOOM  Now in… Very P… Very P… May 12… id Sof… Bethes…
    ## 2     2 https://sto… app   PLAY… PLAYER… Mixed,… Mixed,… Dec 21… PUBG C… PUBG C…
    ## 3     3 https://sto… app   BATT… Take c… Mixed,… Mostly… Apr 24… Harebr… Parado…
    ## 4     4 https://sto… app   DayZ  The po… Mixed,… Mixed,… Dec 13… Bohemi… Bohemi…
    ## 5     5 https://sto… app   EVE … EVE On… Mixed,… Mostly… May 6,… CCP     CCP,CCP
    ## 6     6 https://sto… bund… Gran… Grand … NaN     NaN     NaN     Rockst… Rockst…
    ## # … with 11 more variables: popular_tags <chr>, game_details <chr>,
    ## #   languages <chr>, achievements <dbl>, genre <chr>, game_description <chr>,
    ## #   mature_content <chr>, minimum_requirements <chr>,
    ## #   recommended_requirements <chr>, original_price <dbl>, discount_price <dbl>,
    ## #   and abbreviated variable names ¹​desc_snippet, ²​recent_reviews,
    ## #   ³​all_reviews, ⁴​release_date, ⁵​developer, ⁶​publisher

``` r
class(steam_games)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
dim(steam_games)
```

    ## [1] 40833    21

``` r
#confirmed tibble with 40833 rows and 21 columns. Noticed multiple answers inn popular_tags variable and long descriptions

glimpse(vancouver_trees)
```

    ## Rows: 146,611
    ## Columns: 20
    ## $ tree_id            <dbl> 149556, 149563, 149579, 149590, 149604, 149616, 149…
    ## $ civic_number       <dbl> 494, 450, 4994, 858, 5032, 585, 4909, 4925, 4969, 7…
    ## $ std_street         <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ genus_name         <chr> "ULMUS", "ZELKOVA", "STYRAX", "FRAXINUS", "ACER", "…
    ## $ species_name       <chr> "AMERICANA", "SERRATA", "JAPONICA", "AMERICANA", "C…
    ## $ cultivar_name      <chr> "BRANDON", NA, NA, "AUTUMN APPLAUSE", NA, "CHANTICL…
    ## $ common_name        <chr> "BRANDON ELM", "JAPANESE ZELKOVA", "JAPANESE SNOWBE…
    ## $ assigned           <chr> "N", "N", "N", "Y", "N", "N", "N", "N", "N", "N", "…
    ## $ root_barrier       <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N", "N", "…
    ## $ plant_area         <chr> "N", "N", "4", "4", "4", "B", "6", "6", "3", "3", "…
    ## $ on_street_block    <dbl> 400, 400, 4900, 800, 5000, 500, 4900, 4900, 4900, 7…
    ## $ on_street          <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ neighbourhood_name <chr> "MARPOLE", "MARPOLE", "KENSINGTON-CEDAR COTTAGE", "…
    ## $ street_side_name   <chr> "EVEN", "EVEN", "EVEN", "EVEN", "EVEN", "ODD", "ODD…
    ## $ height_range_id    <dbl> 2, 4, 3, 4, 2, 2, 3, 3, 2, 2, 2, 5, 3, 2, 2, 2, 2, …
    ## $ diameter           <dbl> 10.00, 10.00, 4.00, 18.00, 9.00, 5.00, 15.00, 14.00…
    ## $ curb               <chr> "N", "N", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "…
    ## $ date_planted       <date> 1999-01-13, 1996-05-31, 1993-11-22, 1996-04-29, 19…
    ## $ longitude          <dbl> -123.1161, -123.1147, -123.0846, -123.0870, -123.08…
    ## $ latitude           <dbl> 49.21776, 49.21776, 49.23938, 49.23469, 49.23894, 4…

``` r
class(vancouver_trees)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
dim(vancouver_trees)
```

    ## [1] 146611     20

``` r
#Confirmed tibble with 14661 rows and 20 columns. Straightforward data and variables can be investigated in relation to another.

head(flow_sample)
```

    ## # A tibble: 6 × 7
    ##   station_id  year extreme_type month   day  flow sym  
    ##   <chr>      <dbl> <chr>        <dbl> <dbl> <dbl> <chr>
    ## 1 05BB001     1909 maximum          7     7   314 <NA> 
    ## 2 05BB001     1910 maximum          6    12   230 <NA> 
    ## 3 05BB001     1911 maximum          6    14   264 <NA> 
    ## 4 05BB001     1912 maximum          8    25   174 <NA> 
    ## 5 05BB001     1913 maximum          6    11   232 <NA> 
    ## 6 05BB001     1914 maximum          6    18   214 <NA>

``` r
glimpse(flow_sample)
```

    ## Rows: 218
    ## Columns: 7
    ## $ station_id   <chr> "05BB001", "05BB001", "05BB001", "05BB001", "05BB001", "0…
    ## $ year         <dbl> 1909, 1910, 1911, 1912, 1913, 1914, 1915, 1916, 1917, 191…
    ## $ extreme_type <chr> "maximum", "maximum", "maximum", "maximum", "maximum", "m…
    ## $ month        <dbl> 7, 6, 6, 8, 6, 6, 6, 6, 6, 6, 6, 7, 6, 6, 6, 7, 5, 7, 6, …
    ## $ day          <dbl> 7, 12, 14, 25, 11, 18, 27, 20, 17, 15, 22, 3, 9, 5, 14, 5…
    ## $ flow         <dbl> 314, 230, 264, 174, 232, 214, 236, 309, 174, 345, 185, 24…
    ## $ sym          <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…

``` r
dim(flow_sample)
```

    ## [1] 218   7

``` r
class(flow_sample)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#Confirmed tibble with 218 rows and 7 columns. Smallest dataset, nots of numeric variables.
```

<!----------------------------------------------------------------------------->

1.3 Now that you’ve explored the 4 datasets that you were initially most
interested in, let’s narrow it down to 2. What lead you to choose these
2? Briefly explain your choices below, and feel free to include any code
in your explanation.

<!-------------------------- Start your work below ---------------------------->

2 datasets I am cosidering now is steam_games and vancouver_trees
because the data is straightforward and I am able to think of
relationships between the different variables. Additionally, these two
datasets have fewer variables to work with so it will be easy to work
with.
<!----------------------------------------------------------------------------->

1.4 Time for the final decision! Going back to the beginning, it’s
important to have an *end goal* in mind. For example, if I had chosen
the `titanic` dataset for my project, I might’ve wanted to explore the
relationship between survival and other variables. Try to think of 1
research question that you would want to answer with each dataset. Note
them down below, and make your final choice based on what seems more
interesting to you!

<!-------------------------- Start your work below ---------------------------->

For steam_games, I would be interested to see the relationship between
release_date and genre to see if there was a specific time period where
certain genres were more popular. I could plot the relationship by bar
graph.

For vancouver_trees, I would be interested manipulating diameter to find
the average diameter and neighbourhood_name to see which neighbourhoods
have on average wider diameter trees.

My final choice is vancouver_trees because I’m interested to know more
about the landscape in Vancouver which is the city that I was born and
raised in.
<!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate.
Remember, marks will be awarded for completion of the 4 tasks, but 10
points of the whole project are allocated to a reproducible and clean
analysis. If you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset (15 points)

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 Complete *4 out of the following 8 exercises* to dive deeper into
your data. All datasets are different and therefore, not all of these
tasks may make sense for your data - which is why you should only answer
*4*. Use *dplyr* and *ggplot*.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 For each of the 4 exercises that you complete, provide a *brief
explanation* of why you chose that exercise in relation to your data (in
other words, why does it make sense to do that?), and sufficient
comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->
<!----------------------------------------------------------------------------->

# Task 3: Write your research questions (5 points)

So far, you have chosen a dataset and gotten familiar with it through
exploring the data. Now it’s time to figure out 4 research questions
that you would like to answer with your data! Write the 4 questions and
any additional comments at the end of this deliverable. These questions
are not necessarily set in stone - TAs will review them and give you
feedback; therefore, you may choose to pursue them as they are for the
rest of the project, or make modifications!

<!--- *****START HERE***** --->

**Task 2: I will be doing number 1,4,5, and 6** 1. Plot the distribution
of a numeric variable. I will be looking at the distribution of the
height_range_id to see which height ranges are most common in Vancouver.

``` r
ggplot(vancouver_trees, aes(height_range_id)) + geom_histogram(bins = 15)
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
#I played around with different bins commands and found that 15 gave the nicest graph. 
```

4.  Explore the relationship between 2 variables in a plot. I will be
    looking to see if there are any trends in the height range of trees
    in Vancouver as time goes on.

``` r
ggplot(vancouver_trees, aes(date_planted, height_range_id)) + geom_line(colour = "blue")
```

    ## Warning: Removed 76548 row(s) containing missing values (geom_path).

![](Deliverable-1_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
#After looking at this plot, I noticed that the the trees planted between 2010-2020 have shorter height ranges than trees in 2000-2010.
```

5.  Filter observations in your data according to your own criteria. I
    will be looking at diameter and see how I want to filter the
    variable.

``` r
max(vancouver_trees$diameter) #435
```

    ## [1] 435

``` r
min(vancouver_trees$diameter) #0
```

    ## [1] 0

``` r
median(vancouver_trees$diameter) #9
```

    ## [1] 9

``` r
#After knowing the max, min, and median values of diameter, I was surprised to know that the median was 9 which is so much closer to the min than max so I want to filter all the trees that have a diameter less than 9 to see what is going on.

filter(vancouver_trees, diameter < 9) 
```

    ## # A tibble: 71,893 × 20
    ##    tree_id civic_number std_st…¹ genus…² speci…³ culti…⁴ commo…⁵ assig…⁶ root_…⁷
    ##      <dbl>        <dbl> <chr>    <chr>   <chr>   <chr>   <chr>   <chr>   <chr>  
    ##  1  149579         4994 WINDSOR… STYRAX  JAPONI… <NA>    JAPANE… N       N      
    ##  2  149616          585 W 61ST … PYRUS   CALLER… CHANTI… CHANTI… N       N      
    ##  3  149625          720 E 39TH … FRAXIN… AMERIC… AUTUMN… AUTUMN… N       N      
    ##  4  149626          736 E 39TH … TILIA   EUCHLO… <NA>    CRIMEA… N       N      
    ##  5  149646          505 E 16TH … HIBISC… SYRIACA <NA>    ROSE O… N       N      
    ##  6  149647          509 E 16TH … STYRAX  JAPONI… <NA>    JAPANE… N       N      
    ##  7  149658         5208 WINDSOR… STYRAX  JAPONI… <NA>    JAPANE… N       N      
    ##  8  155226         4525 CLAREND… LIQUID… STYRAC… <NA>    AMERIC… N       N      
    ##  9  155398         1402 MCRAE AV STYRAX  JAPONI… <NA>    JAPANE… N       N      
    ## 10  155416         1394 ROBSON … ROBINIA PSEUDO… <NA>    BLACK … N       N      
    ## # … with 71,883 more rows, 11 more variables: plant_area <chr>,
    ## #   on_street_block <dbl>, on_street <chr>, neighbourhood_name <chr>,
    ## #   street_side_name <chr>, height_range_id <dbl>, diameter <dbl>, curb <chr>,
    ## #   date_planted <date>, longitude <dbl>, latitude <dbl>, and abbreviated
    ## #   variable names ¹​std_street, ²​genus_name, ³​species_name, ⁴​cultivar_name,
    ## #   ⁵​common_name, ⁶​assigned, ⁷​root_barrier

6.  Use a boxplot to look at the frequency of different observations
    within a single variable. I will be looking at the diameter of the
    tree by whether they do or do not have a root barrier.

``` r
ggplot(vancouver_trees, aes(root_barrier, diameter)) + geom_boxplot()
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
#After looking at this boxplot, it looks like trees with a root barrier have smaller diameters than trees without root barriers.
```

**Task 3: Write your research questions** 1. What are the average
diameter of trees in each neighbourhood in Vancouver? 2. Does having a
root barrier result in a smaller tree diameter? 3. Does having a root
barrier result in a smaller height range tree? 4. Is the height range of
trees getting smaller as the years go on?

# Task 4: Process and summarize your data (13 points)

From Task 2, you should have an idea of the basic structure of your
dataset (e.g. number of rows and columns, class types, etc.). Here, we
will start investigating your data more in-depth using various data
manipulation functions.

### 1.1 (10 points)

Now, for each of your four research questions, choose one task from
options 1-4 (summarizing), and one other task from 4-8 (graphing). You
should have 2 tasks done for each research question (8 total). Make sure
it makes sense to do them! (e.g. don’t use a numerical variables for a
task that needs a categorical variable.). Comment on why each task helps
(or doesn’t!) answer the corresponding research question.

Ensure that the output of each operation is printed!

**Summarizing:**

1.  Compute the *range*, *mean*, and *two other summary statistics* of
    **one numerical variable** across the groups of **one categorical
    variable** from your data.
2.  Compute the number of observations for at least one of your
    categorical variables. Do not use the function `table()`!
3.  Create a categorical variable with 3 or more groups from an existing
    numerical variable. You can use this new variable in the other
    tasks! *An example: age in years into “child, teen, adult, senior”.*
4.  Based on two categorical variables, calculate two summary statistics
    of your choosing.

**Graphing:**

5.  Create a graph out of summarized variables that has at least two
    geom layers.
6.  Create a graph of your choosing, make one of the axes logarithmic,
    and format the axes labels so that they are “pretty” or easier to
    read.
7.  Make a graph where it makes sense to customize the alpha
    transparency.
8.  Create 3 histograms out of summarized variables, with each histogram
    having different sized bins. Pick the “best” one and explain why it
    is the best.

Make sure it’s clear what research question you are doing each operation
for!

<!------------------------- Start your work below ----------------------------->

**Research Question 1: What are the average diameter of trees in each
neighbourhood in Vancouver?**

*Summarize 1*

``` r
#To find the average mean of trees in each neighbourhood
neighbourhood_meandiameter <- vancouver_trees %>%
  group_by(neighbourhood_name) %>%
  summarise(diameter_mean = mean(diameter, na.rm = TRUE)) 

#Now I want to know the summary statistics of the average diameter between the different neighbourhoods.
#Finding range
range(neighbourhood_meandiameter$diameter_mean)
```

    ## [1]  7.445648 14.419742

``` r
#Can determine min and max for range aas well as mean, median, 1st and 3rd quartile
summary(neighbourhood_meandiameter) 
```

    ##  neighbourhood_name diameter_mean   
    ##  Length:22          Min.   : 7.446  
    ##  Class :character   1st Qu.:10.305  
    ##  Mode  :character   Median :11.435  
    ##                     Mean   :11.391  
    ##                     3rd Qu.:12.064  
    ##                     Max.   :14.420

``` r
#Finding standard deviation
sd(neighbourhood_meandiameter$diameter_mean)
```

    ## [1] 1.684479

From the summary or range function, the range of average diameters
grouped by different neighbourhoods is 7.446 - 14.240. From the summary
function, the mean is 11.435 and the median is 11.435. The standard
deviation is 1.684479.

*Graphing 8*

``` r
ggplot(neighbourhood_meandiameter, aes(diameter_mean)) + geom_histogram(bins = 10)
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
ggplot(neighbourhood_meandiameter, aes(diameter_mean)) + geom_histogram(bins = 20)
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-8-2.png)<!-- -->

``` r
ggplot(neighbourhood_meandiameter, aes(diameter_mean)) + geom_histogram(bins = 40)
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-8-3.png)<!-- --> From
the different histograms, I plotted where bins = 10, 20, and 40 and I
think the bins = 10 looks the best because you can see the distribution
better and there are no big gaps between the different bins.

**Research question 2: Does having a root barrier result in a smaller
tree diameter?**

*Summarize 1*

``` r
#First I want to compare statistics between trees that having a root barrier and trees that do not
rootbarrier_y <- filter(vancouver_trees, root_barrier == "Y")
rootbarrier_n <- filter(vancouver_trees, root_barrier =="N")

#Now I will look at range, mean, standard deviation, and median of diameter for both datasubsets. 
summary(rootbarrier_y$diameter)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##     0.5     3.0     3.0     4.4     5.0    86.0

``` r
sd(rootbarrier_y$diameter)
```

    ## [1] 2.998134

``` r
#Min = 0.5, Max = 86, Median = 3.0, Mean = 4.4, SD = 2.998134

summary(rootbarrier_n$diameter)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    0.00    4.00   10.00   11.96   17.00  435.00

``` r
sd(rootbarrier_n$diameter)
```

    ## [1] 9.290934

``` r
#Min = 0, Max = 435, Median = 10.0, Mean = 11.96, SD = 9.290934
```

Comparing the statistics between the diameter of trees that do or do not
have a root barrier shows that trees with a root barrier on average is
smaller than trees that do not have a root barrier.

*Graphing 6*

``` r
ggplot(vancouver_trees, aes(root_barrier, diameter)) + geom_jitter(alpha = 0.5) + xlab("Root Barrier") 
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-10-1.png)<!-- --> This
jitterplot visualizes that trees trees with a root barrier have a
smaller diameter compared to trees without a root barrier. This is a
good time to make the transparency lower so that the dots on the
jitterplot are not too crowded.

**Research Question 3: Does having a root barrier result in a shorter
height tree?**

*Summarize 2*

``` r
#To count the number of observations, I will be grouping the height ranges into levels and counting how many trees are in each level.
rootbarrier_y$height_range_id <- as.factor(rootbarrier_y$height_range_id)
summary(rootbarrier_y$height_range_id)
```

    ##    0    1    2    3    4    5    6    7    8    9 
    ##   43 6998 1633  314  142   13    8    2    2    1

``` r
#Level 0 = 43,    1 = 6998,   2 = 1633,    3 = 314,    4 = 142,    5 = 13    6 = 8,    7 = 2,    8 = 2,    9 = 1

rootbarrier_n$height_range_id <-as.factor(rootbarrier_n$height_range_id)
summary(rootbarrier_n$height_range_id)
```

    ##     0     1     2     3     4     5     6     7     8     9    10 
    ##   171 32961 40573 25993 20388  9001  5187  2223   744   202    12

``` r
#Level 0 = 171, 1 = 32961, 2 = 40573, 3 = 25993, 4 = 20388, 5 = 9001, 6 = 5187, 7 = 2223, 8 = 744, 9 = 202, 10 = 12
```

Comparing the number of observations in higher level height ranges
between trees that do and do not have root barriers, you can see that
trees that do not have root barriers have more observations seen in the
heigher level of height ranges.

\*Graphing

``` r
ggplot(vancouver_trees, aes(root_barrier, height_range_id)) + geom_jitter(colour = "dark green", alpha = 0.5) + xlab("Root Barrier") + ylab("Height Range")
```

![](Deliverable-1_files/figure-gfm/unnamed-chunk-12-1.png)<!-- --> This
jitterplot shows that there are more trees in different height ranges if
they do not have a root barrier.

**Research Question 4: Is the height ranges of trees getting smaller as
the years go on?**

*Summarize 1*

``` r
summary(vancouver_trees$height_range_id)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   0.000   1.000   2.000   2.627   4.000  10.000

``` r
sd(vancouver_trees$height_range_id)
```

    ## [1] 1.542994

From these two functions, I can see the range of height-ranges are from
0 - 10. The mean is 2.627, the median is 2 and the standard deviation is
1.542994.

*Graphing 5*

``` r
ggplot(vancouver_trees, aes(date_planted, height_range_id)) + geom_line(colour = "Blue") + geom_point(colour = "blue", size = 0.5)
```

    ## Warning: Removed 76548 row(s) containing missing values (geom_path).

    ## Warning: Removed 76548 rows containing missing values (geom_point).

![](Deliverable-1_files/figure-gfm/unnamed-chunk-14-1.png)<!-- --> From
this graph, you can see that there were trees with higher height range
before 2000 and the height range slowly declines from 2000 to 2020. This
graph has geom_point added onto geom_line (2 layers) so that you can
still the full range of heights.
<!----------------------------------------------------------------------------->

### 1.2 (3 points)

Based on the operations that you’ve completed, how much closer are you
to answering your research questions? Think about what aspects of your
research questions remain unclear. Can your research questions be
refined, now that you’ve investigated your data a bit more? Which
research questions are yielding interesting results?

<!-------------------------- Start your work below ---------------------------->

Based on these exercises, I think I can close to answering question 2-4.
Questions 2 and 2 where I look at the impact of root barrier on height
and diameter shows that having a root barrier negatively impacts these
two qualities of a tree. In question 4, the graph visualizes very well
that the height of trees after 2000 have a negative trend. For question
1, the summarize exercise is able to tell me the average diameter of
trees in each neighbourhood but the plot exercise does not contribute
much to answering the research question.

<!----------------------------------------------------------------------------->

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
