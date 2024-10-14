# Project: Data Modeling with Apache Cassandra

## Overview

This project is part of the Udacity nanodegree **Data Engineering with AWS**. It creates an Apache Cassandra database for a music app. The purpose of the NoSQL database is to answer queries on song play data.

## Project Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can create queries on song play data to answer the questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

## Datasets

For this project, you'll be working with one dataset: **event_data**. The directory of CSV files is partitioned by date. Here are examples of filepaths to two files in the dataset:

>**event_data/2018-11-08-events.csv**<br>
>**event_data/2018-11-09-events.csv**

Below is an example of what an original single event data file, **2018-11-08-events.csv**, looks like.

```
{
    "artist": "Slipknot", 
    "auth": "Logged In", 
    "firstName": "Aiden", 
    "gender": "M", 
    "itemInSession": 0, 
    "lastName": "Ramirez", 
    "length": 192.57424, 
    "lvevel": "paid", 
    "location": "New York-Newark-Jersey City,NY-NJ-PA"
    "method": "PUT"    
    "page": "NextSong"
    "regisgration":1.54028E+12
    "sessionId":19
    "song":"Opinum Of The People"
    "status":200
    "ts":1.5416E+12
    "userId":20    
}
```

## Pre-Processing the raw data

For this project the separate data files will be merged into one single file event_datafile_new.csv, located within the workspace directory.
The event_datafile_new.csv contains the following columns:

- artist
- firstName of user
- gender of user
- item number in session
- last name of user
- length of the song
- level (paid or free song)
- location of the user
- sessionId
- song title
- userId

The image below is a screenshot of what the denormalized data appears like in the event_datafile_new.csv after the pre-processing has been executed:<br>

<img src="images/image_event_datafile_new.jpg">

## Modeling the Apache Cassandra database

The Apache Cassandra database is modeled such that the following questions can be answered:

**Query 1:** Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4.

**Query 2:** Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182.

**Query 3:** Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'.

Details are described in the Jupyter notebook **Project_1B_Project_Template.ipynb**.
