# API Gateway

API Gateway configuration.

<img src=".\assets\images\architecture.png" />

## API Endpoint

### [POST] Register User
```
https://smart-fridge-api-gateway-79skkhn6.an.gateway.dev/v1/auth/register
```

### [POST] Login User
```
https://smart-fridge-api-gateway-79skkhn6.an.gateway.dev/v1/auth/login
```

### [POST] Upload Image and Get Recipes
```
https://smart-fridge-api-gateway-79skkhn6.an.gateway.dev/v1/core/ingredient
```

### [GET] Get Random Recipes
```
https://smart-fridge-api-gateway-79skkhn6.an.gateway.dev/v1/core/random-recipes
```

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