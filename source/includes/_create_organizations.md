# Criação de organizações

Para emissão de NF-e ou NFC-e, é necessário possuir ao menos uma organização criada no Emites. Para realizar a criação de uma organização via API, o processo consiste em dois passos:  

### 1º Passo: Criação da Organização  

Para criar uma organização, é necessário realizar uma requisição POST para o seguinte endereço:  

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:  

```shell
curl -X POST \
  http://localhost:3000/api/v1/organizations/ \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
      "organization": {
        "address": {
          "address": "Rua Gomes de Carvalho",
          "city": "São Paulo",
          "city_code": "812938",
          "complement": "Apto 74",
          "district": "Vila Olímpia da Realeza",
          "number": "55",
          "phone": "1133333333", 
          "state": "SP",
          "zipcode": "04547000" 
        },
        "codigo_regime_tributario": 1,
        "company_name": "The String",
        "document": "58521175000124", 
        "email": "foo@bar.com",

        "inscricao_estadual": "787811920",
        "inscricao_municipal": "13213213",
        "name": "MyString"
      }
    }'
```

### organization

Contém informações sobre a empresa emitente da NF-e. Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    codigo_regime_tributario    |  CRT            |  Não          |     Numérico            |   1 dígito                   |  1 = Simples Nacional;<br>2 = Simples Nacional, excesso sublimite de receita bruta;<br>3 = Regime Normal.  
    razao_social                |  xNome          |  Sim          |     Texto               |   Até 60 caracteres          |  
    cnpj                        |  CNPJ           |  Sim          |     Numérico            |   14 dígitos                 |  CNPJ da empresa emitente, somente números. 
    email                       |  email          |  Sim          |     Texto               |   Até 60 caracteres          |
    inscricao_estadual          |  IE             |  sim          |     Texto               |   Até 14 caracteres          |  Informar somente os algarismos, sem ponto, hífen, barra, etc. Na emissão de NF-e avulsa pode ser informado o texto ISENTO para os contribuintes do ICMS isentos de inscrição no cadastro de contribuintes do ICMS.  
    inscricao_municipal         |  IM             |  Não          |     Texto               |   Até 15 caracteres          |  
    nome_fantasia               |  xFant          |  Não          |     Texto               |   Até 60 caracteres          |  
 
### address  

Grupo de informações relacionadas ao endereço do emitente. Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|----------------------------------------------------------- 
    address                     |                 |               |                         |                              |
    city                        |   xMun          |  Sim          |  Texto                  |   Até 60 caracteres          |
    city_code                   |   cMun          |  Sim          |  Numérico               |   7 dígitos                  |  
    complement                  |   xCpl          |  Não          |  Texto                  |   Até 60 caracteres          |  
    district                    |                 |               |                         |                              |
    number                      |   nro           |  Sim          |  Texto                  |   Até 60 caracteres          |  
    phone                       |   fone          |  Não          |  Numérico               |  De 6 a 14 carateres         |  
    state                       |   UF            |  Sim          |  Texto                  |  2 caracteres                |
    zipcode                     |   CEP           |  Sim          |  Numérico               |  8 dígitos                   |

### 2º Passo: Atualização/Upload do Certificado da Organização

A inclusão de certificado digital vigente da organização é obrigatório para a emissão da nota. Para criar ou atualizar um certificado, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{:organization_id}/certificate</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:  

```shell
curl -X POST \
  http://localhost:3000/api/v1/organizations/8/certificate \
  -H 'authorization: Token token=c3b1164e8ae17f6d9712730ec75be6da' \
  -H 'content-type: application/json' \
  -d '{
        "password": "senhadocertificado",
        "file": "código em Base64 do arquivo PFX"
    }'
```


