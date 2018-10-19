# Cancelamento

## Cancelamento de NFe

Para cancelar uma NFe, envie a seguinte requisição:  

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PATCH </i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}/cancel </h6>
    </div>
</div>  

```shell
EXEMPLO DE REQUISIÇÃO

curl -X PATCH \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990/cancel \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \


EXEMPLO DE RESPOSTA

{
  "nfe": {
    "id": 10990,
    "status": "processing",
    "data": {...},
    "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/pdf_files/000/015/761/original/danfe.pdf?153719",
    "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/xml_files/000/015/761/original/nfe.xml?15379",
    "taxrules_calculation_log": null
  }
}
```

Após o processamento da solicitação de cancelamento da NFe, o XML do evento estará disponível via consulta da NFe no campo "cancel_xml_url". Exemplo:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}  </h6>
    </div>
</div>

```
{
  "nfe": {
    "id": 10990,
    "status": "cancelled",
    "data": {...},
    "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/pdf_files/000/015/761/original/danfe.pdf?153719",
    "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/xml_files/000/015/761/original/nfe.xml?15379",
    "cancel_xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/cancel_xml_files/000/010/598/original/cancel_nfe.xml?15781",
    "taxrules_calculation_log": null
  }
}
```

## Cancelamento de NFCe

Para cancelar uma NFCe, envie a seguinte requisição:  

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PATCH </i>
        <h6>/api/v1/organizations/{organization_id}/nfce/{nfce_id}/cancel </h6>
    </div>
</div>  

```shell
EXEMPLO DE REQUISIÇÃO

curl -X PATCH \
    https://app.emites.com.br/api/v1/organizations/11/nfce/10990/cancel \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \


EXEMPLO DE RESPOSTA

{
  "nfce": {
    "id": 10990,
    "status": "processing",
    "data": {...},
    "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/pdf_files/000/015/761/original/danfe.pdf?153719",
    "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/xml_files/000/015/761/original/nfe.xml?15379",
    "taxrules_calculation_log": null
  }
}
```

Após o processamento da solicitação de cancelamento da NFCe, o XML do evento estará disponível via consulta da NFCe no campo "cancel_xml_url". Exemplo:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/organizations/{organization_id}/nfce/{nfce_id}  </h6>
    </div>
</div>

```
{
  "nfce": {
    "id": 5,
      "status": "cancelled",
      "data": {...},
      "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/pdf_files/000/015/761/original/danfe.pdf?153719",
      "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/xml_files/000/015/761/original/nfce.xml?15379",
      "cancel_xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/cancel_xml_files/000/010/598/original/cancel_nfce.xml?15781",
      "taxrules_calculation_log": null
  }
}
```
