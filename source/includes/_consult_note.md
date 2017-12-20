# Consulta de nota  

Para consultar uma nota é necessário realizar a seguinte requisição:  

GET /api/v1/organizations/{organization_id}/nfe/{nfe_id}  


  ```shell
curl -X GET \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990 \
    -H 'authorization: Token token=$YOUR_API_TOKEN' \
    -H 'content-type: application/json' \
  ```