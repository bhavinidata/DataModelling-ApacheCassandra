# Sparkify - Data Engineering Project

#  ETL - Data Modelling with Apache Cassandra

## Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can create queries on song play data to answer the questions, and wish to bring you on the project. Create a database for this analysis. Test database by running queries required by the analytics team from Sparkify to create the results.

## Tasks
- Process dataset to create a denormalized dataset. 
- Iterate through each event file in event_data to process and create a new CSV file in Python. Below is the example of how file data looks like:

![](image_event_datafile_new.jpg?raw=true)

- Model data by creating tables in Apache Cassandra to run queries for a particular analytic focus.
- Build an ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables using python and CQL.
- Execute queries successfully for analysis puporse.

## Dataset
The directory of CSV files partitioned by date. Here are examples of filepaths to two files in the dataset:

event_data/2018-11-08-events.csv
event_data/2018-11-09-events.csv

## Steps to create an Apache Cassandra database and run the ETL Pipeline:

* Write logic to iterate through each event file and creare a csv file object and run.
* Create a Keyspace in Apache Cassandra.
* Write out your Create Table statements.
* Load the data with Insert statement for the created tables
* Execute qureries and verify the results.
* Close Session and close connection.

## Example queries

Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4
* Here as we want data to be filter out by sessionid and itemInSession, those two are being used as partition key.

`"SELECT artist, song, length FROM song_detail WHERE sessionid=338 and iteminsession=4"`

Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
* Here as we want data by userid and session id, those two are used as partition key and itemInSession is used as clustering column to sort data by itemInSession.

`"SELECT artist, song, first, last FROM song_by_user WHERE sessionid=182 and userid=10"`

Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'
* Here song is used as partition key as we want to filter out data by song and userid is used as clustering column to make primary key unique.

 `"SELECT first, last, song FROM user_by_song WHERE song='All Hands Against His Own'"`

<br>


