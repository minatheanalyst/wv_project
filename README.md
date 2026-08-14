README

Regional Vulnerability Following Industrial Decline

An exploratory analysis of mining, labor-market, and demographic change in West Virginia, 2011–2024

1. Introduction

The decline of the coal mining industry has created major challenges for communities that depended on mining for employment and economic stability. West Virginia provides a particularly useful setting for examining these changes. Coal has shaped the state's economy and identity for more than a century, particularly in the Southern Appalachian coalfields. Mining employment peaked in 2011 before entering a sustained decline and stabilizing at a level well below its peak.

This project started as an exploratory look at whether counties with substantial mining employment experienced similar changes as mining employment began to decline. I focus on seven West Virginia counties where mining accounted for a substantial share of employment in 2011 and compare their mining employment, labor-market, and demographic trends through 2024.

Baseline mining dependence, subsequent mining employment decline, and change are related but distinct dimensions of county experience. A county can lose a large share of its mining jobs without necessarily experiencing the same labor-market and demographic shifts as another county that started with a similar level of mining dependence.

The analysis is informed by a simple post-industrial adjustment perspective: communities with greater dependence on a declining industry may experience greater disruption, but their subsequent changes may differ depending on local economic and demographic conditions. The analysis is descriptive. It doesn't claim causality because the study covers only seven counties and uses observational data, making it difficult to separate the effects of mining decline from other factors that may have shaped these communities. It looks specifically at variation among the seven exposed counties within West Virginia.

2. Data and Approach

The analysis uses three public datasets:

Mining employment data from the Mine Safety and Health Administration's (MSHA) Mine Employment and Coal Production Database.

County-level labor-force and employment data from the Bureau of Labor Statistics' (BLS) Local Area Unemployment Statistics (LAUS) program.

Population and age estimates from the U.S. Census Bureau's American Community Survey (ACS) 5-year estimates.

The workflow has two main stages:

Python is used for source-data cleaning, filtering, aggregation, merging, and preparation of county-year datasets.

Power BI is used for the final data model, DAX measures, visualization, and comparative analysis.

MSHA mine-level records were aggregated to annual county-level mining employment totals after removing inactive mines and facilities with zero production. BLS annual labor-force, employment, unemployment, and unemployment-rate estimates were compiled for West Virginia counties. Missing county-year observations were treated as unavailable rather than zero. ACS estimates were used to measure population and demographic change, including changes in the working-age and older populations.

County Selection

Seven counties were selected using two criteria: mining employment had to represent at least 10 percent of total county employment in 2011, and more than 200 workers had to be employed in mining that year.

The employment-share threshold identifies counties where mining made up a substantial part of the local labor market. The 200-worker threshold helps avoid cases where a small number of mining jobs could make mining appear disproportionately important to the local labor market.

The resulting sample is intentionally limited to counties with substantial baseline mining dependence and a meaningful level of mining employment. It isn't meant to represent all West Virginia counties.

Reference Year

The analysis covers 2000–2024, with particular attention to the period after 2011.

2011 is used as the common reference point because statewide West Virginia mining employment reached its highest observed level that year. That's a statewide baseline, not a claim that every county hit its own individual peak in 2011. Several counties reached their own mining employment peaks earlier or later, and the county-level tables and charts throughout this project treat that separately from the statewide reference year.

3. Project Structure

The project follows a simple workflow from source data to final visualization:

source data to Python processing to processed CSV files to Power BI model to dashboard

The project is organized as follows:

project
  data
    raw
      mining
      labor
      demo
    processed
  python
    01_labor_demo.py.ipynb
    02_mining.py.ipynb
  powerbi
    WV_dashboard
    WV_static.pdf
  figma
    dashboard design and visual assets
  README.txt

The raw folder contains the original source data, organized into mining, labor-market, and demographic data. The processed folder contains the county-year datasets prepared for analysis and loaded into Power BI. The python folder contains the data-processing notebooks, while powerbi contains the dashboard and static PDF version. The figma folder contains the design work used for the dashboard layout and visual elements.

4. Python Data Processing

Python is used for data preparation, transformation, and construction of the analytical dataset. Final visualization and presentation are handled in Power BI.

The processing workflow:

1. Loads the public source datasets.
2. Cleans and standardizes county, year, and employment fields.
3. Removes inactive MSHA mines and facilities with zero production.
4. Aggregates mine-level employment to annual county-level mining employment.
5. Compiles annual county-level BLS labor-force, employment, unemployment, and unemployment-rate estimates.
6. Incorporates ACS population and demographic estimates.
7. Merges the county-year datasets using county and year as the common structure.
8. Treats missing county-year observations as unavailable rather than zero.
9. Calculates the variables needed for the county comparisons and Power BI measures.
10. Exports processed CSV files for use in Power BI.

