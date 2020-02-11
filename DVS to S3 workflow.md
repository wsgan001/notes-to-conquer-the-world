---
title: DVS to S3 workflow
created: '2020-02-04T20:28:24.005Z'
modified: '2020-02-04T20:47:44.078Z'
---

# DVS to S3 workflow
- Use kafka connect to stream to s3
- Some streams dont work correcly. 
- Kenisis -> Firehose -> S3
- You can batch rows per file with Kafka Connect. 
- You can keep the same compression and file format: parquet or avro. 
- Look into Kafka Connect app. Connects to DVS kafka cluster. 
- Kafka Connect can be configured for file sizes. 
- ECS https://github.com/ps-dev/learner-data/tree/master/kafka-connect
