# Create Policy Event

A Connector-style application used to sink data to an AWS Kinesis stream. It exposes a webtoken used by UI to pass information about a CreatePolicy event. The event is transformed to Avro data format according to a schema provided in APICurio Registry.

## Store the schema in Apicurio registry

Connect to http://192.168.49.2:32060/ui/artifacts and store the schema in `avro.json` file.

## Create a Kamelet (Connector)

Create the Kamelet action connector to validate the event with a given schema provided by APICurio Registry.

```
oc apply -f avro-serial.kamelet.yaml
```

## Run the connector

```
oc apply -f push-policy-event.yaml
```

## Push a create Policy event

http post http://push-policy/webhook name=pasquale3 city=Madrid policyid=basic

Show the data stream in AWS Kinesis