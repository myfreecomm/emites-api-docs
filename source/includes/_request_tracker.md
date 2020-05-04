# Request Tracker (Request ID)

Para consultar as informações de um documento fiscal ou mais pelo ID da requisição (Request ID), é necessário realizar uma requisição GET para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/request_tracker/{request_id}</h6>
    </div>
</div>

```shell
EXEMPLO DE REQUISIÇÃO

curl --request GET \
  --url http://app.production.emites.com.br/api/v1/request_tracker/491dd276-b7d9-4623-beb1-234c66a80be3 \
  --header 'authorization: Bearer 6f42433270bc61d746556b17605db05a' \
  --header 'content-type: application/json'


EXEMPLO DE RESPOSTA
{
  "request_tracker": {
    "id": "491dd276-b7d9-4623-beb1-234c66a80be3",
    "nfces": [
      {
        "status": "processing",
        "id": 7569,
        "organization_id": 399
      }
    ]
  }
}
```
