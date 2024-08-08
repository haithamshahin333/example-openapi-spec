# example-openapi-spec

## Simple Commands to Register APIs

## Concepts

APIs
    -> Version 1 (lifecycle, definition)
    -> Version 2 (lifecycle, definition)
    ---
    -> Deployments (version/defn, environment)
    

```bash

# initial registering of api based on spec
az apic api register -g $RG_NAME -n $API_CENTER_NAME -l spec/petstore.yaml --environment-id azure-dev-aks

az apic api update -g $RG_NAME -n $API_CENTER_NAME --api-id petstore --custom-properties ./spec/petstore-properties.yaml

az apic api deployment create -g $RG_NAME -n $API_CENTER_NAME --api-id petstore --deployment-id dev-deployment --definition-id /workspaces/$API_CENTER_NAME/apis/petstore/versions/1-0-11/definitions/openapi --environment-id /workspaces/$API_CENTER_NAME/environments/azure-dev-aks --title dev-deployment --server "{runtime-uri:['http://localhost/petstore/api']}"
```