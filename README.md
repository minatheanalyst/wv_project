Regional Vulnerability Following Industrial Decline

An exploratory analysis of mining, labor-market, and demographic change in West Virginia, 2011–2024

1. Introduction

The decline of the coal mining industry has created major challenges for communities that depended on mining for employment and economic stability. West Virginia provides a particularly useful setting for examining these changes. Coal has shaped the state’s economy and identity for more than a century, particularly in the Southern Appalachian coalfields. Mining employment peaked in 2011 before entering a sustained decline and stabilizing at a level well below its peak.

This project started as an exploratory look at whether counties with substantial mining employment experienced similar changes as mining employment began to decline. I focus on seven West Virginia counties where mining accounted for a substantial share of employment in 2011 and compare their mining employment, labor market, and demographic trends through 2024.

Baseline mining dependence, subsequent mining employment decline, and change are related but distinct dimensions of county experience. A county can lose a large share of its mining jobs without necessarily experiencing the same labor-market and demographic shifts as another county that started with a similar level of mining dependence.

The analysis is descriptive. It doesn’t claim causality, and looks specifically at variation among the seven exposed counties within West Virginia.

---

2. Data and Approach

The analysis uses data from three public sources:

* Mining employment data from the Mine Safety and Health Administration’s (MSHA) Mine Employment and Coal Production Database.
* County-level labor-force and employment data from the Bureau of Labor Statistics’ (BLS) Local Area Unemployment Statistics (LAUS) program.
* Population and age estimates from the U.S. Census Bureau’s American Community Survey (ACS) 5-year estimates.

The workflow has two main stages:

1. Python is used for source data cleaning, filtering, aggregation, merging, and the preparation of county-year datasets.
2. Power BI is used for the final data model, DAX measures, visualization, and comparative analysis.

MSHA mine-level records were aggregated to annual county-level mining employment totals after removing inactive mines and facilities with zero production. BLS annual labor-force, employment, unemployment, and unemployment-rate estimates were compiled for West Virginia counties. Missing county-year observations were treated as unavailable rather than zero. ACS estimates were used to measure population and demographic change, including changes in the working-age and 65+ populations.

County Selection

Seven counties were selected using two criteria: mining employment had to represent at least 10 percent of total county employment in 2011, and more than 200 workers had to be employed in mining that year.

The employment-share threshold identifies counties in which mining accounted for a substantial share of the local labor market. The 200-worker threshold helps avoid cases where a small number of mining jobs could make mining appear disproportionately important to the local labor market.

The resulting sample is intentionally limited to counties with substantial baseline mining dependence and meaningful mining employment; that is, a specific subset of West Virginia’s counties.

Reference Year

The analysis covers 2000–2024, with particular attention to the period after 2011.

2011 is used as the common reference point because statewide West Virginia mining employment reached its highest observed level that year — a statewide baseline. Individual counties reached their own mining employment peaks at different times, and the county-level tables and charts throughout this project treat these separately from the statewide reference year.

---

3. Project Structure

The project follows a simple workflow from source data to final visualization:

project/
├── data/
│   ├── raw/
│   │   ├── MSHA mining employment data
│   │   ├── BLS LAUS county labor-market data
│   │   └── ACS 5-year population and demographic data
│   └── processed/
│       ├── processed county-year datasets
│       └── CSV files loaded into Power BI
├── python/
│   └── data processing and preparation scripts
├── powerbi/
│   └── Power BI dashboard / report
└── README.txt

---

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

---

5. Power BI Visualization and Analysis

The processed CSV files are loaded into Power BI for final visualization and comparative analysis. Measures are created for mining employment change, mining employment dependence, labor-market change, demographic change, and the exploratory composite indicator.

The dashboard is organized in reading order, moving from the statewide context to the selected counties, then to county-level mining trajectories and comparisons of labor-market and demographic change.

Visualization order:

