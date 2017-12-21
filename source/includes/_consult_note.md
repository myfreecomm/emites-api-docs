# Consulta de nota  

Para consultar uma nota é necessário realizar a seguinte requisição:  


<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}  </h6>
    </div>
</div>


  ```shell
curl -X GET \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990 \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \
  ```