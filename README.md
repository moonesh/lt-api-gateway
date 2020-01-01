# GATEWAY-API

## RUN THE FOLLOWING STEPS >>> AFTER POSITION-TRACKER 

1. Build Docker Image of position-tracker [mooneshkachroo/api-gateway:0.0.1-RELEASE] 


2. Previously you ran mongo container : docker run -d -p 27017:27017 --name mongodb --network locationtracker mongo:3.6.5-jessie
3. Previously you ran position-tracker: docker run -d -p 8090:8090 --name positiontracker --network locationtracker --env spring.activemq.broker-url=tcp://myqueue:61616 --env fleetman.position.queue=positionQueue --env spring.data.mongodb.host=mongodb mooneshkachroo/position-tracker:0.0.1-RELEASE


4.NOW RUN APIGATEWAY: docker run -d -p 8080:8080 --name apigateway --network locationtracker --env position-tracker-url=http://positiontracker:8090 mooneshkachroo/api-gateway:0.0.1-RELEASE

5. Check if the messages are being pushed at: http://localhost:8080/history/Secret Service A
 
  

