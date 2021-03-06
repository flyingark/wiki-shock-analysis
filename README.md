# Description

This repository contains data collection, preprossing and part of the Wiki talk page analysis.
All Python codes are written in Python 2.7

## data 

This folder contains all the data we need including the result generated by the code.

### articles

This folder contains two tsv files: Politician and Academic articles with corresponding Wiki urls we got from Wikipedia.
	* polititian_articles_with_wiki_url.tsv
	* scientist_articles_with_url

### suggestions

This folder contains the suggestion data of Wiki Articles from Google Trends API.

Suggestions for all articles 
	* politician_suggestions.tsv
	* scientist_suggestions.tsv
Selected professions for articles
	* scientist_profession_lst.txt
	* politician_profession_lst.txt
Suggestions for articles with a GT topic
	* politician_suggestions_with_GT_topic.tsv
	* scientist_suggestions_with_GT_topic.tsv
Mids for articles (Mid is a reference id of an article under specific topic to GT API)
	* politician_match_data_mid.tsv
	* scientist_match_data_mid.tsv

### trends

This folder contains the Google Trends collected from GT API for selected articles.

A match list of article names with Wikipedia article id
	* article_ids.csv
Mids for articles conbined with Wikipedia article id
	* politician_match_data_merged_mid.tsv
	* scientist_match_data_merged_mid.tsv
GT data (monthly) and Wikipedia summary paragraph for each article
	* politician_trends_with_wiki_id_and_summary_clean.tsv
	* scientist_trends_with_wiki_id_and_summary_clean.tsv
Articles identified a shock in their trends with shock time frame (in order to get daily trends)
	* politician_shock_tf.tsv
	* scientist_shock_tf.tsv
GT data (daily) for each article
	* politician_trends_shock_daily.tsv
	* scientist_trends_shock_daily.tsv

### talkpage

This folder contains the data related to Wikipedia's talk page of articles

Grouped talk page data for articles (Each group is considered a single discussion topic)
	* wiki_talk_groups_academics.json
	* wiki_talk_groups_politicians.json

Metrics of users behaviors and other activities for politician and academic articles.
	* treated_main_metric.csv		

User talk page metrics combined with users activities for articles (json file)
	* wiki_talk_stats_politicians.json
	* wiki_talk_stats_academics.json

Final summrization of user activities for both articles and talk page. (csv file)
	* wiki_talk_stats_academics_final.csv
	* wiki_talk_stats_politicians_final.csv

### Biography

This folders contains all types of data mentioned above for controled group: randomly selected biography samples.

## code 

This folder contains all Python scripts to obtain Google Trends and Wikipedia data, analyze and summarize the data.

**The order follows the actual steps if you want to regenerate part of the data**

suggest.py

* This script is to collect sugeestions from Google Trends API. You need to have pytrends 4.1.1 installed.

suggestions_analysis.py

* This script is to analyze the suggestion data returned by Google Trends API and filter out the mid of good articles. A good article is: the suggestion title matches article's name; AND the suggestions' type is in the selected profession list.

get_trends.py

* This script is to collect Google trends (monthly) for selected articles

get_daily_trends.py

* This script is to collect daily Google trends for articles. Specific shock time fram is needed.

get_grouped_talkpage.py

* This script is to collect original wiki talk page data for politician and academics articles grouped by each discussion topic. (Under the same header on talk page)

get_samplebio_grouped_talkpage.py

* This script is to collect original wiki talk page data for biography sample articles grouped by each discussion topic. (Under the same header on talk page)

talk_stats_analysis.py

* This script is to summarize original talk page contents for politicians and academics into numeric metric and generate a json file to store.

talk_stats_analysis_bio.py

* This script is to summarize original talk page contents for bipgraphy samples into numeric metric and generate a json file to store.

talk_page_summary.py

* This scipt is to load two json files generated in the previous two steps and add a metrics related to the reply of new editors. Cretae a csv summary table for further analysis finally.
