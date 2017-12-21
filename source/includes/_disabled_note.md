# Inutilização de número de nota

Para inutilizar um número, envie a seguinte requisição:  

 
<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/disable</h6>
    </div>
</div> 

```shell
curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfe/disable \
    -H 'authorization: Token token=$YOUR_API_TOKEN' \
    -H 'content-type: application/json' \
    -d '{
            "nfe": {
                "uf": "35",
                "cnpj_emitente": "12345678912345",
                "serie": "1",
                "numero": "9999999999"
            }
        }'
```