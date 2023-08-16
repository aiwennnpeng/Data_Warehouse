# Data-Warehouse
## Introduction
A music streaming startup, Sparkify, aims to shift its user activity and song data from S3 to the cloud. 

As their data engineer, I'm tasked with building an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights into what songs their users are listening to.

## Song dataset
It is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.  
Example:
```
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
```

## Log Dataset
This consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings.

The log files in the dataset you'll be working with are partitioned by year and month. For example, here are file paths to two files in this dataset.
Example:
```
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json
```

## Schema for Song Play Analysis
Utilizing the song and event datasets, your objective is to construct a star schema that's fine-tuned for efficient song-play analysis queries. This includes the following tables:
#### Fact Table
songplays - records in event data associated with song plays  
i.e. records with page NextSong
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
#### Dimension Tables
users - users in the app  
user_id, first_name, last_name, gender, level
songs - songs in music database
song_id, title, artist_id, year, duration
artists - artists in music database
artist_id, name, location, lattitude, longitude
time - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday
