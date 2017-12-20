#Cancelamento de nota

Para cancelar uma nota, envie a seguinte requisição:  

PATCH /api/v1/organizations/{organization_id}/nfe/{nfe_id}/cancel  

  ```shell
curl -X PATCH \
    http://emites-sandbox.herokuapp.com/api/v1/organizations/11/nfe/10990/cancel \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db05aasas' \
    -H 'cache-control: no-cache' \
    -H 'content-type: application/json' \
    -H 'postman-token: 065c1276-5de2-c115-11b1-2fa643b500b8'
  ```