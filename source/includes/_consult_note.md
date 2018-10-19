# Consulta

## Consulta de NF-e  

Para consultar uma NF-e é necessário realizar a seguinte requisição:  


<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}  </h6>
  </div>
</div>


```shell
EXEMPLO DE REQUISIÇÃO
 
curl -X GET \
  https://app.emites.com.br/api/v1/organizations/11/nfe/10990 \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json'


EXEMPLO DE RESPOSTA:

{
  "nfe": {
    "id": 10990,
      "status": "succeeded",
      "data": {...},
      "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/pdf_files/000/015/761/original/danfe.pdf?153719",
      "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/xml_files/000/015/761/original/nfce.xml?15379",
      "taxrules_calculation_log": null
  }
}
```
  
## Consulta de NFC-e  

Para consultar uma NFC-e é necessário realizar a seguinte requisição:  


<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>/api/v1/organizations/{organization_id}/nfce/{nfce_id}  </h6>
  </div>
</div>


```shell
EXEMPLO DE REQUISIÇÃO

curl -X GET \
  https://app.emites.com.br/api/v1/organizations/11/nfce/555 \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json'
  

EXEMPLO DE RESPOSTA:

{
  "nfce": {
    "id": 555,
      "status": "succeeded",
      "data": {...},
      "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/pdf_files/000/015/761/original/danfe.pdf?153719",
      "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfce/xml_files/000/015/761/original/nfce.xml?15379",
      "taxrules_calculation_log": null
  }
}
```