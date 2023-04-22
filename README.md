# ADAMS NRC enrichment for Internet Archive

## Description

This repo contains code for:

- Downloading a mapping between document titles and accession IDs and saving that data `fetching.ipynb`.
- Basic topic modeling of the documents based on those titles `modeling.ipynb`.

<img src=https://github.com/jacksongoode/nuclear-collections/blob/main/top-topics.png  width=50% height=50%>

A sample dataset is also generated and available in this repo at `docs/2023-01-01_2023-04-30_docs.json`.


## Processing Steps
### Major Obstacles
* Data scraped by web archive does not contain any identifying information for organizing and searching 
* Source data at [https://adams.nrc.gov/wba/](https://adams.nrc.gov/wba/) can be queried using SQL to obtain a mapping between document titles, accession IDs, and other relevant information, however queries are limited to 1000 items. 
* Many objects returned by the SQL queries are containers for data, rather than the data itself

### Current Solution (Python)
* Generate template SQL query to send via `requests` to source website, filtering specifically for .pdf files
* Using a sliding window on when the documents were added, compile a list of all documents added during a specific timeframe
* Save as a .json file
* Extract document titles for preliminary analysis

## To Do
* Generate data for desired dates
* Filter through relevant documents
* Apply and join mapping on top of existing archives
