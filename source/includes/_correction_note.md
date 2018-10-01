# Carta de Correção de Nota

A carta de correção de nota fiscal eletrônica (CC-e) é um documento fiscal com o objetivo de corrigir informações da nota fiscal eletrônica (NF-e).
Se você emitir uma NF-e com um erro, pode corrigi-lá com uma CC-e, mas nem todos os erros são passíveis de correção, é preciso seguir algumas regras.

Ela é utilizada para a regularização de algum erro ocorrido na emissão, desde que não seja: 

* o valor do imposto (base de cálculo, alíquota, diferença de preço, quantidade, valor de operação ou prestação), 
* os dados cadastrais (mudanças do remetente ou destinatário)
* data de emissão ou de saída da mercadoria.

Regras:

* Permitido em até 30 dias, após a emissão da nojta.

O que pode ser corrigido?

* A natureza de operação (CFOP): sob a condição de não mudar a natureza dos impostos;
* Os códigos ficais: desde que não altere os valores fiscais;
* Data de emissão ou de saída: contanto que não altere o período de apuração do ICMS;
* Peso, volume etc.;
* Endereço do destinatário;
* Razão social do destinatário: se não alterar por completo;
* Dados adicionais.

Não há um padrão de texto, mas o emissor tem a obrigação de descrever de forma clara e objetiva a correção que deve ser considerada. 

**Obs.: Após o processamento da solicitação da carta de correção da NF, o XML do evento estará disponível via consulta da NF no campo "correction_xml_url".**

Para requisitar uma correção, envie a seguinte requisição:

 
<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PATCH</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}/correction </h6>
    </div>
</div> 

```shell
curl -X PATCH \
  https://app.emites.com.br/api/v1/organizations/11/nfe/10990/correction \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \
    -d '{
            "nfe": {
              "numero_evento": "2",
              "correcao": "Altera-se a descrição do produto para NITROGENIO 50L 10M3"
            }
        }'
```

Após o processamento da solicitação da carta de correção da NF, o XML do evento estará disponível via consulta da NF no campo "correction_xml_url".

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">GET</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}  </h6>
    </div>
</div>

```
{
  "nfe": {
    "id": 5,
      "status": "corrected",
      "data": {...},
      "danfe_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/pdf_files/000/015/761/original/danfe.pdf?153719",
      "xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/xml_files/000/015/761/original/nfe.xml?15379",
      "taxrules_calculation_log": null,
      "correction_xml_url": "http://emites-ruby-sandbox.s3.amazonaws.com/nfe/correction_xml_files/000/010/598/original/correction_nfe.xml?15781"
  }
}
```