The Python stage establishes the analytical dataset and handles the transformations needed to make the three source systems comparable at the county-year level.

5. Power BI Visualization and Analysis

The processed CSV files are loaded into Power BI, which handles the final visualization and comparative analysis. Measures are created for mining employment change, mining employment dependence, labor-market change, demographic change, and the exploratory composite indicator.

The dashboard uses trend charts, a map, tables, and a scatterplot, arranged in reading order so the reader moves from statewide context, to the study counties, to county-specific mining trajectories, and then to the labor-market and demographic comparison.

Dashboard Visualization Order

1. Statewide mining employment trend, 2000–2024 — establishes the statewide context and shows the 2011 peak and subsequent decline, using the full timeline to preserve historical context.

2. Study-county map — shows the seven selected counties geographically, with tooltips displaying 2011 mining employment and mining employment share. The map tooltip translates the share into something more intuitive: alongside the percentage, it shows an approximate worker ratio (e.g., "≈ 1 in 5 workers in coal"), which reads more naturally than a raw percentage when scanning the map.

3. County mining employment trajectories, 2000–2024 — compares mining employment trends across the seven counties, making differences in timing, scale, and persistence of decline visible.

4. Individual county mining peak and change table — shows each county's own mining employment peak year, peak mining employment, latest available mining employment, and percentage decline from that county's own peak, separate from the common 2011 reference year.

5. 2011 mining employment dependence vs. change score scatterplot — compares baseline mining employment dependence in 2011 with the exploratory composite change score. This is descriptive only; with seven counties the sample is too small to support predictive modeling.

6. Labor-market and demographic indicator breakdown — shows the component indicators behind the composite comparison, so the reader can see which dimensions contribute to differences between counties rather than relying only on the overall score.

6. Design and Visual Development

The visual design of the project was developed separately in Figma. The dashboard layout, visual hierarchy, typography, icons, and supporting graphic elements were designed in Figma and then incorporated into the final presentation.

Figma was used to develop the overall visual structure and individual design elements, while Power BI handles the analytical charts, tables, map, scatterplot, and interactive components.

7. Mining Employment Measures

The statewide and county mining employment trend sums mining employment by year, and the trend chart shows the full 2000–2024 timeline so the 2011 statewide reference point is visible in context.

For the 2011 county table, mining employment is filtered to that single year and expressed as a share of total county employment — the measure used to describe how central mining was to each county's labor market at the common baseline.

The map tooltip translates that share into something more intuitive: alongside the percentage, it shows an approximate worker ratio (e.g., "≈ 1 in 5 workers in coal"), which reads more naturally than a raw percentage when scanning the map.

8. Individual County Mining Peaks

The county-level table uses each county's own mining employment history rather than assuming that 2011 was the peak for every county — it identifies each county's highest recorded mining employment year and compares that peak to the latest available figure to get a percent decline.

9. Labor-Market and Demographic Change

All outcome indicators use 2011 as the common baseline reference year, and the analysis considers changes in labor-market and demographic conditions between 2011 and the latest available year in each dataset. Examples include:

Employment-to-population ratio change.

Labor-force exit / not-in-labor-force change.

Population change.

Older-population change.

All indicators are oriented so that higher values represent greater change in the direction being measured — a decline in employment-to-population ratio and a decline in population, for instance, are both flipped so that "more change" always points the same way. Population change specifically is calculated from the 2011 baseline to the latest year available in the ACS data.

10. Exploratory Composite Indicator

To compare change across the seven counties, I built a simple exploratory socioeconomic change indicator.

The indicator combines selected labor-market and demographic measures covering changes between 2011 and the latest available year. The labor-market measures capture changes such as labor-force participation and the employment-to-population ratio, while the demographic measures capture changes such as population decline and population aging.

Each indicator is oriented so that higher values represent greater change. Because the measures use different units, each is converted to a common 0–1 scale using min-max normalization:

Normalized value = (County value - Minimum value) / (Maximum value - Minimum value)

The minimum and maximum values are calculated across the seven study counties for each indicator. After normalization, the labor-market indicators are averaged into a Labor Change Score, and the demographic indicators are averaged into a Demographic Change Score. The overall indicator is:

Composite Change Score = ((Labor Change Score + Demographic Change Score) / 2) x 100

Labor-market and demographic dimensions receive equal weight, a choice made for transparency rather than because it represents a theoretically preferred weighting scheme.

The resulting scores are relative to the seven counties in this analysis. A score of 86, for example, doesn't mean a county experienced 86 percent socioeconomic change — it means the county ranks relatively high on the selected measures within this particular seven-county comparison. The indicator is best understood as a tool for comparing multidimensional change, not as a validated measure of overall socioeconomic conditions.

Mining employment decline is kept separate from the composite indicator. This prevents the analysis from using the loss of mining jobs both as the measure of industrial decline and as part of the outcomes used to assess county change.

