Ground Level: Labor and Population Change in Seven West Virginia Coal Counties

1. Introduction

The decline of the coal mining industry has created a serious challenge for regions that rely on the sector for employment and economic stability. West Virginia is a particularly useful setting for studying this kind of regional change, since coal has been at the heart of the state’s economy and identity for more than a century.

This project examines seven West Virginia counties selected through defined inclusion criteria and investigates whether they experienced similar changes as mining employment began to decline, using indicators drawn from publicly available sources. It compares mining employment, labor-market, and demographic trends across counties where mining accounted for a meaningful share of employment in 2011.

2. Data and Approach

The analysis is based on three public datasets. Data on mining employment were collected from the Mine Safety and Health Administration's MSHA Database, labor-force and employment data at the county level from the Bureau of Labor Statistics' Local Area Unemployment Statistics (LAUS) program, and population and age estimates were collected from the U.S. Census Bureau's American Community Survey (ACS) 5-year estimates.MSHA records were originally reported at the mine level and were later aggregated to annual county-level mining employment totals after removing inactive mines and facilities with zero production. BLS annual labor-force, employment, unemployment, and unemployment-rate estimates were compiled for West Virginia counties. ACS estimates were utilized to measure population and demographic change, including changes in the working-age and older populations.

Data Processing

Data processing was done in two stages. In Python, the source files were cleaned, standardized, limited to West Virginia counties and 2000–2024, and merged by county and year. Mine employment was averaged across reporting quarters. Derived measures such as working-age population, older population, labor-force participation, and population outside the labor force were then calculated, and the results were exported as CSV files.

In Power BI, those files were loaded and used to build the measures, tables, charts, map, and scatterplot for the county comparisons.

County Selection

Seven counties were selected using two criteria. First, mining employment had to represent at least 10 percent of total county employment in 2011. Second, more than 200 workers had to be employed in mining that year. The 10 percent threshold identifies counties where mining accounts for a significant portion of the local labor market. The 200-worker threshold, in contrast, prevents very small labor markets from showing inflated dependence figures based on only a few mining jobs. The resulting sample is intentionally limited to counties with significant baseline mining dependence and a meaningful level of mining employment, and it's not a representation of all West Virginia counties.

Reference Year

The analysis covers 2000–2024, with particular attention to the period after 2011. 2011 is used as the common reference point because statewide West Virginia mining employment reached its highest observed level that year. It is an analytical reference point and not a universal starting point for the decline. A common statewide reference year makes it possible to compare how counties that entered the post-peak period with substantial mining dependence went on to fare.

3. Mining Employment Declined, but County Trajectories Differed

West Virginia mining employment increased for much of the 2000s and peaked in 2011. After that, employment entered a sustained period of decline before stabilizing at a level much below the peak. By 2024, statewide mining employment had fallen by approximately 46 percent compared with 2011. The decline wasn’t uniform across the seven counties. Several, including Boone, Mingo, and Webster, reached their own highest mining employment levels before 2011, while others peaked closer to or after the statewide high. Boone County experienced the largest percentage decline from its own peak, falling from 3,913 mining workers in 2008 to 623 in 2024. Given its large initial mining workforce, Boone also accounted for a substantial share of the total mining employment decline among the seven counties.

See Figure 1: Statewide mining employment, 2000–2024
See Figure 2: Study counties
See Figure 3: County-level mining employment trajectories
See Table 1: County mining employment changes

4. Counties Experienced Different Labor-Market and Demographic Changes

Although all seven counties experienced changes after 2011, the combination of labor-market and demographic shifts varied. McDowell recorded the highest value on the exploratory composite indicator, with a score of 86, and experienced particularly large changes in labor-force exit and the employment-to-population ratio. Mingo also experienced substantial change, including pronounced demographic aging. Wyoming, Boone, and Webster occupied a middle range, with scores of 70, 67, and 63, respectively, while Logan and Marshall recorded lower composite values of 52 and 48 within this particular sample.

Logan and McDowell make for a useful comparison here. Their mining employment shares in 2011 were relatively similar, at approximately 18.0 percent and 20.5 percent, respectively, but their subsequent labor-market and demographic changes looked quite different. This comparison shows that the level of mining employment dependence in 2011 does not, by itself, describe how a county changed afterward. The analysis therefore treats baseline mining dependence as a measure of structural exposure, separate from the labor-market and demographic indicators used to describe change. Baseline mining dependence, subsequent declines in mining employment, and change are related but distinct dimensions of county experience, and the analysis treats them separately.

See Figure 4: 2011 mining employment dependence and subsequent change.

5. Exploratory Composite Indicator

