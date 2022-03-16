# Presentation Overview

1. Front Page
    1. what to take away
        1. Good understanding of what Kinesis Firehose is and what it is good for
        1. limitations and bounds of the service
        1. some common use cases and how and when to apply them
    1. References - Kinesis Firehose Website, Dev UG, Experiences
1. Why talk about Kinesis Firehose
    1. logos
    1. Genuinely useful data engineering service
    1. INFP - lazy type
    1. it's kind of simple, does what is advertised and reduces a lot of annoying gluey code
1. What is it and what does it do
    1. here's what AWS says it is
    1. what it really does
        > close the gap between systems that produce data and systems that turn it into information
1. There's more Kinesis - how are they related
    1. Kinesis Data Streams - the useful streaming bit that has the capacity to scale to half a gb of ingest per second (500 shards) - 42Tb per day
       (smells like DynamoDB)
    1. Kinesis Firehose - like a kinesis stream with a built in consumer to send your stuff to a destination
       (it's probably Apache Flink!)
    1. Kinesis Data Analytics - stateful stream (sliding/tumbling window) processing. Literally is Apache Flink
1. Why is Kinesis Family important?
    1. because AWS supports Kinesis Firehose ingestion natively in a few places, e.g. EventBridge, AWS IOT, AWS CloudWatch (read the fine print), Pinpoint
    1. Because they interact closely with each other, e.g. Firehose Direct Input is like a single shard stream , but with on-demand pricing
    1. Because if you want to scale up, you will need to get familiar with Kinesis Streams
1. Segway - the nature of product / system development teams of the years
    1. my experience
        1. in the beginning it was developers and BAs. My functional specs were printed
        1. then came the testing
        1. then some agilists
        1. then came the devops and SREs
        1. are data people next?
    1. i hope so
        1. help teams deliver operational data for analytics use cases more efficiently
        1. deliver general, but contextual, operational analytics with existing products
        1. improve data literacy across software teams
1. Common Use Cases
    1. Log aggregation - via agent or natively/directly
    1. EIP - funneling, splitting, transformation, conversion
    1. Proxy destination via HTTP (e.g. ClickHouse)
1. Patterns

    1. Agent Provocateur:

        _windows kinesis agent - logs to OpenSearch_

    1. Pump and Dump 1:

        _lambda direct to firehose -> S3_

    1. Ship and Split:

        _e.g. CQRS, differing lambdas sending single firehose using dynamic partitioning to S3_

    1. Storming and Transforming:

        _CSV -> Transform to JSON -> Format Convert to Parquet_

    1. Pump and Dump 2:

        _Multiple DynamoDB tables stream to single Kinesis Stream, destination S3 split to partitions_

1. What to watch out for
    1. quotas
    1. limitations (lambda buffer limit 6mb)
    1. partially supported use cases
1. Summary - what's good about Firehose
    1. with direct input (managed), pay for what you transfer
    1. for high throughput, scale kinesis stream as you require
    1. for variable throughput with remnant base, use new kinesis on-demand (starts at 8 shards) - how much per day?
    1. retries for you!
    1. lots of destinations, and can customise with your own HTTP destination
    1. lots of integrated AWS sources (EvB, IOT, CloudWatch)
    1. Low cost barrier to try out (direct input)
    1. simple or complex transformation options - e.g. enrichment, geoip
