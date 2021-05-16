
# SAINT Imagine Labs Datathon 2021
[Dataset retrieved from Kaggle](https://www.kaggle.com/dgomonov/new-york-city-airbnb-open-data)

## Build AWS EC3 RDS Server
![Amazon](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Server/Create%20Database.png)
  ### Create Database
    1) Select in 'Choose a database creation method'
       Standard create
    2) Select in 'Engine options'
       2.0)  MySQL
       2.1) Edition MySQL community

  ### Template
    1)  Select Free Tier
  
  ### Settings
    1) Generate the DB instance identifier
    2) Generate Master username
    3) Generate Master password

  ### Connectivity
	In public Access, select Yes.


## EDA, Exploratory Data Analysis
[Link to Jupyter NB PDF](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/Python/Airbnb%20EDA.pdf)

	1) Read The Data CSV
	2) Understand the data using head() and tail()

![head()](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/Images/head().jpeg)
![tail()](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/Images/tail().jpeg)

	4) Check the shape of the dataset. Here we have '48895 rows' and '16 columns'
	5) Get info about each column using  info(), we found  that '3 columns where float64',
    '7 columns where int 64', and ‘6 where object/string’.
![df.info()](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/Images/info().jpg)
	
	5) Check the number of nulls in the table, we found out ‘last review’ had 10,005 nulls, 
    reviews_per_month also 10,005,  ‘host_name’ had 25 nulls and ‘name’ just 16.
![Null](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/Images/nullOfDataSet.jpg)
  
## Star Schema DB, we named it 'airbnb_nyc'
       To make the analysis of the dataset easier, we decided to create a data warehouse (database) 
       that followed the star schema. Each unique id in the data set made a dimensional table, meaning
       that we only included attributes that weren’t numerical. In this data set we only managed to design
       2 dimensional tables. Those dimensional tables were the outer tables of the star schema and the core 
       table was the tableFact. This last table was designed with just numerical attributes and the primary 
       keys of the dimensional tables.

![Star Schema DB - airbnb_nyc](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/StarSchema/StarSchemaDB.jpg)	
	
* dimhost Table
* dimhousing Table
* tableFact Table

 ### SCRIPT
[Link to DDL  SCRIPT](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/StarSchema/StarSchema.txt)

 ### Local Dbeaver to MySQL
	Fill the blanks:
		Server host: Endpoint provided by AWS RDS
		Port: Leave it like that
		Database: Empty
		Username: master user created
		Password: pass code created
![Connect Server in DBeaver](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/DBeaver/Connection%20Settings.png)
 
## ETL Data
1) Using python we rearranged  the dataset’s columns into 3 new CSV, one for each new table in the database. Each table matching the attributes of the Star Schema DB model we builted

* [dimhost csv](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/CSV/dimhost.csv)
* [dimhousing csv](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/CSV/dimhousing.csv)
* [tablefact csv](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Analysis/CSV/tableFact.csv)

2) Execute the sql script to create the tables
3) Now, using the graphic interface of DBeaver import the .csv files
4) Firstly, import the tables dimHost and dimHousing
5) Then, import the data to table tableFact

## DashBoard
[File for Tableau Dashboard](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Dashboard/PerformanceMetricsNYC.twb)
1) Identify all the objects and their function.
2) Import the DB to Tableau
3) Design different metrics that are relevant to the data analysis. 
4) For example: Average Price by Neighborhood Group.
5) Select a Sheet in Tableau and start adding the different objects that will satisfy the metric.
6) Place the objects in Row, Column, Marks or Filters and select the most fitting graphical representation. 
7) Add a Dashboard tab and place the different sheets that have been made.
8) Modifications on format, colors and placement can be done.

![Dashboard Tableau](https://github.com/ArmandoDLaRosa/SAINT-ImagineLabs-Datathon-2021-Python-Tableau/blob/main/Dashboard/Dashboard%20-%20Performance%20Metrics%20in%20NYC.png)
