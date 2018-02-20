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
        "nfe_batch":  {
            "lote": 1,
            "sincronicidade": 0,
            "uf": 35,
            "nfes": [{
                "dados_gerais": {
                    "uf": 35,
                    "serie": "1",
                    "codigo_mun_ocorrencia": "3525904",
                    "nfe_numero": "123",
                    "natureza_operacao": "Venda merc. adq. rec. terc. efet. fora estab.",
                    "data_saida_entrada": "2017-09-24T17:07:35-03:00",
                    "tipo_operacao": "1",
                    "indicador_consumidor_final": "0",
                    "indicador_presenca": "9",
                    "finalidade_nfe": "1",
                    "destino_operacao": "1",
                    "indicador_incentivo_fiscal": "FALSE"
                },
                "cliente": {
                    "cpf_cnpj": "46728754000163",
                    "nome": "NF-E EMITIDA EM AMBIENTE DE HOMOLOGACAO - SEM VALOR FISCAL",
                    "pessoa_fisica_juridica": "company",
                    "telefone": "99999999",
                    "inscricao_estadual": "407056228113",
                    "inscricao_municipal": "",
                    "inscricao_suframa": "",
                    "indicador_inscricao_estadual": 1,
                    "email": "teste@nexaas.com.br",
                    "endereco": {
                        "logradouro": "AV GUILHERME PORCARI",
                        "complemento": "",
                        "numero": "S N",
                        "bairro": "MEDEIROS",
                        "codigo_municipio": "3525904",
                        "nome_municipio": "JUNDIAI",
                        "codigo_pais": "1058",
                        "nome_pais": "BRASIL",
                        "uf": "SP",
                        "cep": "13212255"
                    }
                },
                "lista_autorizacao": [],
                "produtos": [
                {
                    "codigo_ean": "",
                    "codigo_produto": "123456",
                    "descricao": "NITROGENIO CIL 50L 10M3",
                    "cfop": 5104,
                    "valor_unitario_comercial": 16.49485,
                    "valor_unitario_tributario": 16.49485,
                    "valor_desconto": 0.0,
                    "valor_total_produto": "98.97",
                    "quantidade_tributaria": 6,
                    "quantidade_comercial": 6,
                    "unidade_tributaria": "M3",
                    "unidade_comercial": "M3",
                    "num_pedido": "S0100249134",
                    "num_item_pedido": 1,
                    "ean_unidade_trib": "",
                    "ncm": 28043000,
                    "cest": "",
                    "valor_frete": 0.0,
                    "valor_seguro": 0.0,
                    "outras_despesas": 0.0,
                    "informacoes_adicionais": "",
                    "tributacao": {
                        "valor_aproximado_total": 269.64,
                        "icms": {
                            "situacao_tributaria": "00",
                            "modalidade_base_calculo": 3,
                            "codigo_origem_produto": 3,
                            "valor_base_calculo": 989.69,
                            "perc_reducao_base_calculo": 0.0,
                            "aliquota_icms": "18.00",
                            "valor_icms": 178.14,
                            "valor_icms_desonerado": 0.0,
                            "motivo_desoneracao": "",
                            "modalidade_base_calculo_st": "3",
                            "valor_base_calculo_st": 0.0,
                            "perc_reducao_base_calculo_st": 0.0,
                            "perc_mva_icms_st": 0.0,
                            "aliquota_icms_st": 0.0,
                            "valor_icms_st": 0.0,
                            "aliquota_interestadual": 0.0,
                            "aliquota_interna_interestadual": 0.0,
                            "valor_uf_remetente_interestadual": 0.0,
                            "valor_uf_destinatario_interestadual": 0.0,
                            "perc_provisorio_interestadual": 0.0,
                            "valor_base_calculo_uf_dest": 0.0,
                            "valor_uf_rementente": 0.0,
                            "perc_fcp_interestadual": 0.0,
                            "valor_fcp_interestadual": 0.0,
                            "valor_icms_operacao": 0.0,
                            "perc_diferimento": 0.0,
                            "valor_icms_diferido": 0.0,
                            "situacao_simples_nacional": 0,
                            "aliquota_icms_simples_nacional": 0,
                            "credito_icms_simples_nacional": 0,
                            "motivo_desoneracao_icms": 0,
                            "valor_icmsst_retido": 0,
                            "base_icmsst_retido": 0
                        },
                        "ipi": {
                            "situacao_tributaria": "01",
                            "cod_enquadramento": 999,
                            "classe_enquadramento": "",
                            "cnpj_produtor": "",
                            "codigo_selo_controle": 0,
                            "quantidade_selo_controle": 0,
                            "valor_ipi": "0.00",
                            "aliquota_ipi": "0.00",
                            "valor_base_calculo": "989.69"
                        },
                        "pis": {
                            "situacao_tributaria": "01",
                            "valor_base_calculo": 989.69,
                            "aliquota_pis": 1.65,
                            "aliquota_pis_reais": 0,
                            "valor_pis": 16.3,
                            "valor_base_calculo_st": 0.0,
                            "aliquota_st": 0.0,
                            "valor_pis_st": 0.0,
                            "aliquota_pis_reais_st": 0
                        },
                        "cofins": {
                            "situacao_tributaria": "01",
                            "valor_base_calculo": 989.69,
                            "aliquota_cofins": "7.60",
                            "aliquota_cofins_reais": 0,
                            "valor_cofins": 75.2,
                            "valor_base_calculo_st": 0.0,
                            "aliquota_st": 0.0,
                            "valor_cofins_st": 0.0,
                            "aliquota_cofins_st_reais": 0
                        }
                    }
                }
                ],
                "cobranca": {
                    "fatura": {
                        "numero_fatura": "",
                        "valor_original": 0,
                        "valor_desconto": 0,
                        "valor_liquido": 0
                    },
                    "duplicatas": [{
                        "numero": "",
                        "data_vencimento": "",
                        "valor": ""
                    }]
                },
                "transporte": {
                    "valor_total_frete": 0.0,
                    "codigo_modalidade": 9,
                    "transportadora": {
                        "cnpj_cpf": "",
                        "razao_social": "",
                        "inscricao_estadual": "",
                        "endereco_completo": "",
                        "municipio": "",
                        "uf": ""
                    },
                    "veiculo": {
                        "placa": "",
                        "uf": "",
                        "rntc": ""
                    },
                    "retencao_icms": {
                        "valor_servico": 0.0,
                        "valor_base_calculo": 0.0,
                        "aliquota_retencao": 0.0,
                        "valor_retido": 0.0,
                        "uf": "",
                        "codigo_municipio": "",
                        "cfop": ""
                    },
                    "endereco_entrega": {
                        "cpf_cnpj": "",
                        "pessoa_fisica_juridica": "",
                        "logradouro": "",
                        "cep": "",
                        "numero": "",
                        "complemento": "",
                        "bairro": "",
                        "uf": "",
                        "nome_municipio": "",
                        "codigo_municipio": ""
                    },
                    "volume_transportado": [{
                        "quantidade_volumes": 1,
                        "numeracao_volumes": 0,
                        "marca": 0,
                        "especie": "Cilindro",
                        "peso_liquido": "66.780",
                        "peso_bruto": "450.780"
                    }]
                },
                "retencao_tributos": {
                    "valor_retido_pis": 0.00,
                    "valor_retido_cofins": 0.00,
                    "valor_retido_csll": 0.00,
                    "valor_base_calculo_irrf": 0.00,
                    "valor_irrf": 0.00,
                    "base_calculo_retencao_previdencia": 0.00,
                    "valor_retencao_previdencia": 0.00
                },
                "informacoes_adicionais": {
                    "informacoes_fisco": "Cliente: 112. Remessa: 000061074-0123",
                    "informacoes_contribuinte": ""
                }
            }]
        }
    }'

```
