#Cancelamento de nota

Para cancelar uma nota, envie a seguinte requisição:  

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PATCH </i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}/cancel </h6>
    </div>
</div>  

  ```shell
curl -X PATCH \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990/cancel \
    -H 'authorization: Token token=$YOUR_API_TOKEN' \
    -H 'content-type: application/json' \
  ```