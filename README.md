# Project: Sparkify Data Modeling with Postgres

## Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

## Resolution
In order to resolve such a problem I created an ETL pipeline for data analysis. Sparkify provided datasources, thus ETL reads data from datasources and formats them in an specific way before saving the modeled data into postgres table.

## Data Modeling
Data were modeled into a Star schema with the following fact and dimension tables:
### Fact Table
songplay

`songplay_id start_time, user_id, level, song_id, artist_id, session_id, location, user_agent`

### Dimensions Tables
users

`user_id, first_name, last_name, gender, level`

songs

`song_id, title, artist_id, year, duration`

artists

`artist_id, name, location, latitude, longitude`

time

`start_time, hour, day, week, month, year, weekday`

## Project Structure
```
├── README.md
├── create_tables.py
├── data
│   ├── log_data
│   │   └── 2018
│   │       └── 11
│   └── song_data
│       └── A
│           ├── A
│           │   ├── A
│           │   ├── B
│           │   └── C
│           └── B
│               ├── A
│               ├── B
│               └── C
├── etl.ipynb
├── etl.py
├── sql_queries.py
└── test.ipynb

14 directories, 6 files
```

`create_tables.py` should be executed in order to create the start database table shema. This file uses sql queries written within the `sql_queries.py` file.

`etl.ipynb` is a jupyter notebook with the project guidethrough. All code within this file is also within `etl.py` -- clearly in a more organised way.

`etl.py` is the etl pipeline itself. It reads data from `data/` and saves them in the postgres database tables.

`sql_queries.py` contains sql queries to create, insert, drop and select from the database.

`test.ipynb` should be run to asure you the data has been saved accordingly.

## Run the Project
Once you clone this repository you should proceed as follows:

Run create_tables.py file:

    python create_tables.py

Run etl.py file:

    python etl.py

And last but not least, run jupyter notebook to be able to run test.ipynb. It will make sure tables were created and data saved in your database.

## Constrains
You need to run a postgres database locally. Docker is a great tool to run your local postgres db.

## Greetings
Made with Love in Malta

Wagner de Lima