### 3 - Ship and Split

#### Context

Create simple data infrastructure to capture diverse Event Source data to S3

#### Solution

-   <span style="font-size:80%">Create a Kinesis Data Stream with on-demand capacity</span>
-   <span style="font-size:80%">Create a Kinesis Data Firehose with input from the data stream</span>
-   <span style="font-size:80%">Configure Event Sources to write JSON payloads to Data Stream with distinguishing field / identifier</span>
-   <span style="font-size:80%">Configure Data Firehose with Dynamic Partition to split data stream into dynamic prefixes</span>
