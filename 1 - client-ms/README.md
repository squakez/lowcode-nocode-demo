# Client Microservice

A REST API used to perform CRUD operations for Clients. Backed by a SQL database.

## Create database secret

```
oc create secret generic my-datasource --from-file datasource.properties
```

## Init database client table

Connect to database and execute:

```
CREATE TABLE customers (
	name TEXT PRIMARY KEY,
	city TEXT NOT NULL
);
```

## Run Client-MS

```
kamel run client.yaml
```

Connect to the exposed service via REST API:

```
http http://client-ms/customers
http POST http://client-ms/customers name=Pasquale city=Madrid
...
```