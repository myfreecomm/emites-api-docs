# Terminais

## Criação de terminal

Para criar um terminal, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/CNPJ${:cnpj}IE${:ie}/terminals</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  http://app.homologation.emites.com.br/api/v1/organizations/CNPJ22769530000131IE772733700120/terminals \
  -H 'authorization: Bearer c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
        "terminal": {
	      "name": "ABC001",
		    "id_pos": "xxxxyyy001",
		    "nfce_online_serial_number": 233,
		    "nfce_contingency_serial_number": 765,
		    "cashier_number": "001",
		    "ip": "127.0.0.1",
		    "sats_attributes": [
			    {
				    "activation_code": "123456789",
				    "device_serial": "123",
				    "sat_device_model": "SDK-1000"
			    }
		    ]
	    }
    }'


EXEMPLO DE RESPOSTA

{
  "id": "7039ea4c-1ecc-478a-8218-1dbb5a4fa483",
  "organization_id": "886dbbeb-801e-4d2f-a81f-358754a1195c",
  "name": "ABC002",
  "id_pos": "xxxxyyy002",
  "status": "inactivated",
  "terminal_type": "pc",
  "token": "b82efa9181f689138ab76791bcc55400",
  "created_at": "2020-02-07T14:57:03.773Z",
  "updated_at": "2020-02-07T14:57:03.773Z",
  "sat_device_id": null,
  "contingency_serial": null,
  "discarded_at": null,
  "notified_at": null,
  "online_serial": null,
  "online_last_number": null,
  "contingency_last_number": null,
  "ip": "127.0.0.2",
  "sat_emission": false,
  "datasource_url": "jdbc:sqlite:file:emites.db",
  "cashier_number": "002",
  "nfce_online_serial_id": "eb2f81bd-a1ee-4a58-8051-d9bac1bd734f",
  "nfce_contingency_serial_id": "63e1c52a-90c1-435b-b0b9-197bb9d033c8",
  "ipc_acceptor": null,
  "ipc_taxengine": null,
  "ipc_publisher": null,
  "nfe_online_serial_id": null,
  "client_version_update": false,
  "sats": [
    {
      "id": "427f3aaf-5842-4291-aca9-15349f453fcf",
      "uri": "file:///opt/local/emites-client/libsat.so",
      "activation_code": "123456789",
      "priority": null,
      "device_serial": "123",
      "terminal_id": "7039ea4c-1ecc-478a-8218-1dbb5a4fa483",
      "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
      "created_at": "2020-02-07T14:57:03.777Z",
      "updated_at": "2020-02-07T14:57:03.777Z",
      "access_key_validator": null
    }
  ]
}

EXEMPLO DE RETORNO DE ERROS

{
  "errors": {
    "messages": {
      "id_pos": [
        "já está em uso"
      ],
      "cashier_number": [
        "já está em uso"
      ],
      "ip": [
        "já está em uso"
      ]
    }
  }
}

