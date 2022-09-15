# Eitri Medical Datathon 2022 - News media & respiratory diseases dataset

This repository contains the news media & respiratory diseases dataset as part of one of the challenges of the Eitri Medical Datathon 2022.

It contains data but also scripts to expand the dataset.

## Installation

Clone this repository :

```bash
git clone https://github.com/AdrienC21/eitridatathon2022_media.git
```

Or download the files manually.

## Datasets

All files are located inside the folder **datasets**.

### Disease, COVID data

```msis_data.csv```

Daily data for different diseases in Norway (at the national level) such as respiratory diseases. [Source: MSIS](http://msis.no).

**IMPORTANT:** Data can be obtained at the regional level, can be stratified by gender, age group and/or place of infection. We can also extract data from 1976 (instead of 2010). If needed, please ask a mentor to retrieve such data automatically.

```NOR.csv```

Daily COVID data at the national level (cases, deaths, vaccines, school closing, etc).

```covid_cases_regions_norway.csv```

Daily COVID cases data at the kommune level in Norway. The fylke of each kommune is also indicated. Extracted from John Hopkins University database.

### Media Cloud & Google Trends

New Media Cloud and GoogleTrends data can be downloaded using the scripts ```generate_mediacloud.py``` and ```generate_googletrends.py```, located inside the folder **datasets**.

You can find a list of countries in the excel files *collections_country.csv* (worldwide) and *norway_collections.csv* (specific for Norway).

Before running the scripts:

- To fetch data for specific keywords, modify the keyword list in the file *keywords.csv*.

- Change the configuration file ```config.py``` (instructions below)

```config.py``` allows one to change the list of countries, the timeframe, and the keywords for data retrieval.

**IMPORTANT:** If you need help to extract Media Cloud and Google Trends data, please call a mentor.

#### Media Cloud

For Media Cloud data, the dictionnary entitled ```login_info``` needs to be modified. To do so, connect to your [Media Cloud](https://mediacloud.org/) account and open the *Explorer tool*. Inspect the webpage and go to the *Network* tab. After making a query, click on *split-count*. On the right, in *Request Headers* and *cookie*, retrieve the ```mc_remember_token``` and ```mc_session``` values and insert them into ```config.py```.

![mediacloud](https://raw.githubusercontent.com/AdrienC21/eitridatathon2022_media/master/images/mediacloud.png)

#### Google Trends

For Google Trends data, the ```header``` dictionnary must be updated. First, visit the [Google Trends website](https://trends.google.com/trends/?geo=US), inspect the webpage and go to the *Network* tab. After making a query, right click on explore, and click on *Copy as cURL (bash)*. Convert the command into a Python request using [curlconverter](https://curlconverter.com/). Retrieve only the ```header``` dictionnary.

![googletrends](https://raw.githubusercontent.com/AdrienC21/eitridatathon2022_media/master/images/ggtrends.png)

## Additional files

```collections_country.csv```

Contains the Media Cloud collection ids and the Google trends ISO codes of almost all the countries in the world.

```norway.csv```

Raw list of Media Cloud collection id for all regions in Norway.

```norway_collections.csv```

List of Media Cloud collection id for all regions in Norway & collection id for the national level.

```fylke.csv```

Map each counties in Norway to the corresponding fylke (county after 1 January 2020). [Source](https://en.wikipedia.org/wiki/Counties_of_Norway).

```fylker_komprimert.csv```

Geojson file with the boundaries of each county. Useful to plot choropleth map (an exemple of such plot is provided in the workshop: Leveraging Non-traditional Sources of Data).

## License

[MIT](https://choosealicense.com/licenses/mit/)
