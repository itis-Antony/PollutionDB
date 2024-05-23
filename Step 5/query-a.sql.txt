-- Selecting the date_time, station_name, and maximum NOx reading for each monitor station within a specific date range

SELECT 
    air_quality_reading.date_time,  
    monitor_station.station_name,  
    MAX(air_quality_reading.nox) AS max_nox
FROM 
    air_quality_reading 
INNER JOIN 
    monitor_station ON air_quality_reading.site_id = monitor_station.site_id -- Joining the air quality reading table with the monitor station table based on the site ID
WHERE 
    air_quality_reading.date_time BETWEEN '2022-01-01 00:00:00' AND '2022-12-31 23:59:59' -- Filtering the readings for a specific date range
GROUP BY 
    air_quality_reading.site_id, monitor_station.station_name; -- Grouping the results by site ID and station name to get the max NOx reading for each monitor station
