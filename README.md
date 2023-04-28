# Develop-a-data-pipeline-using-Apache-Spark-Google-Cloud-Storage-and-Google-Big-Query

This project consist of developing a data pipeline using Apache Spark, Google Cloud Storage, and Google Big Query.

1) Tools used:

	-Spark- is an open-source big data processing framework used for distributed computing. 
			It is designed to handle large amounts of data and can perform tasks such as data processing,
			and machine learning.
			
	-Google Cloud Storage-  is a cloud-based object storage service provided by Google that allows you to store 
							and access your data from anywhere on the internet.
							
	-Google BigQuery- is a cloud-based data warehousing tool provided by Google. 
					  It allows you to analyze large datasets using SQL-like queries and offers high-performance 
					  querying and scalable storage for structured and semi-structured data.

2) Data Source:

The data we'll be using is from the Brazilian “higher education” (literal translation) census. 
This census yearly collects many statistics about Brazilian higher education institutions
(basically the universities) from many perspectives: institutional,social & demographic, geographic, and so on.
This data is publically available [CC BY-ND 3.0] in CSV files (one per year).

3) Schema:

The idea to develop this pipeline is to download the CSV files to the local machine, 
convert them into a Delta-Lake table stored in a GCS bucket, 
do the transformations we want over this delta table, then save the results in a Big Query Table 
that can be easily consumed by other downstream tasks.

Here is the schema I followed to build the pipeline:

![alt text](https://github.com/haytam1999/Develop-a-data-pipeline-using-Apache-Spark-Google-Cloud-Storage-and-Google-Big-Query/blob/master/Schema.png?raw=true)

4) Scripts:

file_downloads.py: download the CSV files from the web to our local machine.

CSV_to_GCS_delta_table.py: insert the CSV files to a delta table in google cloud storage.

delta_table_GCS_to_GBQ_table.py: aggregates the final tables into Google big query.

	
