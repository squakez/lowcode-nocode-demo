# Policy Microservice

A REST API used to perform read only operations for Policies. Backed by a NoSQL database.

## Init database

Connect to Azure and create a database/container PolicyDB/SampleContainer. Upload the policies in `policies.json` files to feed the demo DB.

## Run Policy MS

```
kamel run policy.yaml
```

Connect to the exposed service via REST API:

```
http http://policy-ms/policies
```