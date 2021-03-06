# SQL Database Definition
This directory contains the logical and physical data model for the voter file warehouse as well as generated DDL.

The data models are maintained using Oracle's SQL Data Modeler Tool [Download a copy here](http://www.oracle.com/technetwork/developer-tools/datamodeler/overview/index.html).

# Setting up the Postgres Database (the easy way)
If you're into [Docker][docker], we have written a Dockerfile to build the database service. The following instructions assume you've installed Docker, and are familiar with the basics of it. If you're not using Docker, see the next section for how to build your database manually.

[docker]: https://docker.com

## Building the Container
```
dockerResources/docker-build.sh
```
This command builds the container from the Dockerfile and names it `nvf_postgis`. If you rename the container, the other scripts in this folder won't work. 

## Running the Container 
```
dockerResources/docker-run.sh
```
This scripts first tries attaching to the running container. If the container isn't running, it will start it. When you run this script, the terminal window shows the running output of the postgres server. To exit the server, press `ctrl-C`.

## Connecting via PSQL
```
dockerResources/psql-connect.sh
```
Simply a convenience script to the running database via psql.

## Connection Settings
The settings for connecting to the database while the container runs are as follows. Use these for connecting from Pentaho, PgAdmin, or whatever else you may enjoy:

```
host: localhost
port: 54321 // Note non-standard port! 
user: postgres 
database: VOTER
```




# Setting up the Postgres Database (the hard way)
This ddl has been tested against Postgres version 9.5 with postgis extensions installed.

1. Execute create_database.sql to create the voter database instance
2. Execute create_tables.sql to run the DDL for setting up the DB
3. Run populate_static_date.sql to set up some static data in the dimensions.

The script clearDB.sql is handy for clearing out all data so you can run scripts over agains
with empty tables.

The DDL was initially generated from the SQLModeller data model, however significant adjustments are required to 
use it with Postgres. The file tablesNotYetReady.sql contains some tables that have not yet been cleaned up.
They will need some attention before they can be added to the DB.