```

    Campo                         |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
----------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    name                          |  Sim          |     Text                |                              | Identificação do terminal
    id_pos                        |  Sim          |     Texto               |   Até 51 caracteres          | Série/identificador do terminal
    cashier_number                |  Sim          |     Texto               |   /\A\d{3}\z/                | Número do caixa
    nfce_online_serial_number     |  Sim          |     Numérico            |                              | Número da série de emissão online
    nfce_contingency_serial_number|  Sim          |     Numérico            |                              | Número da série de emissão offline (Contingência)
    ip                            |  Não          |     Texto               |                              | IP
    client_version_update         |  Não          |     Booleano            |                              | Flag para atualização da versão do Emites Client
    sat_emission                  |  Não          |     Booleano            |                              | Flag para informar se SAT/MFE é a emissão principal

#### sats

Grupo de informações relacionadas ao disposito SAT/MFE do terminal. Seus atributos são:

    Campo                       |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    sat_device_model            |  Sim          |  Texto                  |   ["SDK-1000", "MDK-1000 L"] | Modelo do dispositivo SAT/MFE
    activation_code             |  Sim          |  Texto                  |                              | Código de ativação
    device_serial               |  Sim          |  Texto                  |                              | Série do dispositivo
    access_key_validator        |  Não          |  Texto                  |   UUID4                      | Obrigatório somente para MFE
    priority                    |  Não          |  Numérico               |                              | Prioridade/Ordenação do dispositivo

## Atualização de Terminais

Para atualizar um terminal, é necessário realizar uma requisição PUT para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PUT</i>
        <h6>/api/v1/organizations/CNPJ{:cnpj}IE{:ie}/terminals/{:terminal_id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO

curl -X PUT \
  http://app.homologation.emites.com.br/api/v1/organizations/CNPJ22769530000131IE772733700120/terminals/d4b6f53d-c6b9-47a9-a256-5db679ccc8e4 \
  -H 'authorization: Bearer c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
	      "terminal": {
		      "name": "ABC007",
		      "id_pos": "xxxxxx001",
		      "nfce_online_serial_number": 233,
		      "nfce_contingency_serial_number": 765,
		      "cashier_number": "005",
		      "ip": "127.0.0.1",
		      "client_version_update": true,
		      "sats_attributes": [
			      {
				      "activation_code": "123456789",
				      "device_serial": "777",
				      "sat_device_model": "SDK-1000"
			      }
		      ]
	      }
      }
    }'


EXEMPLO DE RESPOSTA

{
  "organization_id": "886dbbeb-801e-4d2f-a81f-358754a1195c",
  "id_pos": "xxxxyyy001",
  "name": "ABC007",
  "terminal_type": "pc",
  "sat_emission": false,
  "client_version_update": true,
  "ip": "127.0.0.1",
  "cashier_number": "005",
  "datasource_url": "jdbc:sqlite:file:emites.db",
  "nfce_online_serial_id": "eb2f81bd-a1ee-4a58-8051-d9bac1bd734f",
  "nfce_contingency_serial_id": "63e1c52a-90c1-435b-b0b9-197bb9d033c8",
  "nfe_online_serial_id": null,
  "id": "d4b6f53d-c6b9-47a9-a256-5db679ccc8e4",
  "status": "inactivated",
  "token": "fafc11a7d96d20423641ddc8e9002a0c",
  "created_at": "2020-02-07T14:29:50.452Z",
  "updated_at": "2020-02-07T16:07:17.518Z",
  "sat_device_id": null,
  "contingency_serial": null,
  "discarded_at": null,
  "notified_at": null,
  "online_serial": null,
  "online_last_number": null,
  "contingency_last_number": null,
  "ipc_acceptor": null,
  "ipc_taxengine": null,
  "ipc_publisher": null,
  "sats": [
    {
      "terminal_id": "d4b6f53d-c6b9-47a9-a256-5db679ccc8e4",
      "id": "7c374ab9-ddb4-4215-b7db-37957f54639c",
      "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
      "priority": null,
      "activation_code": "123456789",
      "device_serial": "123",
      "access_key_validator": null,
      "uri": "file:///opt/local/emites-client/libsat.so",
      "created_at": "2020-02-07T14:29:50.455Z",
      "updated_at": "2020-02-07T14:29:50.455Z"
    },
    {
      "id": "06d14c89-e380-4685-a53c-f1b3ddaa8394",
      "uri": "file:///opt/local/emites-client/libsat.so",
      "activation_code": "123456789",
      "priority": null,
      "device_serial": "777",
      "terminal_id": "d4b6f53d-c6b9-47a9-a256-5db679ccc8e4",
      "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
      "created_at": "2020-02-07T16:07:17.503Z",
      "updated_at": "2020-02-07T16:07:17.503Z",
      "access_key_validator": null
    }
  ]
}

EXEMPLO DE RETORNO DE ERROS

{
  "errors": {
    "messages": {
      "cashier_number": [
        "não é válido"
      ],
      "nfce_online_serial_id": [
        "não pode ficar em branco"
      ],
      "nfce_online_serial_number": [
        "não pode ficar em branco"
      ]
    }
  }
}
```

    Campo                         |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
----------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    name                          |  Sim          |     Text                |                              | Identificação do terminal
    id_pos                        |  Sim          |     Texto               |   Até 51 caracteres          | Série/identificador do terminal
    cashier_number                |  Sim          |     Texto               |   /\A\d{3}\z/                | Número do caixa
    nfce_online_serial_number     |  Sim          |     Numérico            |                              | Número da série de emissão online
    nfce_contingency_serial_number|  Sim          |     Numérico            |                              | Número da série de emissão offline (Contingência)
    ip                            |  Não          |     Texto               |                              | IP
    client_version_update         |  Não          |     Booleano            |                              | Flag para atualização da versão do Emites Client
    sat_emission                  |  Não          |     Booleano            |                              | Flag para informar se SAT/MFE é a emissão principal

#### sats

Grupo de informações relacionadas ao disposito SAT/MFE do terminal. Seus atributos são:

    Campo                       |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    sat_device_model            |  Sim          |  Texto                  |   ["SDK-1000", "MDK-1000 L"] | Modelo do dispositivo SAT/MFE
    activation_code             |  Sim          |  Texto                  |                              | Código de ativação
    device_serial               |  Sim          |  Texto                  |                              | Série do dispositivo
    access_key_validator        |  Não          |  Texto                  |   UUID4                      | Obrigatório somente para MFE
    priority                    |  Não          |  Numérico               |                              | Prioridade/Ordenação do dispositivo


## Exclusão de Terminais

