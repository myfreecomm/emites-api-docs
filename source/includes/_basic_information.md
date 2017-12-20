# Informaçães básicas

<!-- ## Introdução


O Emites possui uma API REST para interagir com seus recursos, através de objetos JSON sobre HTTP, usando todos principais verbos HTTP (GET, POST, PATCH, DELETE). Cada recurso possui sua própria URL e pode ser manipulado de maneira isolada, tentando assim seguir os princípios REST ao máximo. -->


## Autenticação


Todo acesso à API é feito do ponto de vista de uma conta existente no Emites. Assim sendo, toda requisição à API deverá ser autenticada. A autenticação é feita via token, que deve ser informado no header de cada requisição efetuada.

Para todas as requisições são necessários os seguintes Headers:

"Authorization": "Token token=123",  
"Content-Type": "application/json"



  ```shell
  Formato JSON

  EXEMPLO DE REQUISIÇÃO

    curl -X GET \
      http://localhost:3000/api/v1/organizations \
      -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec7101010' \
      -H 'cache-control: no-cache' \
      -H 'content-type: application/json' 

  EXEMPLO DE RESPOSTA

  {
    "chave": "valor"
  }

  ```

