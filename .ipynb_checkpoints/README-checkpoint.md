# sqlalchemy-challenge

## Climate (Part 1)

Using sqlalchemy, I connected to the hawaii.sqlite file which is a sqlite DB. 
From there, using Python's sqlalchemy, I reflected the database by connecting to
the main "engine" (which points to the sqlite file).

After identifying the classes that automap found (meaurement, and station), I 
create references to the two names as Measurement and Station respectively.

Then a session is initiated by connecting to the engine, which now allows for
querying the sqlite file. 

Using the query functions of sqlalchemy, such as session.query, func.max, <Class>.<attribute>, I queried the DB for precipitation data, and used pandas plot function to plot precipitation in inches over the last year (of data available in the sqlite file). 

Then, querying for all stations, I use func.count to find the number of data points
available for each of the stations, sort in descending order, then slice the
list of stations by count to find the station with the highest count 
observation (USC00519281).

Using more func functions, I find the min, max, and avg of temperatures. 

Then, using the temperature data across the last 12 months (from the most
recent date available in the sqlite file), I create a histogram with pandas
hist function. 

Finally the session is closed, disconnecting from the sqlite DB file. 



## Flask App (part 2)

Repeating most of the steps from part 1:

1. create an engine to sqlite
2. reflect the database metadata into Base
3. get the classes (station and measurement)
4. start a session to engine
5. query for the following
   1. most_recent_date_dt (most recent date available in the sqlite DB)
   2. most_observed_station (station with the highest occurence count in the sqlite DB)
   3. twelve_months_ago (date 12 months prior to most_recent_date_dt)
  
I think create a Flask app under `app` that uses the current __name__ as the base. 

Structured as follows:

1. homepage, where all available routes are listed and linked. The links to /<start> and /<start>/<end> don't necessarily work, and need to be manually modified using YYYY-MM-DD formatting ex: "./api/v1.0/2010-01-01/2011-01-01" where "." is the beginning url to the app
2. precipitation gathers the precipitation from the 12 most recent months of data
3. stations lists all of the stations from the dataset
4. tobs returnes the temperature observations for the most active station over the last year
5. start_date returns the min, max, and avg temperatures from the date provided in the format YYYY-MM-DD
6. start_end_date returns the min, max, and avg temperatures from the date provided in the format YYYY-MM-DD up to the second date provided in the format YYYY-MM-DD

## Conclusion

Not an overly difficult assignment. Just needed to look up documentation for some of the functions regarding aggregation in sqlite, as well as how to link within a python-flask application. 