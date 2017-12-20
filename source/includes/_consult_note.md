# Consulta de nota  

Para consultar uma nota é necessário realizar a seguinte requisição:  

GET /api/v1/organizations/{organization_id}/nfe/{nfe_id}  


  ```shell
curl -X GET \
    http://emites-sandbox.herokuapp.com/api/v1/organizations/11/nfe/10990 \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db05a' \
    -H 'cache-control: no-cache' \
    -H 'content-type: application/json' \
    -H 'postman-token: 332205aa-2eec-a72b-c8df-a4381b9142f7'
  ```