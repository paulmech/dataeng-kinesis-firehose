### Storming &amp; Transforming

#### Context

Convert high volume of S3 landed CSV files into parquet format

#### Solution

-   <span style="font-size:80%">Define Glue Catalog Table with require parquet output structure</span>
-   <span style="font-size:80%">Create Firehose with Transformation Lambda to convert CSV to JSON</span>
-   <span style="font-size:80%">Configure Firehose with format conversion bound to Glue Table</span>
-   <span style="font-size:80%">Use Lambda, ECS, etc to process landed CSV files, streaming into Firehose</span>
