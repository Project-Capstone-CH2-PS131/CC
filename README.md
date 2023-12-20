# API Gateway

API Gateway configuration.

## How to Deploy

Set project id and region.

``` bash
export PROJECT_ID='PROJECT_ID'
export REGION='REGION'
```

Upload API config.

```bash
gcloud api-gateway api-configs create api-gateway-v1 \
    --api service \
    --display-name 'Smart Fridge API' \
    --openapi-spec api_services.yml \
    --backend-auth-service-account 'service account' \
    --project $PROJECT_ID
```

Deploy to 'API Gateway'

```bash
gcloud api-gateway gateways update smart-fridge-api-gateway \
    --location $REGION \
    --display-name 'Smart Fridge API Gateway'
    --api-config api-gateway-v1
```