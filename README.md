## Introduction

<p> A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app. </p>

## Project Design

<p> Create a Postgres database, schema with tables designed to optimize queries on song play analysis. Create a Postgres database, schema with tables designed to optimize queries on song play analysis.  

I am going to create use Postgres database for this project. PostgreSQL is a powerful, open source object-relational database system that uses and extends the SQL language combined with many features that safely store and scale the most complicated data workloads. PostgreSQL runs on all major operating systems, has been ACID-compliant. I am going to create separate fact and dimension table and create star schema. Star schema is helpful in crating simple queries, fast aggregation, better query performance and simplified business reporting logic.

I am going to create ETL pipeline in python. I am going to utilize the powerful pandas library of python for pulling required fields from the source file. I am going to use psycopg2 python library to connect to postgres database.

</p>

## Datasets
### Song Dataset
<p> The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.This dataset contains below keys:

</p>
<ul>
<li>num_songs</li>
<li>artist_id</li>
<li>artist_latitude</li>
<li>artist_longitude</li>
<li>artist_location</li>
<li>artist_name</li>
<li>song_id</li>
<li>title</li>
<li>duration</li> 
</ul>

### Log Dataset
<p>The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.This dataset contains below keys:
  
  </p>
  
<ul>
<li>artist</li>
<li>auth</li>
<li>filemane</li>
<li>gender</li>
<li>iteminSession</li>
<li>lastName</li>
<li>length</li>
<li>level</li>
<li>location</li> 
<li>method</li>
<li>page</li>
<li>registration</li>
<li>sessionid</li>
<li>song</li>
<li>status</li>
<li>ts</li>
<li>userAgent</li>
<li>userid</li>   
  
</ul>  

## Schema Design, Setup Instructions and Steps followed

<p>
Using the song and log datasets, start schema is created for to queries on song play analysis. This includes the following tables.
</p>  

### Fact Table

<ul>
<li>songplays - records in log data associated with song plays i.e. records with page NextSong
  songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent</li>
</ul>  

### Dimension Tables

<ul>
<li>users - users in the app</li>
<li>user_id, first_name, last_name, gender, level</li>
<li>songs - songs in music database</li>
<li>song_id, title, artist_id, year, duration</li>
<li>artists - artists in music database</li>
<li>artist_id, name, location, latitude, longitude</li>
<li>time - timestamps of records in songplays broken down into specific units</li>
<li>start_time, hour, day, week, month, year, weekday</li>
</ul>  
  
### Steps followed

<p>

Below are steps followed to complete the project:

</p>  

<ul>
  
<li>Create Tables - CREATE TABLE statement for fact and dimension table is written.</li>
<li>Load dimension table - INSERT statement to load dimension table from json file is written.</li> 
<li>Transformation - Data from the source json file is transformed to get the required filed like hour, month and year.</li>
<li>Load Fact table - Once the dimension table is loaded then we can fetch the required fileds from dimension table and source file to get required filed to load in to fact table.</li>  
</ul>

## Program execution 

<p>

Below are steps followed for program execution:

</p>  

<ul>
  
<li>Run create_tables.py to create your database and tables.</li>
<li>Run etl.py to process all the files to load in to dimension and fact table.</li>
<li>Run test.ipynb to confirm your records were successfully inserted into each table.</li>
</ul>

## Purpose of this database

<p> Sparkifydb database helps in answering the questions to analyst like what song users are listening to. Analyst can perform 
  various analytical operation on this data easily to gain more insight on users activity.
 </p> 
  
