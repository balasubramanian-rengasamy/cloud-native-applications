# Helidon  MP Jaeger Example

This example demonstrates how Jaeger can be used for tracing in a Helidon MP application 

# Clone the Repository

Clone the git https://github.com/jobinesh/cloud-native-applications.git
Navigate to helidon-example-mp-jaeger

# Start the Jaeger via Docker

```
docker run --rm -it --name jaeger \
  -p 5778:5778 \
  -p 16686:16686 \
  -p 14268:14268 \
  jaegertracing/all-in-one:1.14  
```
## Build and run the application

With JDK8+
```bash
mvn package
java -jar target/helidon-example-mp-jaeger.jar
```

## Exercise some of the application APIs to generate traces

```
curl -X GET http://localhost:8080/greet
{"message":"Hola World!"}

curl -X GET http://localhost:8080/greet/Joe
{"message":"Hola Joe!"}

curl -X PUT -H "Content-Type: application/json" -d '{"greeting" : "Namaste"}' http://localhost:8080/greet/greeting

curl -X GET http://localhost:8080/greet/Jose
{"message":"Namaste Jose!"}
```

## View the API tracing with Jaegar

In order to view the API call tracing for the above API calls with Jaeger UI, open a browser and navigate to the following URL:
http://localhost:16686/search
- You will see a search panel on left side of the UI. 
- Set serach parameters as appropiate or leave the default values as is and click on Find Traces. 
- You will see all traces appearing on right side of the search panel !

Have fun !
