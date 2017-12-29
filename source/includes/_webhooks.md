# Webhooks

Os Webhooks são notificações assíncronas enviadas para todos os eventos solicitados ao Emites.  
Sendo assim, ao receber um evento, o sistema envia uma requisição HTTP para a url configurada no Emites com as informações relacionadas ao evento.
Os webhooks também são conhecidos como Callbacks ou Reverse API .  

Para adicionar uma nova url, acesse a interface do Emites, clique no ícone do menu, depois em conta, no final da página terá um botão para a adição do novo webhook.  

Após adicionado, a cada requisição efetuada ao Emites, será retornada uma notificação sobre o estado do evento.  

Os webhooks seguem a mesma estrutura com exceção da inutilização rejeitada que possui os campos `uf`, `serie`, `numero`, `errors`. Veja abaixo a descrição de cada campo:

`object_type: tipo do objeto solicitado (NFe/NFeBatch e NFCe/NFCeBatch)`

`object_id: id interno objeto solicitado`

`organization_id: id da organização`

`event: status da nota`

`uf: código do estado de acordo com o IBGE `

`serie: série do lote`

`numero: número da nfe/nfc`

`errors: código de erro seguido de uma breve descrição`

## Lote Enviado

Enviado: Quando é realizado o envio de um lote de NF para a Sefaz e a mesma é recebida. Nesta etapa será enviado o seguinte webhook:  

```
{
    "object_type":"NFeBatch",
    "object_id":5,
    "organization_id":1,
    "event":"sent"
}
```

## Nota sendo processada

Processando: Quando a Sefaz do estado recebe a NF e inicia o processo de autenticação da mesma. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"NFeBatch",
    "object_id":5,
    "organization_id":1,
    "event":"processed"
}
```

## Nota Emitida

Emitida: Quando a NF é aceita pela Sefaz. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"NFe",
    "object_id":5,
    "organization_id":1,
    "event":"succeeded"
}
```

## Nota Rejeitada

Rejeitada: Quando a NF é rejeitada pela Sefaz. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"NFeBatch",
    "object_id":4,
    "organization_id":1,
    "event":"rejected"
}
```

## Nota Cancelada  

Cancelada: Quando o cancelamento da NF é aceito pela Sefaz. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"NFe",
    "object_id":5,
    "organization_id":1,
    "event":"cancelled"
}
```

## Cancelamento Rejeitado 

Cancelamento Rejeitado: Quando o cancelamento da NF é rejeitado pela Sefaz. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"NFe",
    "object_id":5,
    "organization_id":1,
    "event":"cancel_rejected"
}
```

## Inutilização Rejeitada

Inutilização Rejeitada: Quando o inutilização da NF é rejeitado pela Sefaz. Nesta etapa será enviado o seguinte webhook:

```
{
    "object_type":"None",
    "object_id":"",
    "organization_id":1,
    "event":"disablement_rejected",
    "uf":"35",
    "serie":"0",
    "numero":"98080986123",
    "errors":["215 - Rejeição: Falha no schema XML"]
}
```