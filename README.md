# A2 - Bias in Data
## data-512-a2
## Laura Thriftwood

### Purpose

The goal of this assignment is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries. I combine a dataset of Wikipedia articles with a dataset of country populations, and use a machine learning service called ORES to estimate the quality of each article.
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

### Reflection 
This reflection focuses on the findings from this analysis and the process through which those findings were reached to help understand the causes and consequences of biased data in large, complex data science projects. A copy of this reflection is included at the end of the notebook. 

### Final data file includes the following fields:
