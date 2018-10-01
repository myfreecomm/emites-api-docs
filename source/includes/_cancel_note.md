#Cancelamento de nota

Para cancelar uma nota, envie a seguinte requisição:  

**Obs.: Após o processamento da solicitação de cancelamento da NF, o XML do evento estará disponível via consulta da NF no campo "cancel_xml_url".**

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">PATCH </i>
        <h6>/api/v1/organizations/{organization_id}/nfe/{nfe_id}/cancel </h6>
    </div>
</div>  

  ```shell
curl -X PATCH \
    https://app.emites.com.br/api/v1/organizations/11/nfe/10990/cancel \
    -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
    -H 'content-type: application/json' \
  ```
