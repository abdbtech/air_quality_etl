## Overview
Creating modern ETL pipeline for disparate air quality data streams for future analysis




## Tools
apache spark
apache airflow
tableu
clickhouse (postgresql)
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

`exit`

