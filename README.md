![Language](https://img.shields.io/badge/language-python-blue.svg)
[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/pragyy/Data-512-homework_2/blob/main/LICENSE)
![contributors](https://img.shields.io/github/contributors/pragyy/Data-512-homework_2.svg) 
![codesize](https://img.shields.io/github/languages/code-size/pragyy/Data-512-homework_2.svg) 

# Identifying bias in the politicians' Wikipedia articles

## Project Overview
The aim of this project is to explore the concept of bias in data using Wikipedia articles. The articles on political figures from different countries is combined with a dataset of country populations, and use a machine learning service called ORES to estimate the quality of each article. Then further use this generated dataset to perform analysis that answers questions like highest and lowest article coverage, highest and lowest proportion of high quality articles, and ranking of geographic regions by articles-per-person and proportion of high quality articles.

## Codes and Resources Used
- **Editor used:** VS code
- **Python version:** 3.9.4
- **Documentation:** [Wikipedia Page API](https://www.mediawiki.org/wiki/API:Info),  [ORES](https://www.mediawiki.org/wiki/ORES)

## Python Packages Used
- **General Purpose:** json, time, urllib.parse, requests
- **Data Manipulation:** pandas
- **Miscelleneous:** warnings

## Source Data
The source data used are [politicians wikipedia links and articles title](https://en.wikipedia.org/wiki/Category:Politicians_by_nationality) and [population of various countries](https://www.prb.org/international/indicator/population/table). These data are saved in `./data` folder. 

## Data Acquisition
The first API call is made to the Wikipedia API that gives the articles `lastrevid` and using this variable another API call is made to the ORES model that gives the article quality.

For the countries that are present in the population dataset and not in the politician's country and vice versa is stored in `.\output_data\wp_countries-no_match.txt`.

The final required combined data is stored in `.\output_data\wp_politicians_by_country.csv`.


## Analysis 
For analysis variables being calculated are  total-articles-per-population (a ratio representing the number of articles per person) and high-quality-articles-per-population (a ratio representing the number of high quality articles per person) on a country-by-country and regional basis. All of these values are “per capita”.

## Results

Using the above analysis we have fecthed the answers for following -
- **Top 10 countries by coverage:** The 10 countries with the highest total articles per capita (in descending order).
- **Bottom 10 countries by coverage:** The 10 countries with the lowest total articles per capita (in ascending order) .
- **Top 10 countries by high quality:** The 10 countries with the highest high quality articles per capita (in descending order) .
- **Bottom 10 countries by high quality:** The 10 countries with the lowest high quality articles per capita (in ascending order).
- **Geographic regions by total coverage:** A rank ordered list of geographic regions (in descending order) by total articles per capita.
- **Geographic regions by high quality coverage:** Rank ordered list of geographic regions (in descending order) by high quality articles per capita.

## Research Implications

In this project I have learnt how to make API calls by the implementation of API calls such as the WIkimedia and ORES. Morover, my data manipulation skills have strengthened. This project has also helped me in easily identifying anything out of order that might exist in the dataset.

I believe the calculation of the metric ratio of no of articles by the population of that country is not a good measure, as it brings in the bias of population that skew the result significanlty. For instance, countries like India and China has a very huge population so the coverage ratio will be very low for articles produced in these countries, and it might not be true. Similarly for smaller countries like Barbados and Bhutan, the coverage will be very high considering very small population size and non-english speaking country.

It was interestingly suprising to find that the articles list doesn't contain the articles from big countries like United states, Canada, United Kingdom, Australia, and many more. 

Implementing this project can help us in determining what countries have good articles and which countries to focus more on improving their articles. 

Furthermore, the ratio of good articles by total number of articles generated in each country, region and continent will be a good way to overcome the bias along with understanding the high quality production at different level of granularity.

## Licenses

Source Data License: [Wikimedia Rest API](https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end), licensed under [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/licenses/fdl-1.3.html)

Wikimedia Foundation REST API terms of use: [Wikimedia Terms & Conditions](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions)