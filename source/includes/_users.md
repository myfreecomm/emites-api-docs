# Usuários

## Exclusão de Usuário

Para excluir um usuário da conta, é necessário realizar uma requisição DELETE para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-warning">DELETE</i>
        <h6>/api/v1/users/{:user_id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X DELETE \
  http://localhost:3000/api/v1/users/1 \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \

EXEMPLO DE RETORNO DE ERROS

{
    "errors": { "base": "Não foi possível remover usuário." },
    "error_details": [
        {
            "base": [
                { "error": "default" }
            ]
        }
    ]
}

```