To compare change across the seven counties, this analysis uses a simple exploratory socioeconomic change indicator. The indicator combines selected labor-market and demographic measures covering changes between 2011 and 2024. The labor-market measures capture changes such as labor-force participation and the employment-to-population ratio, while the demographic measures capture changes such as population decline and population aging. Each indicator is oriented so that higher values represent greater change. Because the measures use different units, each is converted to a common 0–1 scale using min-max normalization:

Normalized value = (County value - Minimum value) / (Maximum value - Minimum value)

Here, the minimum and maximum values are calculated across the seven study counties for each indicator. After normalization, the labor-market indicators are averaged into a Labor Change Score, and the demographic indicators are averaged into a Demographic Change Score. The overall indicator is then:

Composite Change Score = ((Labor Change Score + Demographic Change Score) / 2) × 100

Labor-market and demographic dimensions receive equal weight, a choice made for transparency rather than because it represents a theoretically preferred weighting scheme. The resulting scores are relative to the seven counties in this analysis. A score of 86, for example, does not mean a county experienced 86 percent socioeconomic change. It means the county ranks relatively high on the selected measures within this particular seven-county comparison. The indicator is therefore best understood as a tool for comparing multidimensional change, not as a validated measure of overall socioeconomic conditions. Mining employment decline is kept separate from the composite indicator. This prevents the analysis from using the loss of mining jobs both as the measure of industrial decline and as part of the outcomes used to assess county change.

6. Limitations

This analysis has several limitations. It focuses on only seven counties that met the selection criteria, so the findings describe variation among counties with substantial baseline mining dependence and shouldn’t be read as representative of all West Virginia counties or coal-producing communities more broadly. The analysis is also descriptive and doesn’t claim causality. Plenty of other factors could have shaped county outcomes – industrial diversification, infrastructure, education, healthcare, migration, local fiscal conditions – and none of these are part of the analysis. The sample is too small for statistical inference. With only seven counties, the analysis doesn’t estimate regression relationships or treat the observed differences as statistically generalizable to a larger population.

Some labor-market data were also unavailable for certain county-years. Missing observations were treated as unavailable rather than zero and excluded from calculations requiring those observations; if the missingness is systematically tied to particular counties or years, that could affect the results. Finally, the composite indicator depends on the specific measures, normalization method, and equal-weighting scheme used here. Because each indicator is normalized against the seven-county sample, the scores are relative rather than absolute. They shouldn’t be read as measures of overall county well-being or compared directly with other regions.

7. Potential Policy Implications

The differences across the seven counties suggest that policies addressing coal decline shouldn’t lean solely on historical mining dependence as representative of community need. Counties with substantial and sometimes similar levels of mining dependence went through different combinations of labor-market and demographic change, which points to local conditions shaping the effects of industrial decline. A more targeted approach could weigh multiple dimensions of county conditions alongside mining employment – labor-force participation, employment-to-population ratios, population change, demographic aging. A community facing substantial labor-force disengagement, for instance, likely needs a different response than one where the main pressure is population loss or demographic aging. In other words, economic-transition policy may work better when it responds to the specific mix of challenges each community faces, rather than applying one approach across the board.

The analysis doesn’t identify which specific policies would work better, and it doesn’t establish why counties differed. The findings are better read as a case for more differentiated policy attention than as an evaluation of any particular intervention.

8. Conclusion

Mining employment in West Virginia fell by roughly 46 percent between the 2011 statewide peak and 2024, but the seven counties examined here did not move together. Boone lost the largest share of its mining workforce from its own peak, yet landed in the middle of the composite ranking, while McDowell showed the greatest overall change. Logan and McDowell, with similar mining dependence in 2011, still scored 52 and 86. Dependence on mining, then, does not by itself describe how a county changed afterward.

The analysis is descriptive, covers only seven counties, and relies on a relative composite indicator, so it can't explain why the observed differences emerged. Future work could look at different local factors, such as industrial diversification, healthcare, education, infrastructure, and migration, to see what separates counties like Logan and McDowell. It could also test whether the same patterns hold across a larger set of coal-dependent counties and under different indicators or weighting schemes. Answering those questions would require broader samples and methods suited to testing explanations, which this analysis does not attempt.

9. Sources

Mine Safety and Health Administration. (2024). Mine Employment and Coal Production Database. U.S. Department of Labor.

U.S. Bureau of Labor Statistics. (2024). Local Area Unemployment Statistics. U.S. Department of Labor.

U.S. Census Bureau. (2024). American Community Survey 5-year estimates, Table S0101: Age and Sex. U.S. Department of Commerce.
