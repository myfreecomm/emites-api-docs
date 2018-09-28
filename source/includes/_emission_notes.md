# Emissão de notas

Para emitir notas, é necessário realizar uma requisição POST para o seguinte endereço:  

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe_batch</h6>
    </div>
</div>

Veja a seguir um exemplo do corpo da requisição:  

<aside class="warning">
Todos os campos de texto da NF-e não aceitam caracteres acentuados como, por exemplo "á", "é", "â", "ã" etc. Também não aceitam "ç".
</aside>

```shell
curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfe_batch \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json' \
  -d '{
        "nfe_batch": {
          "lote": 1,
          "sincronicidade": 0,
          "uf": 35,
          "nfes": [
            {
              "cliente": {
                "cpf_cnpj": "46728754000163",
                "email": "teste@nexaas.com.br",
                "endereco": {
                  "bairro": "MEDEIROS",
                  "cep": "13212255",
                  "codigo_municipio": "3525904",
                  "codigo_pais": "1058",
                  "complemento": "",
                  "logradouro": "AV GUILHERME PORCARI",
                  "nome_municipio": "JUNDIAI",
                  "nome_pais": "BRASIL",
                  "numero": "S N",
                  "uf": "SP"
                },
                "indicador_inscricao_estadual": 1,
                "inscricao_estadual": "407056228113",
                "inscricao_municipal": "",
                "inscricao_suframa": "",
                "nome": "NF-E EMITIDA EM AMBIENTE DE HOMOLOGACAO - SEM VALOR FISCAL",
                "pessoa_fisica_juridica": "company",
                "telefone": "99999999"
              },
              "cobranca": {
                "duplicatas": [
                  {
                    "data_vencimento": "",
                    "numero": "",
                    "valor": ""
                  }
                ],
                "fatura": {
                  "numero_fatura": "",
                  "valor_desconto": 0,
                  "valor_liquido": 0,
                  "valor_original": 0
                }
              },
              "dados_gerais": {
                "codigo_mun_ocorrencia": "3525904",
                "data_saida_entrada": "2017-09-24T17:07:35-03:00",
                "destino_operacao": "1",
                "finalidade_nfe": "1",
                "indicador_consumidor_final": "0",
                "indicador_incentivo_fiscal": "FALSE",
                "indicador_presenca": "9",
                "natureza_operacao": "Venda merc. adq. rec. terc. efet. fora estab.",
                "nfe_numero": "123",
                "serie": "1",
                "tipo_operacao": "1",
                "uf": 35
              },
              "forma_de_pagamento": [
                {
                  "tipo_de_pagamento": "01",
                  "valor_do_pagamento": 50.0
                },
                {
                  "tipo_de_integracao": "2",
                  "tipo_de_pagamento": "03",
                  "valor_do_pagamento": 8.97
                },
                {
                  "bandeira_operadora": "02",
                  "cnpj_credenciadora": "99999999999999",
                  "numero_autorizacao_operacao": "99999999999999999999",
                  "tipo_de_integracao": "1",
                  "tipo_de_pagamento": "03",
                  "valor_do_pagamento": 40.0
                }
              ],
              "informacoes_adicionais": {
                "informacoes_contribuinte": "",
                "informacoes_fisco": "Cliente: 112. Remessa: 000061074-0123"
              },
              "lista_autorizacao": [],
              "produtos": [
                {
                  "cest": "",
                  "cfop": 5104,
                  "cnpj_fabricante_mercadoria": "99999999999999999",
                  "codigo_beneficio_fiscal": "foo",
                  "codigo_ean": "",
                  "codigo_produto": "123456",
                  "descricao": "NITROGENIO CIL 50L 10M3",
                  "ean_unidade_trib": "",
                  "informacoes_adicionais": "",
                  "ncm": 28043000,
                  "num_item_pedido": 1,
                  "num_pedido": "S0100249134",
                  "outras_despesas": 0.0,
                  "producao_escala": "S",
                  "quantidade_comercial": 6,
                  "quantidade_tributaria": 6,
                  "tributacao": {
                    "cofins": {
                      "aliquota_cofins": "7.60",
                      "aliquota_cofins_reais": 0,
                      "aliquota_cofins_st_reais": 0,
                      "aliquota_st": 0.0,
                      "situacao_tributaria": "01",
                      "valor_base_calculo": 989.69,
                      "valor_base_calculo_st": 0.0,
                      "valor_cofins": 75.2,
                      "valor_cofins_st": 0.0
                    },
                    "icms": {
                      "aliquota_consumidor_final": 0,
                      "aliquota_fcp": 0,
                      "aliquota_fcp_st": 0,
                      "aliquota_fcp_st_retido": 0,
                      "aliquota_icms": "18.00",
                      "aliquota_icms_simples_nacional": 0,
                      "aliquota_icms_st": 0.0,
                      "aliquota_interestadual": 0.0,
                      "aliquota_interna_interestadual": 0.0,
                      "base_icmsst_retido": 0,
                      "codigo_origem_produto": 3,
                      "credito_icms_simples_nacional": 0,
                      "modalidade_base_calculo": 3,
                      "modalidade_base_calculo_st": "3",
                      "motivo_desoneracao": "",
                      "motivo_desoneracao_icms": 0,
                      "perc_diferimento": 0.0,
                      "perc_fcp_interestadual": 0.0,
                      "perc_mva_icms_st": 0.0,
                      "perc_provisorio_interestadual": 0.0,
                      "perc_reducao_base_calculo": 0.0,
                      "perc_reducao_base_calculo_st": 0.0,
                      "situacao_simples_nacional": 0,
                      "situacao_tributaria": "00",
                      "valor_base_calculo": 989.69,
                      "valor_base_calculo_fcp": 0,
                      "valor_base_calculo_fcp_st": 0.0,
                      "valor_base_calculo_fcp_st_retido": 0.0,
                      "valor_base_calculo_st": 0.0,
                      "valor_base_calculo_uf_dest": 0.0,
                      "valor_fcp": 0.0,
                      "valor_fcp_interestadual": 0.0,
                      "valor_fcp_st": 0.0,
                      "valor_fcp_st_retido": 0.0,
                      "valor_icms": 178.14,
                      "valor_icms_desonerado": 0.0,
                      "valor_icms_diferido": 0.0,
                      "valor_icms_operacao": 0.0,
                      "valor_icms_st": 0.0,
                      "valor_icmsst_retido": 0,
                      "valor_uf_destinatario_interestadual": 0.0,
                      "valor_uf_rementente": 0.0,
                      "valor_uf_remetente_interestadual": 0.0
                    },
                    "ipi": {
                      "aliquota_ipi": "0.00",
                      "cnpj_produtor": "",
                      "codigo_enquadramento": 999,
                      "codigo_selo_controle": 0,
                      "quantidade_selo_controle": 0,
                      "situacao_tributaria": "01",
                      "valor_base_calculo": "989.69",
                      "valor_ipi": "0.00"
                    },
                    "pis": {
                      "aliquota_pis": 1.65,
                      "aliquota_pis_reais": 0,
                      "aliquota_pis_reais_st": 0,
                      "aliquota_st": 0.0,
                      "situacao_tributaria": "01",
                      "valor_base_calculo": 989.69,
                      "valor_base_calculo_st": 0.0,
                      "valor_pis": 16.3,
                      "valor_pis_st": 0.0
                    },
                    "valor_aproximado_total": 269.64
                  },
                  "unidade_comercial": "M3",
                  "unidade_tributaria": "M3",
                  "valor_desconto": 0.0,
                  "valor_frete": 0.0,
                  "valor_seguro": 0.0,
                  "valor_total_produto": "98.97",
                  "valor_unitario_comercial": 16.49485,
                  "valor_unitario_tributario": 16.49485
                }
              ],
              "retencao_tributos": {
                "base_calculo_retencao_previdencia": 0.0,
                "valor_base_calculo_irrf": 0.0,
                "valor_irrf": 0.0,
                "valor_retencao_previdencia": 0.0,
                "valor_retido_cofins": 0.0,
                "valor_retido_csll": 0.0,
                "valor_retido_pis": 0.0
              },
              "transporte": {
                "codigo_modalidade": 9,
                "endereco_entrega": {
                  "bairro": "",
                  "cep": "",
                  "codigo_municipio": "",
                  "complemento": "",
                  "cpf_cnpj": "",
                  "logradouro": "",
                  "nome_municipio": "",
                  "numero": "",
                  "pessoa_fisica_juridica": "",
                  "uf": ""
                },
                "retencao_icms": {
                  "aliquota_retencao": 0.0,
                  "cfop": "",
                  "codigo_municipio": "",
                  "uf": "",
                  "valor_base_calculo": 0.0,
                  "valor_retido": 0.0,
                  "valor_servico": 0.0
                },
                "transportadora": {
                  "cnpj_cpf": "",
                  "endereco_completo": "",
                  "inscricao_estadual": "",
                  "municipio": "",
                  "razao_social": "",
                  "uf": ""
                },
                "valor_total_frete": 0.0,
                "veiculo": {
                  "placa": "",
                  "rntc": "",
                  "uf": ""
                },
                "volume_transportado": [
                  {
                    "especie": "Cilindro",
                    "marca": 0,
                    "numeracao_volumes": 0,
                    "peso_bruto": "450.780",
                    "peso_liquido": "66.780",
                    "quantidade_volumes": 1
                  }
                ]
              }
            }
          ]
        }
      }'

```
