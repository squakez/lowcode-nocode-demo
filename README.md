# HDFC Demo

Install all microservices and show in Kaoto visual designer

## Use case scenario

Simulate a UI interface that will use a microservices oriented architecture to:

1. create a new profile for a Client on an on-prem PostgreSQL SQL database
2. connect an Azure CosmoDB NoSQL DB to get a list of Policies
3. connect to a suggestion engine legacy application simulated by a Java dependency (which may connect to any service in a legacy way)
4. push the event for a creation of a new Policy for a Client in AWS Kinesis stream formatting via Avro dataformat stored in an on prem APICurio Registry

