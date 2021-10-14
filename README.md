# A2 - Bias in Data
## data-512-a2
## Laura Thriftwood

### Purpose

The goal of this assignment is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from various countries. I combine a dataset of Wikipedia articles with a dataset of country populations and use a machine learning service called ORES to estimate the quality of each article.
I then perform an analysis of how the coverage of politicians on Wikipedia and the quality of articles about politicians varies between countries. 

This analysis consists of a series of tables that show:
- the countries with the greatest and least coverage of politicians on Wikipedia compared to their population.
- the countries with the highest and lowest proportion of high quality articles about politicians.
- a ranking of geographic regions by articles-per-person and proportion of high quality articles.

### Source data and licenses

The Wikipedia politicians by country dataset can be found on Figshare at https://figshare.com/articles/Untitled_Item/5513449
The file was downloaded and unzipped to extract the data file called __page_data.csv__. 
License: CC by 4.0 https://creativecommons.org/licenses/by/4.0/

The population data is available in CSV format as __WPDS_2020_data.csv__ and is drawn from the world population data sheet published by the Population Reference Bureau at https://www.prb.org/international/indicator/population/table/

### API documentation

ORES GitHub repository: https://github.com/wikimedia/ores
ORES Documentation: https://www.mediawiki.org/wiki/ORES
ORES API Documentation: https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model

### Important notes about the data

- There are 6 score categories for Wikipedia articles

  - FA: Featured article
  - GA: Good article
  - B: B-class article
  - C: C-class article
  - Start: Start-class article
  - Stub: Stub-class article

- This analysis is limited to English Wikipedia pages only
- for each article (identified by rev_id), the ORES API returns a prediction probability for each of the six score categories. This analysis only uses the "prediction" which is the highest predicted score category.
-  Where no prediction was available, the API returns an error. In this analysis, the return of an error was interpreted to be No_Score and was removed from the dataset. The list of these articles is available in the output file __wp_wpds_politicians_no_score.csv__
-  There is a subset of the data where the country names in the __page_data.csv__ and __WPDS_2020_data.csv__ do not match. In this analysis, these unmatched entries were removed from the dataset. The list of these entries is available in the output file __wp_wpds_countries-no_match.csv__. 

### Final output data files includes the following fields:

__wp_wpds_politicians_by_country.csv__
- country
- article_name
- revision_id
- article_quality_est
- population

__wp_wpds_countries-no_match.csv__
- page
- country
- rev_id
- prediction
- FIPS
- Name
- Type
- TimeFrame
- Data (M)
- Population
- Sub_Region

__wp_wpds_politicians_no_score.csv__
- page
- country
- rev_id
- prediction

### Reflection 
This reflection focuses on the findings from this analysis and the process through which those findings were reached to help understand the causes and consequences of biased data in large, complex data science projects. A copy of this reflection is included at the end of the notebook. 

_What biases did you expect to find in the data (before you started working with it), and why?_

When considering geographic regions, I strongly suspected that there would be a bias regarding the “coverage” (number of articles as a proportion of population) in favor of countries in North America, and specifically the United States when broken down by country. This assumption was simply because our analysis would use English Wikipedia pages so there would exist an overrepresentation of articles about politicians from primarily English-speaking countries in North America. Regarding the “relative quality” assessment, I suspected a negative bias toward countries in Africa based on the overwhelming prevalence of anti-black bias in the world that would affect the amount attention paid to articles written about politicians in African countries which would reduce the quality ratings.

_What (potential) sources of bias did you discover in the course of your data processing and analysis?_

I was initially surprised to see that North Korea was the highest-ranked country in terms of relative quality of articles about its politicians. After some reflection, I concluded that the relative quality was likely an indicator of the amount of news/media attention paid to politicians in that country. This attention wouldn't necessarily need to be positive, more likely it would be born of an abundance unrest or turmoil the country experienced. This theory is supported by other entries in the top 10 countries in terms of the relative proportion of politician articles that are of GA and FA-quality (Table 3) such as Saudi Arabia and the Central African Republic.

_What might your results suggest about the internet and global society in general?_

These results suggest that politicians from countries that dominate global news coverage generate more interest in the form of Wikipedia contributions to their articles. A larger volume of contributions forces a higher degree of scrutiny of the contents of the article by other contributors, editors, and Wikipedia itself which will likely increase the overall quality ratings.

_How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?_

I think the most impactful supplement to this dataset would be to include an analysis of Wikipedia articles from non-English speaking pages. As this would obviously result in multiple conflicting quality predictions for the same politicians, there would need to be weights assigned to each of the quality ratings and then aggregated into a single metric for each country. This would normalize the data and allow for a better global comparison between countries and regions, removing the bias introduced by the English language restriction in this analysis. It would also potentially uncover other language-specific biases through comparison of predicted ratings for the same countries between language pages.
