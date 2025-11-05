## Overview
Creating a pipeline to injest and analyze OpenAQ historical data




to do
download from s3
create API maintenance download 
automate with airflow
add test units 



## Tools
Ingestion - 
  apache spark
  OpenAQ S3 bucket
Orchestration
  apache airflow
Transformation
  dbt (data build tool)
Storage
  Clickhouse
Quality
  Great Expectations
Visualization
  tableu

https://clickhouse.com/docs/getting-started/quick-start/oss

## Datasources

### OpenAQ
https://openaq.org/why-open-data/
https://github.com/openaq/openaq-fetch

Api end point allows for 60/min or 2000/day
pull from S3 bucket then daily pulls from API (need to test how much data is generated daily)
https://docs.openaq.org/aws/quick-start

*Current plan:* Load bulk data from S3, move into clickhouse running on (?) load daily from API with airflow. 

#### Questions
- Which datasources are used for this dataset? this is billed as comprehensive, are all the sources listed below in this set?
- How many records are generated daily? Can daily injestion be handed under rate limits? if not adopt a sampling strategy?


### AirnowAPI
https://docs.airnowapi.org/

### Air Gradient
https://www.airgradient.com/

### Purpleair
https://community.purpleair.com/t/about-the-purpleair-api/7145


## Clickhouse

`sudo -u clickhouse clickhouse-server --config-file=/etc/clickhouse-server/config.xml --daemon`

`clickhouse-client`


## Bulk load
### Setup infastructure
- [ ] Setup Clickhouse on local server via docker
- [ ] Setup local spark environment
- [ ] Setup Click-house spark connector
- [ ] setup dbt and configure with clickhouse
### Extract and pre-process
- [ ] read files from S3 with spark
- [ ] define schema in spark
- [ ] initial cleaning (define better)
- [ ] standardize features if needed
### Load data
- [ ] create raw table in clickhouse using MergeTree (for time-series)
- [ ] Insert data with spark dataframe writer
### Transform
- [ ] setup dbt to select from raw tables
- [ ] setup fact/dim tables
- [ ] test and validate data



`exit`

