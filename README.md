# ASE/NewsGuard Dataset

Contained in this repository is a dataset (`dataset.json`) generated from the ADM+S Australian Search Experience (ASE) research project that corresponds to website domains (as search results) obtained for specific search platforms, keywords, time ranges, and statistics.

## Data Fields

### Time Window

The results were collected for the period of time between _Wednesday, September 1, 2021 12:00:00 AM GMT+10:00_ to _Thursday, December 30, 2021 12:00:00 AM GMT+10:00_.

### Platforms

The results were obtained from the following platforms: "Google News", "Google Search", and "Youtube".

### Queried Keywords

The results were obtained for the following _keywords_, which served as search queries that were fed into the relevant platforms to yield the necessary results: "Feminism", "Critical Race Theory", and "COVID".

### Statistics

The statistics collected at each interval within the time range were the __frequency of observations__ for any search result, as well as the __average rankings__ that the search results had within the lists of search results for the search pages returned (on said queries).

### Other Considerations

* For any search page obtained for any of the surveyed platforms (from which the search results here were yielded), only the top 10 search results were considered.
* When compiling the dataset, both mobile and desktop domain types (obtained through the ASE study design) were combined in post-processing steps.
* For the collected time window, each interval encapsulates the results for the consecutive three days that follow it e.g. September 1st 2021 will encapsulate all results collected for the 2nd and 3rd of said month also.

## Data Format

The structure of the dataset is given as follows:

_Note: The elements listed for both the `observations_frequency` and `average_ranking` keys are ordered from largest to smallest, by their respective values._

```
{
	PLATFORM : {
		QUERIED_KEYWORD : {
			TIME_WINDOW_AS_UNIX_TIMESTAMP : {
				"observations_frequency" : [
					{
              "result": WEBSITE DOMAIN 1,
              "value": XXX
           },
					{
              "result": WEBSITE DOMAIN 2,
              "value": XXX
           },
					{
              "result": WEBSITE DOMAIN 3,
              "value": XXX
           },
           ...
				],
				"average_ranking" : [
					{
              "result": WEBSITE DOMAIN 1,
              "value": XXX
           },
					{
              "result": WEBSITE DOMAIN 2,
              "value": XXX
           },
					{
              "result": WEBSITE DOMAIN 3,
              "value": XXX
           },
           ...
				]
			}
		}
	}
}
```



## Supplementary NewsGuard API Data

NewsGuard compiles qualitative news 'health score' data for various news outlets. Excluding the "Youtube" platform (which does not have corresponding news outlet data for Youtube channels), website domains have been queried within the NewsGuard API, to yield data where their organisation indexes it.

This is given in the additional `newsguard.json` file, which contains a dictionary, where each key is the relative domain queried, with the result being that which was returned from NewsGuard (if applicable) or `null` otherwise.

_Note: Presently, 633 of the 1,207 domains are indexed by NewsGuard._