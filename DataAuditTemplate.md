# Data Overview: 3rd down decision-making in the CFL
Tyler Forbes
2026-11-18

- [1: Project Overview](#1-project-overview)
  - [In the Canadian Football League, 3rd down is the kind of play where
    if a team does not reach the line to gain, they turn the ball over
    to the other team. In response to the pressure, teams decide to punt
    the ball downfield, kick for a field goal, or take the risk and play
    the ball to get a first down. My project aims to help teams make
    better decisions in this scenario using play-by-play data from the
    2024 and 2025 seasons so teams aren’t just driven by fear, but also
    data.](#in-the-canadian-football-league-3rd-down-is-the-kind-of-play-where-if-a-team-does-not-reach-the-line-to-gain-they-turn-the-ball-over-to-the-other-team-in-response-to-the-pressure-teams-decide-to-punt-the-ball-downfield-kick-for-a-field-goal-or-take-the-risk-and-play-the-ball-to-get-a-first-down-my-project-aims-to-help-teams-make-better-decisions-in-this-scenario-using-play-by-play-data-from-the-2024-and-2025-seasons-so-teams-arent-just-driven-by-fear-but-also-data)
- [2: Data Sources](#2-data-sources)
  - [2.1 Summary of sources](#21-summary-of-sources)
  - [2.2.1: CFL Charts PbP Data](#221-cfl-charts-pbp-data)
  - [2.3: Investigated and rejected
    sources](#23-investigated-and-rejected-sources)
  - [2.4: What I could not find](#24-what-i-could-not-find)
- [3: Licensing and permissions](#3-licensing-and-permissions)
  - [3.1: Licence by source](#31-licence-by-source)
  - [3.2: Unresolved licensing](#32-unresolved-licensing)
  - [3.3: Downstream permissions](#33-downstream-permissions)
- [4: Consent and identifiability](#4-consent-and-identifiability)
- [5: Exclusions and harms](#5-exclusions-and-harms)
  - [5.1: Excluded data from the
    audit](#51-excluded-data-from-the-audit)
  - [5.2: Who could be harmed](#52-who-could-be-harmed)
  - [5.3: Unreleased working data](#53-unreleased-working-data)
- [6: Data Stewardship](#6-data-stewardship)
- [7: Use of AI](#7-use-of-ai)
- [8: Session information](#8-session-information)

<!--  another version of markdown elements, this works for html-style documents
&#10;[FP Part 2: HOW TO USE THIS TEMPLATE FOR YOUR SUBMISSION
&#10;Replace every bracketed prompt with your own writing (remove the brackets themselves, they're part of the placeholder here), and delete the prompt. 
&#10;Delete any sections that are not relevant for project, but note in commit message notes (not commit titles!) why you chose to delete them. That way I know that you've been thinking through what will be relevant as you begin the coding portion of this project.
&#10;Render, commit and push the markdown AND the .Rmd to your final project folder. 
&#10;This document will live in your final project folder in your repository alongside the AI-LOG.md, your code, and your raw data. Remember to commit it as you work on it, so that it doesn't get mixed up in your class or assignment commit messages.]
-->

# 1: Project Overview

## In the Canadian Football League, 3rd down is the kind of play where if a team does not reach the line to gain, they turn the ball over to the other team. In response to the pressure, teams decide to punt the ball downfield, kick for a field goal, or take the risk and play the ball to get a first down. My project aims to help teams make better decisions in this scenario using play-by-play data from the 2024 and 2025 seasons so teams aren’t just driven by fear, but also data.

# 2: Data Sources

<!-- For the section numbers above, remember to update if needed for multiple sources or removing unneeded subsections -->

## 2.1 Summary of sources

| Source | Producer | Format | Coverage | Using |
|:---|:---|:---|:---|:---|
| CFL Talk | Canadian Football Forum | PDF | CFL, 2024-present | No |
| CFLCharts.ca | CFLCharts.ca - third-party site using CFL data | CSV | CFL, 2024-2025 | Yes |
| CFL API | CFL, Statsperform/Customerhub | API | CFL, 2023-present | No |

## 2.2.1: CFL Charts PbP Data

**Producer and authority.** CFLCharts.ca is a third-party site using
public play-by-play and other game information given by the CFL’s API,
with additional stats like win probabilities and expected points for
valuing game situations. It is likely just a passionate fan publishing
to share insights.

**Original Dataset Purpose.** Observing the site, it looks like just a
passionate CFL fan who wanted to expand on game data shared their
findings.

**Collection method.** The data is collected from the CFL API’s
play-by-play info. The data is not manually checked for accuracy.

**Coverage and resolution.** One row per recorded play. A single game
dataset has 148 plays with 93 columns. The coverage being used is all of
the 2024 season and a majority of the 2025 season.

**Licence.** Not found

**Access.** It was retrieved from cflstats.ca, a website with a very
simple interface. The base link is where the match data is accessed
from. I accessed it Nov 18. Data stopped being posted on the site in
September 2025, so it’s reasonable to assume a chance that the site
could come down without warning.

**Known problems.** The About section indicates a possibility of
slightly inaccurate data. Also, EP and EPA statistics are not very clear
on what exactly they are, although definitions can be found with clues
and maybe some reverse engineering. Data is incomplete in that the 2025
season’s data was not fully posted online, although datasets for each
game are still available online.

    Rows: 148
    Columns: 93
    $ game                         <chr> "WEEK 14 - CGY @ EDM", "WEEK 14 - CGY @ E…
    $ cfl_game_id                  <dbl> 6549, 6549, 6549, 6549, 6549, 6549, 6549,…
    $ play_id                      <chr> "24-2", "1-3", "0-1", "1-1", "1-2", "1-4"…
    $ play_number                  <dbl> 88, 4, 1, 2, 3, 5, 6, 7, 8, 9, 10, 11, 12…
    $ team_drive                   <dbl> 12, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2…
    $ play_of_drive                <dbl> 2, 3, 1, 1, 2, 4, 5, 6, 7, 8, 1, 2, 3, 4,…
    $ half                         <dbl> 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
    $ quarter                      <dbl> 3, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
    $ clock_time                   <time> 08:00:00, 13:29:00, 15:00:00, 14:40:00, …
    $ clock_time_seconds           <dbl> 480, 809, 900, 880, 845, 770, 731, 706, 6…
    $ seconds_in_half_remaining    <dbl> 1380, 1709, 1800, 1780, 1745, 1670, 1631,…
    $ seconds_in_game_remaining    <dbl> 1380, 3509, 3600, 3580, 3545, 3470, 3431,…
    $ home_team_score              <dbl> 21, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0…
    $ away_team_score              <dbl> 12, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 3, 3, 3…
    $ field_position               <chr> "CGY50", "EDM43", "EDM30", "CGY44", "EDM5…
    $ field_position_end           <chr> "CGY55", "EDM40", "CGY44", "EDM51", "EDM4…
    $ yards_to_endzone             <dbl> 60, 43, 80, 66, 51, 40, 36, 20, 20, 20, 7…
    $ yards_to_endzone_end         <dbl> 55, 40, 44, 51, 43, 36, 20, 20, 20, 40, 5…
    $ down                         <dbl> 1, 2, NA, 1, 1, 1, 2, 1, 2, 3, 1, 1, 1, 2…
    $ yards_to_go                  <dbl> 10, 2, NA, 10, 10, 10, 6, 10, 10, 10, 10,…
    $ possession_team              <chr> "CGY", "CGY", "EDM", "CGY", "CGY", "CGY",…
    $ defensive_team               <chr> "EDM", "EDM", "CGY", "EDM", "EDM", "EDM",…
    $ description                  <chr> "PENALTY EDM Offside (#42 N.Taylor) 5 yar…
    $ play_type                    <chr> "Penalty", "Run", "Kickoff", "Pass", "Pas…
    $ play_sub_type                <chr> "Offside", "Basic", "Basic", "CompletePas…
    $ play_result                  <chr> "No Play", "Nothing", "Kickoff", "Nothing…
    $ result_yards                 <dbl> 5, 3, 36, 15, 8, 4, 16, 0, 0, 0, 14, 17, …
    $ result_points                <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 0, 0, 0, 0,…
    $ is_change_of_possession      <dbl> 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0,…
    $ is_1st_down                  <dbl> 0, 1, 0, 1, 0, 0, 1, 0, 0, 0, 1, 1, 0, 0,…
    $ is_penalty                   <dbl> 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1,…
    $ is_official                  <dbl> 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0,…
    $ is_dropback                  <dbl> 0, 0, 0, 1, 1, 0, 1, 1, 1, 0, 1, 1, 0, 0,…
    $ is_rush                      <dbl> 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 1,…
    $ is_knee                      <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
    $ ep                           <dbl> 2.3292377, 3.3274330, -1.5793277, 2.00214…
    $ epa                          <dbl> 0.2726124, 0.3530505, -0.4228223, 0.94203…
    $ home_wp                      <dbl> 0.8102455, 0.4246794, 0.5710903, 0.521946…
    $ away_wp                      <dbl> 0.1897545, 0.5753206, 0.4289097, 0.478053…
    $ offense_wp                   <dbl> 0.1897545, 0.5753206, 0.5710903, 0.478053…
    $ defense_wp                   <dbl> 0.8102455, 0.4246794, 0.4289097, 0.521946…
    $ wpa                          <dbl> -0.0060762764, -0.0085689014, -0.04914366…
    $ dropback_prob                <dbl> NA, 0.19020714, NA, 0.55656504, 0.5551416…
    $ next_score                   <chr> "TOUCHDOWN FOR", "FIELD GOAL FOR", "FIELD…
    $ next_score_play_id           <chr> "26-10", "1-8", "1-8", "1-8", "1-8", "1-8…
    $ next_score_seconds_remaining <dbl> 669, 142, 233, 213, 178, 103, 64, 39, 21,…
    $ next_score_plays_remaining   <dbl> 23, 5, 8, 7, 6, 4, 3, 2, 1, 0, 5, 4, 3, 2…
    $ rusher_name                  <chr> NA, "Dedrick Mills", NA, NA, NA, "Dedrick…
    $ rusher_number                <dbl> NA, 26, NA, NA, NA, 26, NA, NA, NA, NA, N…
    $ rusher_id                    <dbl> NA, 1290033, NA, NA, NA, 1290033, NA, NA,…
    $ rusher_position              <chr> NA, "RB", NA, NA, NA, "RB", NA, NA, NA, N…
    $ tackler_name                 <chr> NA, "Brock Mogensen", "Kenny Logan Jr.", …
    $ tackler_number               <dbl> NA, 43, 20, 50, 43, 54, NA, NA, NA, NA, 2…
    $ tackler_id                   <dbl> NA, 1079457, 1464749, 1011445, 1079457, 1…
    $ tackler_position             <chr> NA, "LB", "LB", "LB", "LB", "DL", NA, NA,…
    $ kicker_name                  <chr> NA, NA, "Vincent Blanchard", NA, NA, NA, …
    $ kicker_number                <dbl> NA, NA, 26, NA, NA, NA, NA, NA, NA, 30, N…
    $ kicker_id                    <dbl> NA, NA, 1468042, NA, NA, NA, NA, NA, NA, …
    $ kicker_position              <chr> NA, NA, "K", NA, NA, NA, NA, NA, NA, "K",…
    $ returner_name                <chr> NA, NA, "Ludovick Choquette", NA, NA, NA,…
    $ returner_number              <dbl> NA, NA, 28, NA, NA, NA, NA, NA, NA, NA, N…
    $ returner_id                  <dbl> NA, NA, 1520021, NA, NA, NA, NA, NA, NA, …
    $ returner_position            <chr> NA, NA, "RB", NA, NA, NA, NA, NA, NA, NA,…
    $ passing_yards                <dbl> NA, NA, NA, 15, 8, NA, 0, 0, 0, NA, 14, 1…
    $ air_yards                    <dbl> NA, NA, NA, 10, 5, NA, 24, 5, 30, NA, 14,…
    $ yards_after_catch            <dbl> NA, NA, NA, 5, 3, NA, 0, 0, 0, NA, 0, 2, …
    $ completion_probability       <dbl> NA, NA, NA, 0.5979278, 0.7123398, NA, 0.4…
    $ qb_epa                       <dbl> NA, NA, NA, 0.5640265, -0.0637105, NA, NA…
    $ receiver_epa                 <dbl> NA, NA, NA, 0.3780069, 0.2436252, NA, NA,…
    $ passer_name                  <chr> NA, NA, NA, "Vernon Adams Jr.", "Vernon A…
    $ passer_number                <dbl> NA, NA, NA, 3, 3, NA, 3, 3, 3, NA, 7, 7, …
    $ passer_id                    <dbl> NA, NA, NA, 1349494, 1349494, NA, 1349494…
    $ passer_position              <chr> NA, NA, NA, "QB", "QB", NA, "QB", "QB", "…
    $ receiver_name                <chr> NA, NA, NA, "Erik Brooks", "Erik Brooks",…
    $ receiver_number              <dbl> NA, NA, NA, 87, 87, NA, 14, 85, 85, NA, 8…
    $ receiver_id                  <dbl> NA, NA, NA, 1081744, 1081744, NA, 1403599…
    $ receiver_position            <chr> NA, NA, NA, "WR", "WR", NA, "WR", "WR", "…
    $ holder_name                  <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, "Mark…
    $ holder_number                <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, 70, N…
    $ holder_id                    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, 14894…
    $ holder_position              <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, "P", …
    $ quarterback_name             <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ quarterback_number           <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ quarterback_id               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ quarterback_position         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ kneeler_name                 <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ kneeler_number               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ kneeler_id                   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ kneeler_position             <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ interceptor_name             <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ interceptor_number           <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ interceptor_id               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    $ interceptor_position         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…

    # A tibble: 148 × 6
       game                cfl_game_id play_id play_number team_drive play_of_drive
       <chr>                     <dbl> <chr>         <dbl>      <dbl>         <dbl>
     1 WEEK 14 - CGY @ EDM        6549 24-2             88         12             2
     2 WEEK 14 - CGY @ EDM        6549 1-3               4          1             3
     3 WEEK 14 - CGY @ EDM        6549 0-1               1          1             1
     4 WEEK 14 - CGY @ EDM        6549 1-1               2          1             1
     5 WEEK 14 - CGY @ EDM        6549 1-2               3          1             2
     6 WEEK 14 - CGY @ EDM        6549 1-4               5          1             4
     7 WEEK 14 - CGY @ EDM        6549 1-5               6          1             5
     8 WEEK 14 - CGY @ EDM        6549 1-6               7          1             6
     9 WEEK 14 - CGY @ EDM        6549 1-7               8          1             7
    10 WEEK 14 - CGY @ EDM        6549 1-8               9          1             8
    # ℹ 138 more rows

The size is small since this is one of 80 or so games I will be
combining in the future. Thankfully the game id and name is indicated in
the dataset for each game so not as much of a headache is caused.

## 2.3: Investigated and rejected sources

CFL Talk: PDFs were too time-consuming to extract data from, 15 page
documents for each individual game with lots of buttons and dropdowns to
press. Checked it out because it had up-to-date information but the info
I can get elsewhere will do the job for this kind of work studying a
general decision instead of game or player trends.

CFL API: Had problems documented online about moving APIs in 2023 and
paywalls blocked in-depth data. No direct structured access to the new
API could be established in an easy way. Checked it out because it is
direct from the source and APIs have lots of potential to be helpful.

## 2.4: What I could not find

I could not find a full CSV collection for CFLcharts for the 2025 season
and no bulk CSV download as that part of the site is “under
construction” or something; i.e. likely abandoned. Explicit data license
was also not found, and specifics on what the EP model within the data
is.

------------------------------------------------------------------------

# 3: Licensing and permissions

## 3.1: Licence by source

| Source    | Licence            | Attribution_required | Attribution_given    |
|:----------|:-------------------|:---------------------|:---------------------|
| CFLcharts | CFL’s terms of use | Not specified        | Yes, source credited |

## 3.2: Unresolved licensing

I was unable to find a direct license for CFLcharts or the actual CFL
API. I looked through the ‘about’, ‘updates’ and ‘raw data’ sections on
the website, as well as every other tab and individual game sheet within
the website. I looked outward and found the CFL terms of use, which
allow use of their website contents for individual non-commercial and
informational purposes only. It’s unknown if any attribution is required
but the site will be credited as well as where the data was derived
from, as CFLcharts states “All data on CFLCharts.ca is sourced from the
CFL’s public facing API”.

## 3.3: Downstream permissions

No open license offered for the combined (combining data for each game)
dataset, due to unclear third-party redistribution rights. I can still
offer a license for my code and written explanations. I can offer an MIT
License for my data scripts. I can offer a CC BY type of license for
open access to my analysis work.

------------------------------------------------------------------------

# 4: Consent and identifiability

The statistics being used are public professional sports statistics,
including information about clubs and players that are publicly
identified in news publications and all other kinds of media. No private
information is collected directly from any of the participants, all
information is extracted live in front of crowds.

------------------------------------------------------------------------

# 5: Exclusions and harms

## 5.1: Excluded data from the audit

Exclusions will only include a chunk of the 2025 season because of it
not existing on the website. In turning the raw game datasets into one
big table, there isn’t any information at the moment that looks like it
will need to be removed. Keeping the extra info will insure that if the
EP and EPA statistics aren’t figured out or don’t prove useful, new
statistics can be derived from the play data. The exclusion of part of
the 2025 season could possibly impact the data by thinking of maybe
teams started to make different decisions in situations as the season
progressed over time and coaches got more comfortable or had more data
to refer back to. Including the 2024 season as well ensures that there
is a large sample size but also that atleast one full season cycle is
accounted for in the case of possible changes over a season in strategy.

## 5.2: Who could be harmed

An inaccurate model or inaccurate results could paint players, coaches,
clubs etc in bad lights and on a larger scale (if I were a highly
accredited journalist or publication), jobs or contract terms could be
impacted in both good and bad ways. Coaching decisions could be
influenced in a misguiding way if outcome is faulty. Teams at lower
levels and different leagues could also falsely apply conclusions to
their own games and possibly earn negative game outcomes that impact
athletes and staff.

## 5.3: Unreleased working data

I wouldn’t exclude any working data if I didn’t have to; i think it’s a
fairly important process of data transparency and organization to have
raw script and data in your project files. I did an independent project
where I gitignored a large raw data file because it was in the hundreds
of megabytes and sometimes it’s not super necessary if data wasn’t
excessively altered. In reference to that project I think I only added
2-3 columns to the original csv.

------------------------------------------------------------------------

# 6: Data Stewardship

**Where it lives.** A repository on github. If I like how my project
looks, I’ll likely add it to my public group of projects with some
modifications to prove that I am capable of some solid data analysis and
coding work with reasonable AI help. I imagine it’ll also be nice to
look back on if I continue down my career path.

**Who maintains it.** Likely nobody, unless I find a new passion in this
final project and decide to add seasons and add more games as the league
moves forward.

**Formats and dependencies.** In 2036, it’s likely that the website
hosting the original data would have been down for years, and maybe
markdown files or R itself could be out of date formats. I’m likely not
using some complex packages unless I go through with a complex dashboard
for data visualization.

**Lifespan.** In sports, the timelines can get real messy. I think I
wouldn’t use 2023 season data or earlier, so the lifespan of conclusions
from 2024-2025 would probably only stretch until 2027-2028 until it
starts to be questioned. Or even earlier if there’s a big revolution in
play style or decision-making tendencies.

------------------------------------------------------------------------

# 7: Use of AI

\[State plainly whether you have used AI tools on this project.

Your `AI-LOG.md` will live in this repository and is committed alongside
the work it describes. Do not reproduce it here, but use a link such as
`/log/AI-LOG.md` to point to it within your final project directory:\]

**AI log:** `AI-LOG.md` \[— maintained from \[starting date\] and
committed alongside each stage of work.\]

\[One short paragraph summarizing your pattern of AI use (if any) so
far: which stages, what for, etc. State the model you are using, such as
ChatGPT or Claude. If you are continuing to chat to a Gemeni search
agent after looking something up, that counts too! If you have not used
AI tools at all, say so here and make sure `AI-LOG.md` says the same.\]

\[**Reminder: the text in this document must be written in your own
words.**\]

------------------------------------------------------------------------

# 8: Session information

    R version 4.5.2 (2025-10-31)
    Platform: aarch64-apple-darwin20
    Running under: macOS Sonoma 14.5

    Matrix products: default
    BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
    LAPACK: /Library/Frameworks/R.framework/Versions/4.5-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

    locale:
    [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

    time zone: America/Moncton
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] lubridate_1.9.4 forcats_1.0.1   stringr_1.6.0   dplyr_1.1.4    
     [5] purrr_1.2.0     readr_2.1.6     tidyr_1.3.2     tibble_3.3.0   
     [9] ggplot2_4.0.1   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] bit_4.6.0          gtable_0.3.6       jsonlite_2.0.0     crayon_1.5.3      
     [5] compiler_4.5.2     tidyselect_1.2.1   parallel_4.5.2     scales_1.4.0      
     [9] yaml_2.3.12        fastmap_1.2.0      R6_2.6.1           generics_0.1.4    
    [13] knitr_1.51         pillar_1.11.1      RColorBrewer_1.1-3 tzdb_0.5.0        
    [17] rlang_1.3.0        utf8_1.2.6         stringi_1.8.7      xfun_0.55         
    [21] S7_0.2.1           bit64_4.6.0-1      otel_0.2.0         timechange_0.3.0  
    [25] cli_3.6.5          withr_3.0.2        magrittr_2.0.4     digest_0.6.39     
    [29] grid_4.5.2         vroom_1.6.7        rstudioapi_0.17.1  hms_1.1.4         
    [33] lifecycle_1.0.5    vctrs_0.6.5        evaluate_1.0.5     glue_1.8.0        
    [37] farver_2.1.2       rmarkdown_2.30     tools_4.5.2        pkgconfig_2.0.3   
    [41] htmltools_0.5.9   

<!--
BEFORE YOU SUBMIT
&#10;- Does your file render from a clean session (wiping the environment and history with no errors?
- Are all paths relative? No setwd(), no C:/Users/yourname/
- Is every package you used declared in the setup chunk?
- Is AI-LOG.md committed and current?
- Could a stranger read this and know what you are hoping to do in your project, what your data is, where it came
  from, and what others are allowed to do with it?
- Have you deleted every bracketed prompt including this comment block?
-->