11. Findings

Mining Employment Declined, but County Trajectories Differed

West Virginia mining employment increased for much of the 2000s and peaked in 2011. After that, employment entered a sustained period of decline before stabilizing at a level much below the peak. By 2024, statewide mining employment had fallen by approximately 46 percent compared with 2011.

The decline wasn't uniform across the seven counties. Several, including Boone, Mingo, and Webster, reached their own highest mining employment levels before 2011, while others peaked closer to or after the statewide high.

Boone County experienced the largest percentage decline from its own peak, falling from 3,913 mining workers in 2008 to 623 in its latest available mining-employment observation. Given its large initial mining workforce, Boone also accounted for a substantial share of the total mining employment decline among the seven counties.

Counties Experienced Different Labor-Market and Demographic Changes

Although all seven counties experienced changes after 2011, the combination of labor-market and demographic shifts varied.

McDowell recorded the highest value on the exploratory composite indicator, with a score of 86, and experienced particularly large changes in labor-force exit and the employment-to-population ratio. Mingo also experienced substantial change, including pronounced demographic aging. Wyoming, Boone, and Webster occupied a middle range, with scores of 70, 67, and 63, respectively, while Logan and Marshall recorded lower composite values of 52 and 48 within this particular sample.

Logan and McDowell make for a useful comparison here. Their mining employment shares in 2011 were relatively similar, at approximately 18.0 percent and 20.5 percent, respectively, but their subsequent labor-market and demographic changes looked quite different.

This comparison shows that the level of mining employment dependence in 2011 does not, by itself, describe how a county changed afterward. The analysis therefore treats baseline mining dependence as a measure of structural exposure, separate from the labor-market and demographic indicators used to describe change.

12. Limitations

This analysis has several limitations worth noting.

It focuses on only seven counties that met the selection criteria, so the findings describe variation among counties with substantial baseline mining dependence and shouldn't be read as representative of all West Virginia counties or coal-producing communities more broadly.

The analysis is also descriptive. Plenty of other factors could have shaped county outcomes – industrial diversification, infrastructure, education, healthcare, migration, local fiscal conditions – and none of these are part of the analysis.

The sample is too small for statistical inference. With only seven counties, I don't estimate regression relationships or treat the observed differences as statistically generalizable to a larger population. The scatterplot is therefore descriptive and does not support future predictions.

Some labor-market data were also unavailable for certain county-years. Missing observations were treated as unavailable rather than zero and excluded from calculations requiring those observations; if the missingness is systematically tied to particular counties or years, that could affect the results.

Webster County has no mining-employment record for 2024 in the dataset used for this analysis. The mining-employment comparison therefore uses Webster County's latest available mining-employment observation rather than treating the missing 2024 value as zero. This is a data-availability limitation and should not be interpreted as evidence that Webster County had zero mining employment in 2024.

Finally, the composite indicator depends on the specific measures, normalization method, and equal-weighting scheme used here. Because each indicator is normalized against the seven-county sample, the scores are relative rather than absolute. They shouldn't be read as measures of overall county well-being or compared directly with other regions.

13. Potential Policy Implications

The differences across the seven counties suggest that policies addressing coal decline shouldn't lean solely on historical mining dependence as representative of community need. Counties with substantial and sometimes similar levels of mining dependence went through different combinations of labor-market and demographic change, which points to local conditions shaping the effects of industrial decline.

A more targeted approach could weigh multiple dimensions of county conditions alongside mining employment – labor-force participation, employment-to-population ratios, population change, demographic aging. A community facing substantial labor-force disengagement, for instance, likely needs a different response than one where the main pressure is population loss or demographic aging.

The analysis doesn't identify which specific policies would work better, and it doesn't establish why counties differed. The findings are better read as a case for more differentiated policy attention than as an evaluation of any particular intervention.

14. Conclusion

Mining employment in West Virginia declined substantially after the 2011 statewide peak, but the seven counties examined here didn't follow identical trajectories. They differed both in the timing and scale of their mining employment declines and in the labor-market and demographic changes that followed. Boone, for example, saw a particularly large decline in mining employment but didn't record the highest value on the composite indicator. At the same time, McDowell and Mingo experienced greater overall change on the measures used here.

The main finding, then, isn't that one county was universally better or worse off than another. It's that counties with substantial mining dependence experienced different patterns of change after the statewide mining employment peak — which is also why mining dependence, mining employment decline, and change are worth treating as separate dimensions rather than collapsing into one story.

15. Sources

Mine Safety and Health Administration. (2024). Mine Employment and Coal Production Database. U.S. Department of Labor.

U.S. Bureau of Labor Statistics. (2024). Local Area Unemployment Statistics. U.S. Department of Labor.

U.S. Census Bureau. (2024). American Community Survey 5-year estimates, Table S0101: Age and Sex. U.S. Department of Commerce.
