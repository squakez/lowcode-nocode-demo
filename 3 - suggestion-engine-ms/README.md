# Suggestion engine Microservice

A REST API used to wrap a legacy application. Backed by a legacy Java dependency (which could perform its own service communication/business logic).

## Run Policy MS

```
kamel run suggestion-engine.yaml
```

Connect to the exposed service via REST API:

```
http POST http://suggestion-engine-ms/suggestions/best id=xyz
```