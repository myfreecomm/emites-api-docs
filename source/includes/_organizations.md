# Organizações

## Listagem de Organizações

Para listar todas as organizações da conta, é necessário realizar uma requisição GET para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>api/v1/organizations</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X GET \
  http://localhost:3000/api/v1/organizations \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```

```shell
EXEMPLO DE RESPOSTA
{
    "organizations": [
        {
            "id": 1,
            "document": "12345678000000",
            "name": "Fulano de tal",
            "inscricao_municipal": "123456",
            "company_name": "F Comp",
            "email": "fulano.de.tal@nexaas.com",
            "logo_file_name": null,
            "logo_url": "",
            "address": {
                "address": "Rua 1",
                "city": "Rio de Janeiro",
                "city_code": "3301009",
                "complement": "-",
                "district": "Parque 2",
                "number": "119",
                "phone": "21999999999",
                "state": "RJ",
                "zipcode": "28000200"
            },
            "inscricao_estadual": "123456",
            "codigo_regime_tributario": "simples_nacional",
            "regime_tributario_diferenciado": "LFEM",
            "cnae": "14.02/951180002",
            "csc_id": "120",
            "csc_token": "Lorem Ipsum",
            "certificate_expires_at": null,
            "certificate": null
        }
    ]
}
```

## Consulta de Organizações

Para listar uma organização da conta, é necessário realizar uma requisição GET para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>api/v1/organizations/{:organization_id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X GET \
  http://localhost:3000/api/v1/organizations \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```

```shell
EXEMPLO DE RESPOSTA
{
    "organization": {
        "id": 1,
        "document": "12345678000000",
        "name": "Fulano de tal",
        "inscricao_municipal": "123456",
        "company_name": "F Comp",
        "email": "fulano.de.tal@nexaas.com",
        "logo_file_name": null,
        "logo_url": "",
        "address": {
            "address": "Rua 1",
            "city": "Rio de Janeiro",
            "city_code": "3301009",
            "complement": "-",
            "district": "Parque 2",
            "number": "119",
            "phone": "21999999999",
            "state": "RJ",
            "zipcode": "28000200"
        },
        "inscricao_estadual": "123456",
        "codigo_regime_tributario": "simples_nacional",
        "regime_tributario_diferenciado": "LFEM",
        "cnae": "14.02/951180002",
        "csc_id": "120",
        "csc_token": "Lorem Ipsum",
        "certificate_expires_at": null,
        "certificate": null
    }
}
```
