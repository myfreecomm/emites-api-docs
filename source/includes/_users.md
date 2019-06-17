# Usuários

## Criação de Usuário

Para criar um usuário, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/users</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  http://localhost:3000/api/v1/users/ \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
      "users": {
        "email": "foo@bar.com",
      }
    }'


EXEMPLO DE RESPOSTA

{
  "user": {
    "id": 2,
    "name": "foo@bar.com",
    "email": "foo@bar.com",
    "auth_provider": "nexaas_id",
    "uuid": "1234",
    "created_at": "2019-06-17T09:51:51.558-03:00",
    "updated_at": "2019-06-17T09:51:51.558-03:00"
  }
}

```

    Campo                       |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    email                       |  Sim          |     Texto               |   Até 60 caracteres          |