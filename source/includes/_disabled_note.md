# Inutilização de número de nota

Para inutilizar um número, envie a seguinte requisição:  

POST /api/v1/organizations/{organization_id}/nfe/disable  

```shell
curl -X POST \
  http://emites-sandbox.herokuapp.com/api/v1/organizations/11/nfe/disable \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db05aasas' \
    -H 'cache-control: no-cache' \
    -H 'content-type: application/json' \
    -H 'postman-token: 79bb907b-95ac-5261-bfc1-d772c6514a0b' \
    -d '{
            "nfe": {
                "uf": "35",
                "cnpj_emitente": "12345678912345",
                "serie": "1",
                "numero": "9999999999"
            }
        }'
```