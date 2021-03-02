# Covid-19 Reporting On Azure Cloud

Create a Covid-19 reporting project utilising the following Azure services:
- Data Factory
- SQL DB
- Data Lake
- Databricks
- HDInsight


&nbsp;
&nbsp;


## 2020-02-08

### Created the following services
- Resource Group (covid-19-reporting-rg)
- SQL DB (c19-server/c19-db)
- Data Factory (c19-reporting-df)
- Datalake (c19reportingdatalake)
- Blob Storage (c19reportingstorageacct)


&nbsp;
&nbsp;


## 2020-02-23

### Prepared containers in Blob Storage and DataLake
1. Created a container ('population') in Blob Storage
2. Created a container ('raw') in Datalake
3. Uploaded gzip file 'population_by_age.tsv.gz' to 'population' container in Blob Storage


&nbsp;
&nbsp;


## 2020-03-02

### Created linked services and datasets in Azure Data Factory
1. Created a linked service ('ls_blob_c19reportingstorageacct') for Blob Storage
2. Created a linked service ('ls_adls_c19reportingdatalake') for ADLS Gen 2
3. Created a dataset ('ds_population_raw_gz')
    * linked service: 'ls_blob_c19reportingstorageacct'
    * file path: 'population/population_by_age.tsv.gz'
4. Created a dataset ('ds_population_raw_tsv')
    * linked service: 'ls_adls_c19reportingdatalake'
    * file path: 'raw/population/population_by_age.tsv'
5. Published these 2 datasets

&nbsp;

### Created data pipeline to move data from Blob Storage to ADLS
1. Created a data pipeline ('pl_ingest_population_data')
2. Created a copy activity ('Copy Population Data') in the pipeline
    * timeout: 0.00:05:00 (which is 5 mins)
    * source dataset: 'ds_population_raw_gz'
    * sink dataset: 'ds_population_raw_tsv'
3. Published the copy activity
4. Debug the copy activity