Para excluir um terminal da organização, é necessário realizar uma requisição DELETE para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-warning">DELETE</i>
        <h6>/api/v1/organizations/CNPJ{:cnpj}IE{:ie}/terminals/{:terminal_id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X DELETE \
  http://app.homologation.emites.com.br/api/v1/organizations/CNPJ22769530000131IE772733700120/terminals/d7d6e731-df61-4b0d-9468-29c09b295391 \
  -H 'authorization: Bearer c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json'
```

## Listagem de Terminais

Para listar todas os terminais de uma organização, é necessário realizar uma requisição GET para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>api/v1/organizations/CNPJ{:cnpj}IE{:ie}/terminals</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X GET \
  http://app.homologation.emites.com.br/api/v1/organizations/CNPJ22769530000131IE772733700120/terminals \
  -H 'authorization: Bearer c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```

```shell
EXEMPLO DE RESPOSTA
[
  {
    "id": "d4b6f53d-c6b9-47a9-a256-5db679ccc8e4",
    "organization_id": "886dbbeb-801e-4d2f-a81f-358754a1195c",
    "name": "ABC001",
    "id_pos": "xxxxyyy001",
    "status": "inactivated",
    "terminal_type": "pc",
    "token": "fafc11a7d96d20423641ddc8e9002a0c",
    "created_at": "2020-02-07T14:29:50.452Z",
    "updated_at": "2020-02-07T14:29:50.452Z",
    "sat_device_id": null,
    "contingency_serial": null,
    "discarded_at": null,
    "notified_at": null,
    "online_serial": null,
    "online_last_number": null,
    "contingency_last_number": null,
    "ip": "127.0.0.1",
    "sat_emission": false,
    "datasource_url": "jdbc:sqlite:file:emites.db",
    "cashier_number": "001",
    "nfce_online_serial_id": "eb2f81bd-a1ee-4a58-8051-d9bac1bd734f",
    "nfce_contingency_serial_id": "63e1c52a-90c1-435b-b0b9-197bb9d033c8",
    "ipc_acceptor": null,
    "ipc_taxengine": null,
    "ipc_publisher": null,
    "nfe_online_serial_id": null,
    "client_version_update": false,
    "sats": [
      {
        "id": "7c374ab9-ddb4-4215-b7db-37957f54639c",
        "uri": "file:///opt/local/emites-client/libsat.so",
        "activation_code": "123456789",
        "priority": null,
        "device_serial": "123",
        "terminal_id": "d4b6f53d-c6b9-47a9-a256-5db679ccc8e4",
        "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
        "created_at": "2020-02-07T14:29:50.455Z",
        "updated_at": "2020-02-07T14:29:50.455Z",
        "access_key_validator": null
      }
    ]
  },
  ...
]
```

## Consulta de Terminais

Para listar um terminal da organização, é necessário realizar uma requisição GET para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>api/v1/organizations/CNPJ{:cnpj}IE{:ie}/terminals/{:terminal_id}</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:

```shell
EXEMPLO DE REQUISIÇÃO
curl -X GET \
  http://app.homologation.emites.com.br/api/v1/organizations/CNPJ22769530000131IE772733700120/terminals/d7d6e731-df61-4b0d-9468-29c09b295391 \
  -H 'authorization: Bearer c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
```

```shell
EXEMPLO DE RESPOSTA
{
  "id": "d7d6e731-df61-4b0d-9468-29c09b295391",
  "organization_id": "886dbbeb-801e-4d2f-a81f-358754a1195c",
  "name": "ABC007",
  "id_pos": "xxxxyyy001",
  "status": "inactivated",
  "terminal_type": "pc",
  "token": "73c7aaf05da0f2bf20e1381ce891c6d3",
  "created_at": "2020-02-07T14:27:09.368Z",
  "updated_at": "2020-02-07T14:27:56.889Z",
  "sat_device_id": null,
  "contingency_serial": null,
  "discarded_at": null,
  "notified_at": null,
  "online_serial": null,
  "online_last_number": null,
  "contingency_last_number": null,
  "ip": "127.0.0.1",
  "sat_emission": false,
  "datasource_url": "jdbc:sqlite:file:emites.db",
  "cashier_number": "005",
  "nfce_online_serial_id": "eb2f81bd-a1ee-4a58-8051-d9bac1bd734f",
  "nfce_contingency_serial_id": "63e1c52a-90c1-435b-b0b9-197bb9d033c8",
  "ipc_acceptor": null,
  "ipc_taxengine": null,
  "ipc_publisher": null,
  "nfe_online_serial_id": null,
  "client_version_update": false,
  "sats": [
    {
      "id": "f4777547-8ffd-4554-a78f-9adfee8bec97",
      "uri": "file:///opt/local/emites-client/libsat.so",
      "activation_code": "123456789",
      "priority": null,
      "device_serial": "123",
      "terminal_id": "d7d6e731-df61-4b0d-9468-29c09b295391",
      "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
      "created_at": "2020-02-07T14:27:09.375Z",
      "updated_at": "2020-02-07T14:27:09.375Z",
      "access_key_validator": null
    },
    {
      "id": "bd442833-20ab-4c0a-b339-63e7a59b295e",
      "uri": "file:///opt/local/emites-client/libsat.so",
      "activation_code": "123456789",
      "priority": null,
      "device_serial": "777",
      "terminal_id": "d7d6e731-df61-4b0d-9468-29c09b295391",
      "sat_device_id": "810b922f-db26-455a-a5e0-7e17198a7240",
      "created_at": "2020-02-07T14:27:56.877Z",
      "updated_at": "2020-02-07T14:27:56.877Z",
      "access_key_validator": null
    }
  ]
}
```
