# Lista

## Lista de NF-e  

Para obter uma lista de NF-e é necessário realizar a seguinte requisição:  


<div class="api-endpoint">
  <div class="endpoint-data">
    <i class="label label-get">GET</i>
    <h6>/api/v1/organizations/{organization_id}/nfe</h6>
  </div>
</div>

<aside class="notice">
    Os resultados estão limitados a 10 registros por página.<br>
    Você pode usar o parâmetro "page" para indicar página desejada.
</aside>

```shell
EXEMPLO DE REQUISIÇÃO
 
curl -X GET \
  https://app.emites.com.br/api/v1/organizations/11/nfe?page=1 \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json'


EXEMPLO DE RESPOSTA:

{
  "nfe": [
    {
      "id": 10990,
        "status": "succeeded",
        "data": {...},
        "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/pdf_files/000/015/761/original/danfe.pdf?153719",
        "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/xml_files/000/015/761/original/nfce.xml?15379",
        "taxrules_calculation_log": null
    }
  ]
}
```