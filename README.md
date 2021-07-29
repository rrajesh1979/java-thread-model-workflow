# java-thread-model-workflow

## This project will demonstrate IoT data processing using a Java multi-threaded model. We will explore
1. Complexities arising from a multi-threading approach
2. Synchronization challenges 
3. Code complexity
4. Complexity in handling failure, distributed deployment, state persistence etc.

## Workflow definition
1. Sensor data available in Kafka topic
Temperature sensor
Payload will be
{
SensorID,
RegionID,
Lat, Long,
Sensor Reading: {
  type: String, //Temp, Humidity, dew point, air pressure
  reading: Float,
  units: String
  }
}

2. Stage 1: Read data from Kafka topic and pass thru data clean-up and transformation
- Convert all data to Farenheit
- Discard any data missing sensor reading or other critical data point

3. Stage 2: Data enrichment - call Open Geocoding API
Add address by reverse engineering from Lat/Long

4. Stage 3: Write to another Kafka topic for anomaly detection component to pick-up

6. Stage 4a: Mock anomaly detection component reads from Kafka topic and logs anomalies

7. Stage 4b: Mock metics component - creates average and histogram of data available over an hourly period

8. Stage 4c: Persist data into AWS S3
9. Stage 4d: Persist data into MongoDB
10. Stage NNN: can be added / extended

