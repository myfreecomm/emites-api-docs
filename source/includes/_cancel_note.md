#Cancelamento de nota

Para cancelar uma nota, envie a seguinte requisição:  

PATCH /api/v1/organizations/{organization_id}/nfe/{nfe_id}/cancel  

  ```shell
curl -X PATCH \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990/cancel \
    -H 'authorization: Token token=$YOUR_API_TOKEN' \
    -H 'content-type: application/json' \
  ```