1. Statewide mining employment trend, 2000–2024 — establishes the statewide context and shows the 2011 peak and subsequent decline, using the full timeline to preserve historical context.
2. Study-county map — shows the seven selected counties geographically, with tooltips displaying 2011 mining employment and mining employment share. ##??? The map tooltip rephrases the share intuitively for the reader. Alongside the percentage, it also shows an approximate worker ratio (e.g., “≈ 1 in 5 workers in coal”), which reads better than a raw percentage.
3. County mining employment trajectories, 2000–2024 — compares mining employment trends across the seven counties, making differences in timing, scale, and persistence of decline visible.
4. Individual county mining peak and change table — shows each county’s own mining employment peak year, peak mining employment, latest available mining employment, and percentage decline from that county’s own peak, separate from the common 2011 reference year.
5. 2011 mining employment dependence vs. change score scatterplot — compares baseline mining employment dependence in 2011 with the exploratory composite change score. This is descriptive only; with seven counties the sample is too small to support predictive modeling.
6. Labor-market and demographic indicator breakdown — shows the component indicators behind the composite comparison, so the reader can see which dimensions drive differences between counties rather than relying only on the overall score.

---

6. Mining Employment Measures

The statewide and county mining employment trend sums mining employment by year, and the trend chart shows the full 2000–2024 timeline so the 2011 statewide reference point is visible in context.

For the 2011 county table, mining employment is filtered to that single year and expressed as a share of total county employment — a measure used to describe how central mining was to each county’s labor market at the common baseline.

The map tooltip rephrases the share intuitively for the reader. Alongside the percentage, it also shows an approximate worker ratio (e.g., “≈ 1 in 5 workers in coal”), which reads better than a raw percentage.

---

7. Individual County Mining Peaks

The county-level table is built from each county’s own mining employment history: it identifies each county’s highest recorded mining employment year and compares that peak to the latest available figure to get a percent decline.

---

8. Labor-Market and Demographic Change

All outcome indicators use 2011 as the common baseline reference year, and the analysis considers changes in labor-market and demographic conditions between 2011 and the latest available year in each dataset. Examples include:

* Employment-to-population ratio change.
* Labor-force exit / not-in-labor-force change.
* Population change.
* Older-population change.

All indicators are oriented so that higher values represent greater change in the direction being measured — a decline in employment-to-population ratio and a decline in population, for instance, are both flipped so that “more change” always points the same way. Population change specifically is calculated from the 2011 baseline to the latest year available in the ACS data.

---

9. Exploratory Composite Indicator

To compare change across the seven counties, I built a simple exploratory socioeconomic change indicator.

The indicator combines selected labor-market and demographic measures covering changes between 2011 and the latest available year. The labor-market measures capture changes in labor-force participation and the employment-to-population ratio, while the demographic measures capture changes in population decline and aging.

Each indicator is oriented so that higher values represent greater change. Because the measures use different units, each is converted to a common 0–1 scale using min-max normalization:

Normalized value = (County value - Minimum value) / (Maximum value - Minimum value)

The minimum and maximum values are calculated across the seven study counties for each indicator. After normalization, the labor-market indicators are averaged into a Labor Change Score, and the demographic indicators are averaged into a Demographic Change Score. The overall indicator is:

Composite Change Score = ((Labor Change Score + Demographic Change Score) / 2) × 100

Labor-market and demographic dimensions receive equal weight, a choice made for transparency rather than because it represents a theoretically preferred weighting scheme.

The resulting scores are relative to the seven counties in this analysis. A score of 86, for example, shows where a county ranks on the selected measures within this particular seven-county comparison. The indicator is a tool for comparing multidimensional change, useful for ranking within this sample rather than as a validated measure of overall socioeconomic conditions.

Mining employment decline is kept separate from the composite indicator. This prevents the analysis from using the loss of mining jobs both as the measure of industrial decline and as part of the outcomes used to assess county change.

---

10. Findings

Mining Employment Declined, but County Trajectories Differed

West Virginia mining employment increased for much of the 2000s and peaked in 2011. After that, employment entered a sustained period of decline before stabilizing at a level much below the peak. By 2024, statewide mining employment had fallen by approximately 46 percent compared with 2011.

The decline wasn’t uniform across the seven counties. Several, including Boone, Mingo, and Webster, reached their own highest mining employment levels before 2011, while others peaked closer to or after the statewide high.

