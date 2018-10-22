# Inutilização

## Inutilização de NF-e

Para inutilizar um número de NF-e, envie a seguinte requisição:  

 
<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/disable</h6>
    </div>
</div> 

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfe/disable \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \
    -d '{
          "nfe": {
            "uf": "35",
            "serie": "1",
            "numero": "9999999999"
          }
        }'


EXEMPLO DE RESPOSTA

{
  "status": "Inutilização de número solicitada à SEFAZ"
}

```

## Inutilização de NFC-e

Para inutilizar um número de NFC-e, envie a seguinte requisição:  


<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfce/disable</h6>
    </div>
</div> 

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfce/disable \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \
    -d '{
          "nfce": {
            "uf": "35",
            "serie": "1",
            "numero": "9999999999"
          }
        }'


EXEMPLO DE RESPOSTA

{
  "status": "Inutilização de número solicitada à SEFAZ"
}
```