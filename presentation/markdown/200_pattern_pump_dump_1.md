## 2 - Pump and Dump

#### Context

DynamoDB Change Data Capture to S3 (cheaply)

#### Solution

-   Create Kinesis Firehose Direct Input and S3 destination
-   Create Lambda Function to write CDC to Firehose
-   Subscribe Lambda Function to DynamoDB Stream Event Source