Boone County experienced the largest percentage decline from its own peak, falling from 3,913 mining workers in 2008 to 623 in its latest available mining-employment observation. Given its large initial mining workforce, Boone also accounted for a substantial share of the total mining employment decline among the seven counties.

Counties Experienced Different Labor-Market and Demographic Changes

Although all seven counties experienced changes after 2011, the combination of labor-market and demographic shifts varied.

McDowell recorded the highest value on the exploratory composite indicator, with a score of 86, and experienced particularly large changes in labor-force exit and the employment-to-population ratio. Mingo also experienced substantial change, including pronounced demographic aging. Wyoming, Boone, and Webster occupied a middle range, with scores of 70, 67, and 63, respectively, while Logan and Marshall recorded lower composite scores of 52 and 48 in this sample.

Logan and McDowell make for a useful comparison here. Their mining employment shares in 2011 were relatively similar, at approximately 18.0 percent and 20.5 percent, respectively, but their subsequent labor-market and demographic changes looked quite different.

This comparison shows that the level of mining employment dependence in 2011 does not, by itself, describe how a county changed afterward. The analysis therefore treats baseline mining dependence as a measure of structural exposure, separate from the labor-market and demographic indicators used to describe change.

---

11. Limitations

This analysis has several limitations.

It focuses on only seven counties that met the selection criteria, so the findings describe variation within that specific group of counties with substantial baseline mining dependence.

The analysis is also descriptive. Plenty of other factors could have shaped county outcomes – industrial diversification, infrastructure, education, healthcare, migration, local fiscal conditions – and none of these are part of the analysis.

The sample is too small for statistical inference. With only seven counties, I don’t estimate regression relationships or treat the observed differences as statistically generalizable to a larger population. The scatterplot is therefore descriptive and does not support future predictions.

Some labor-market data were also unavailable for certain county-year combinations. These missing observations were treated as unavailable rather than zero and excluded from calculations requiring those observations; if the missingness is systematically tied to particular counties or years, that could affect the results.

Webster County has no records of mining employment for 2024 in the dataset used for this analysis. The comparison therefore uses Webster County’s latest available mining-employment observation (2023) — a data-availability gap, not evidence that Webster County had zero mining employment in 2024. Treating the missing 2024 value as zero would have inflated the county’s mining employment decline to 100 percent.

Finally, the composite indicator depends on the specific measures, normalization method, and equal-weighting scheme used here. Because each indicator is normalized against the seven-county sample, the scores are relative rather than absolute — useful for comparing within this group, not for judging overall county well-being or comparing directly with other regions.

---

12. Potential Policy Implications

The differences across the seven counties suggest that policies addressing coal decline shouldn’t rely solely on historical dependence on mining as a proxy for community need. Counties with substantial and sometimes similar levels of mining dependence went through different combinations of labor-market and demographic change, which points to local conditions shaping the effects of industrial decline.

A targeted approach could weigh multiple dimensions of county conditions alongside mining employment – labor-force participation, employment-to-population ratios, population change, demographic aging. A community facing substantial labor-force disengagement, for instance, likely needs a different response than one facing population loss or demographic aging as the main pressure.

The findings make a case for more differentiated policy attention — figuring out which specific policies would work, or why counties differed, is outside the scope of this analysis.

---

13. Conclusion

Mining employment in West Virginia declined substantially after the 2011 statewide peak, but the seven counties examined here didn’t follow identical trajectories. They differed both in the timing and scale of their mining employment declines and in the labor-market and demographic changes that followed. Boone, for example, saw a particularly large decline in mining employment but didn’t record the highest value on the composite indicator. At the same time, McDowell and Mingo experienced greater overall change on the measures used here.

Counties with substantial mining dependence experienced different patterns of change after the statewide mining employment peak, and no single county was uniformly better or worse off. That’s also why mining dependence, mining employment decline, and change are worth treating as separate dimensions here.

---

14. Sources

Mine Safety and Health Administration. (2024). Mine Employment and Coal Production Database. U.S. Department of Labor.

U.S. Bureau of Labor Statistics. (2024). Local Area Unemployment Statistics. U.S. Department of Labor.

U.S. Census Bureau. (2024). American Community Survey 5-year estimates, Table S0101: Age and Sex. U.S. Department of Commerce.
