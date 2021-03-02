# Covid-19 Reporting On Azure Cloud

Utilise Azure cloud service to create a Covid-19 reporting side project.


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

### Copied a dataset from Blob Storage to DataLake
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
 * file path: 'raw/population_by_age.tsv'




