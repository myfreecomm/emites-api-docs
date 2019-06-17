# Gestão de séries de notas fiscais

Para criar séries de notas fiscais você precisa ter ao menos uma organização cadastrada.
<p>Você pode verificar como criar organizações em [Criação de organizações](#cria-o-de-organiza-es)</p>


## Criação de séries NF-e

Para criar uma série de NF-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe_numerations</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:  

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  http://localhost:3000/api/v1/organizations/1/nfe_numerations \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
      "nfe_numeration": {
        "serie": 1,
        "last_number": "100",
      }
    }'

EXEMPLO DE RESPOSTA

{
  "nfe_numeration": {
    "id": 1,
    "serie": 1,
    "last_number": 100,
    "created_at": "2019-01-31T14:05:11.733-03:00",
    "updated_at": "2019-01-31T14:05:11.733-03:00"
  }
}
```

    Campo                       |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    serie                       |  Sim          |     Numérico            |                              |                                                
    last_number                 |  Sim          |     Numérico            |                              |  

## Exclusão de séries NF-e

Para excluir uma série de NF-e, é necessário realizar uma requisição DELETE para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-warning">DELETE</i>
        <h6>/api/v1/organizations/{organization_id}/nfe_numerations/{id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO

curl -X DELETE \
  http://localhost:3000/api/v1/organizations/1/nfe_numerations/1 \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```

## Criação de séries NFC-e

Para criar uma série de NFC-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfce_numerations</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:  

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  http://localhost:3000/api/v1/organizations/1/nfce_numerations \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
      "nfce_numeration": {
        "serie": 1,
        "last_number": "100",
      }
    }'

EXEMPLO DE RESPOSTA

{
  "nfce_numeration": {
    "id": 1,
    "serie": 1,
    "last_number": 100,
    "created_at": "2019-01-31T14:05:11.733-03:00",
    "updated_at": "2019-01-31T14:05:11.733-03:00"
  }
}
```

    Campo                       |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    serie                       |  Sim          |     Numérico            |                              |                                                
    last_number                 |  Sim          |     Numérico            |                              |  

## Exclusão de séries NFC-e

Para excluir uma série de NFC-e, é necessário realizar uma requisição DELETE para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-warning">DELETE</i>
        <h6>/api/v1/organizations/{organization_id}/nfce_numerations/{id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO

curl -X DELETE \
  http://localhost:3000/api/v1/organizations/1/nfce_numerations/1 \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```
