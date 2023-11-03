# Big-Data-Los-Angeles-Crime-Data-Analysis

## Description 

The Public Policy Institute of California reports that violent crime rates in California have seen a significant increase of 6.0% in 2021, with a marked rise in aggravated assaults, homicides, and rapes. The impact of crime on communities cannot be overstated, and it is crucial to analyze crime incident data to identify trends and patterns. This project aims to focus on the extensive historical dataset from Los Angeles, covering January 2010 to April 2023 and consisting of approximately 2.8 million records. By leveraging data-driven strategies, the project aims to address the escalating occurrence of crime.

## DataSet 
 Los Angeles Open Data hub with the data provided by the Los Angeles Police Department.

 ## System Architecture

 The raw dataset used for this project was downloaded from the LA Open Data Portal and provided by the LA Police Department. The dataset was then uploaded into the S3 bucket 'raw_dataset' folder. An EMR cluster was created to provide computational resources for ETL and analytical querying. Hive and Spark applications were installed in the cluster.

To clean and transform the raw dataset into a processed one, a PySpark script was written. The AWS Glue Spark Job was then configured to run the script using the EMR cluster resources. As a result, parquet files containing the processed dataset were created in the S3 bucket 'processed_data' folder.

The AWS Glue Crawler was run to read a schema of the parquet file and place it into a new table in the AWS Glue Catalog. AWS Athena was used to query the table and check that the dataset was created without errors.

Using the EMR cluster command line interface, an external Hive table was created concerning the dataset's parquet files. To query the external Hive table, a Tableau EMR Hadoop Hive connection was established. Views and dashboards were created using Tableau to analyze the data through the external Hive table. The dashboard was published in Tableau Public.

An EC2 instance was created to host the web application. Apache HTTP Web Server was installed on the EC2 Web Server as an environment to host and manage the web application. Web application files were created with embedded code that provides access to the Tableau Public Dashboard and was copied to the Apache HTTP work directory.

The domain pipapp.xyz was purchased and the AWS Route 53 Hosted Zone was configured to publish the web application. An SSL Certificate was created and configured for the hosted zone to provide a secure https connection to the users of the web application.

<img width="584" alt="Screen Shot 2023-11-03 at 1 14 33 AM" src="https://github.com/ProBag/Big-Data-Los-Angeles-Crime-Data-Analysis/assets/143302669/9d23f17a-0093-4bd7-91dd-5b007a150540">

## Data Flow 

To start with, the raw dataset was uploaded from LA Open Data (LA Police Department) to the S3 bucket. The PySpark ETL script used in AWS Glue Spark Job cleaned and transformed the raw dataset into parquet files of processed data, which were then saved in S3.

Using EMR Hive, a Hive external table concerning the parquet files was created. Tableau used Amazon EMR Hadoop Hive connection to query the Hive external table. The resulting Tableau dashboard was embedded as a script to the web application's index.html.

The web application files were then uploaded to the EC2 Web Server, and users accessed the web application through an https (SSL) connection on pipapp.xyz.

<img width="612" alt="Screen Shot 2023-11-03 at 1 16 15 AM" src="https://github.com/ProBag/Big-Data-Los-Angeles-Crime-Data-Analysis/assets/143302669/ef132da5-822e-46ef-a538-0a76ba85d23f">

## Conclusion 

Crime data from 2010 to 2023 in Los Angeles was obtained from the Los Angeles Open Data portal. The data was combined and uploaded to an Amazon S3 bucket. An EMR cluster was then created to provide the resources for ETL and analytical processing. The data was processed through a PySpark script and Amazon Glue, and the output was a parquet file.

Using the EMR command line interface, an external Hive table was created regarding the parquet files. Tableau established an EMR Hadoop Hive connection to the Hive external table to create an interactive dashboard. The dashboard was then published to the Tableau public.

To host the web application, an EC2 instance with Apache HTTP was created. The web application was created using HTML and embedded the interactive dashboard made with Tableau. The domain "pipapp.xyz" was purchased and configured with AWS Route 53 Hosted Zone to publish the web application.

 Web applications will aid regular citizens, law enforcement, and policymakers in being more aware of crimes that have occurred in the city of Los Angeles.

## References

Lofstrom, M., & Martin, B. (2023, February 13). Crime trends in California. Public Policy Institute of California. Retrieved May 7, 2023, from https://www.ppic.org/publication/crime-trends-in-california/ 

A. Mukherjee, S. De, S. Bhattacharyya, and J. Platos, "Chicago Crime Data Analysis 
Using PIG in Hadoop," 2018 Fourth International Conference on Research in 
Computational Intelligence and Communication Networks (ICRCICN), Kolkata, India, 2018, pp. 242-247, doi: 10.1109/ICRCICN.2018.8718725.


Monika and A. Bhat, "An analysis of Crime data under Apache Pig on Big Data," 2019 
Third International Conference on I-SMAC (IoT in Social, Mobile, Analytics and 
Cloud) (I-SMAC), Palladam, India, 2019, pp. 330-335, doi: 10.1109/I-SMAC47947.2019.9032565.


