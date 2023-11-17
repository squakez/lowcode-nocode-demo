# HDFC Demo

Install all microservices and show in Kaoto visual designer

## Use case scenario

Simulate a UI interface that will use a microservices oriented architecture to:

1. create a new profile for a Client on an on-prem PostgreSQL SQL database
2. connect an Azure CosmoDB NoSQL DB to get a list of Policies
3. connect to a suggestion engine legacy application simulated by a Java dependency (which may connect to any service in a legacy way)
4. push the event for a creation of a new Policy for a Client in AWS Kinesis stream formatting via Avro dataformat stored in an on prem APICurio Registry

## Execution example

Ephemeral services such as Client database and APICurio registry submission must be created every time we start a new cluster.

### Launch all services

```
# run the client microservice
kamel run client.yaml
# get the local service port
oc get svc client
# check service is running
http 192.168.49.2:31404/customers/
```

```
# run the policy microservice
kamel run policy.yaml
# get the local service port
oc get svc policy
# check service is running
http 192.168.49.2:31404/policies/
```

```
# run the suggestion engine microservice
kamel run suggestion-engine.yaml
# get the local service port
oc get svc suggestion-engine
# check service is running
http POST 192.168.49.2:31404/suggestions/best id=1
```

```
# run the create Policy event
oc apply -f avro-serial.kamelet.yaml
oc apply -f push-policy-event.yaml
# get the local service port
oc get svc push-policy-event
# check service is running
http POST 192.168.49.2:31404/webhook name=Pasquale city=Mumbai policyid=family
```

### Run the use case scenario

http POST 192.168.49.2:31404/customers/ name=Pasquale city=Bangalore
http 192.168.49.2:31404/customers/Pasquale
http 192.168.49.2:31404/policies/
http POST 192.168.49.2:31404/suggestions/best id=1
http POST 192.168.49.2:31404/webhook name=Pasquale city=Bangalore policyid=family