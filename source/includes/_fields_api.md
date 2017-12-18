#Campos da API

## dados_gerais (XML: ide)  

Contém informações gerais e metadados sobre a NF-e. Seus atributos são:

### uf

Código da UF do emitente do Documento Fiscal.


  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  cUF          |  Sim          |  Numérico  |  2 dígitos         |


### serie
Série do Documento Fiscal. Informar 0 (zero) para série única.

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  serie        |  Sim          |  Numérico  | Até 3 dígitos      |


### codigo_mun_ocorrencia  

Código do Município de Ocorrência do Fato Gerador.

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  cMunFG       |  Sim          |  Numérico  | 7 dígitos          |


### nfe_numero  

Número do Documento Fiscal.

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  nNF          |  Sim          |  Numérico  |                    |

### data_saida_entrada  

Data e hora de Saída ou da Entrada da Mercadoria/Produto.  

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho        | Observações
---------------|---------------|------------|---------------------------|------------
  dhSaiEnt     |  Não          |  Data      | aaaa-mm-ddThh:mm:ss-03:00 |


### tipo_operacao  

Tipo de Operação, sendo 0 = Entrada e 1 = Saída.  

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  tpNF         |  Sim          |  Numérico  | 1 dígito           |

### tipo_emissão

Forma de Emissão da NF-e. Seleção entre:  
1 = Emissão normal (não em contingência);   
2 = Contingência FS-IA, com impressão do DANFE em formulário de segurança;   
3 = Contingência SCAN (Sistema de Contingência do Ambiente Nacional);   
4 = Contingência DPEC (Declaração Prévia da Emissão em Contingência);  
5 = Contingência FS-DA, com impressão do DANFE em formulário de segurança; 
6 = Contingência SVC-AN (SEFAZ Virtual de Contingência do AN);  
7 = Contingência SVC-RS (SEFAZ Virtual de Contingência do RS);  
9 = Contingência off-line da NFC-e (as demais opções de contingência são válidas também para a NFC-e).  

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
  tpEmiss      |  Sim          |  Numérico  |  1 dígito          |

### destino_operacao  

Identificador de Local de destino da operação (1 - Interna; 2 - Interestadual; 3 - Exterior).

  Campo no XML |  Obrigatório  |    Tipo    |  Formato e tamanho | Observações
---------------|---------------|------------|--------------------|------------
idDest         |  Sim          |  Numérico  |  1 dígito          |

### natureza_operacao  

Informar a natureza da operação de que decorrer a saída ou a entrada, tais como venda, compra, transferência, devolução, importação, consignação, remessa (para fins de demonstração, de industrialização ou outra), conforme previsto na alínea 'i', inciso I, do art. 19 do Convênio s/nº de 15 de dezembro de 1970. 


  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  natOp        |  Sim          |  Texto  e/ou número  |  1 a 60 caracteres           |

### indicador_pagamento  

Indicador da forma de pagamento. Seleção entre:   0 = pagamento a vista   1 = pagamento a prazo   2 = outros. 

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indPag       |  Sim          |  Numérico            |  1 dígito                    |  

### indicador_consumidor_final

Indica se a NF-e foi emitida para consumidor final, sendo 0 = Não e 1 = Sim.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indFinal     |  Sim          |  Numérico            |  1 dígito                    |  

### indicador_presenca
Indicador de presença do comprador no estabelecimento comercial no momento da operação. Seleção entre:  

0 = Não se aplica (por exemplo, Nota Fiscal complementar ou de ajuste);  
1 = Operação presencial;   
2 = Operação não presencial, pela Internet;  
3   = Operação não presencial, Teleatendimento;  
4 = NFC-e em operação com entrega a domicílio;  
9 = Operação não presencial, outros.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indPres      |  Sim          |  Numérico            |  1 dígito                    |  

### finalidade_nfe
Finalidade de emissão da NF-e. Seleção entre:   1 - NF-e normal   2 - NF-e complementar   3 - NF-e de ajuste  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  finNFe       |  Sim          |  Numérico            |  1 dígito                    |  

### valor_total_nota

Somatória do Valor Total dos Produtos ou Serviços e determinados impostos. Calculado automaticamente pelo Emites.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vNF          |  Sim          |  Decimal             |                              |  

###  indicador_incentivo_fiscal  
Indicador de incentivo fiscal, sendo 1 = Sim, 2 = Não.  
  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indIncentivo |  Sim          |  Numérico            |   1 dígito                   |  


## emitente (XML: emit)  

Contém informações sobre a empresa emitente da NF-e. Seus atributos são:  

### cnpj  

CNPJ da empresa emitente, somente números.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CNPJ         |  Sim          |  Numérico            |   14 dígitos                 |  

### razao_social  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xNome        |  Sim          |  Texto               |   Até 60 caracteres          |  

### nome_fantasia  
 
  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xFant        |  Não          |  Texto               |   Até 60 caracteres          |  

### inscricao_estadual  

Informar somente os algarismos, sem ponto, hífen, barra, etc. Na emissão de NF-e avulsa pode ser informado o texto ISENTO para os contribuintes do ICMS isentos de inscrição no cadastro de contribuintes do ICMS.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  IE           |  sim          |  Texto               |   Até 14 caracteres          |  

### inscricao_estadual_st  

Inscrição Estadual do Substituto Tributário do estado de destino da mercadoria, quando houver a retenção de ICMS ST para o estado de destino.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  IEST         |  Não          |  Numérico            |   Até 14 caracteres          |  

### inscricao_municipal  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  IM           |  Não          |  Texto               |   Até 15 caracteres          |  

### cnae  

CNAE fiscal que pode ser informado quando a inscrição municipal for informada.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CNAE         |  Não          |  Numérico            |   7 caracteres               |  

### codigo_regime_tributario  
 
Seleção entre:  

1 = Simples Nacional;
2 = Simples Nacional, excesso sublimite de receita bruta;
3 = Regime Normal.  

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CRT          |  Não          |  Numérico            |   1 dígito                   |  
 
## endereco (XML: enderEmit)  

Grupo de informações relacionadas ao endereço do emitente. Seus atributos são:  

### logradouro

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xLgr         |  Sim          |  Texto               |   Até 60 caracteres          |  

### numero

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  nro          |  Sim          |  Texto               |   Até 60 caracteres          |  

### complemento

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xCpl         |  Não          |  Texto               |   Até 60 caracteres          |  

### bairro

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xBairro      |  Sim          |  Texto               |  Até 60 caracteres          |  

### codigo_municipio

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cMun         |  Sim          |  Numérico            |  7 dígitos                   |  

### nome_municipio

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xMun         |  Sim          |  Texto               |  Até 60 caracteres           |  

### cep
Campo no XML

  Campo no XML |  Obrigatório  |    Tipo              |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CEP          |  Sim          |  Numérico            |  8 dígitos                   |  

### uf

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  UF           |  Sim          |  Texto               |  2 caracteres                |  

### codigo_pais

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cPais        |  Não          |  Numérico            |  4 dígitos                   | 1058 = Brasil  

### nome_pais

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xPais        |  Não          |  Texto               |  Até 60 caracteres           | Brasil ou BRASIL  

### telefone

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  fone         |  Não          |  Numérico            |  De 6 a 14 carateres         |  

## cliente (XML: dest)  

Contém informações sobre o destinatário da aquisição dos produtos do emitente (nota de saída) ou venda dos produtos para o emitente (nota de entrada). Seus atributos são:  

### cpf_cnpj
CPF ou CNPJ do destinatário, somente números.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CPF ou CNPJ  |  Sim          |  Numérico            |  11 ou 14 dígitos            |  

### nome  

Razão social ou nome do destinatário  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xNome        |  Sim          |  Texto               |  Até 60 caracteres           |  

### pessoa_fisica_juridica  

Campo de controle do Emites para indicar se o destinatário é pessoa física (“person”) ou jurídica (“company”).

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  -            |  Sim          |  Texto               |  -                           |  


### inscricao_estadual  

Informar somente os algarismos, sem ponto, hífen, barra, etc.  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  IE           |  Não          |  Numérico            |  Até 14 dígitos              |  

### inscricao_suframa
Obrigatório nas operações que se beneficiam de incentivos fiscais existentes nas áreas sob controle da SUFRAMA. A omissão desta informação impede o processamento da operação pelo Sistema de Mercadoria Nacional da SUFRAMA e a liberação da Declaração de Ingresso, prejudicando a comprovação do ingresso / internamento da mercadoria nestas áreas.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  ISUF         |  Não          |  Numérico            |  De 8 a 9 dígitos            |  

### inscricao_municipal

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  IM           |  Não          |  Texto               |  Até 15 caracteres           |  

### indicador_inscricao_estadual

Indica se o destinatário é contribuinte do ICMS. Seleção entre:  

1 = Contribuinte ICMS (informar a IE do destinatário);  
2 = Contribuinte isento de Inscrição no cadastro de Contribuintes do ICMS;  
9 = Não Contribuinte, que pode ou não possuir Inscrição Estadual no Cadastro de Contribuintes do ICMS.  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indIEDest    |  Sim          |  Numérico            |  1 dígito                    |  

### email

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  email        |  Não          |  Texto               |  Até 60 caracteres           |  

### endereco (XML: enderDest)  

Grupo de informações relacionadas ao endereço do destinatário. Seus atributos são:  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xLgr         |  Sim          |  Texto               |  Até 60 caracteres           |  

### numero

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  nro          |  Sim          |  Texto               |  Até 60 caracteres           |  

### complemento

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xCpl         |  Não          |  Texto               |  Até 60 caracteres           |  

### bairro

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xBairro      |  Sim          |  Texto               |  Até 60 caracteres           |  

### codigo_municipio

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cMun         |  Sim          |  Numérico            |  7 dígitos                   |  

### nome_municipio

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xMun         |  Sim          |  Texto              |  Até 60 caracteres            |  

### cep

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CEP          |  Sim          |  Numérico            |  8 dígitos                   |  


### uf

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  UF           |  Sim          |  Texto               |  2 caracteres                |  

### codigo_pais

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cPais        |  Não          |  Numérico            |  4 dígitos                   |  

### nome_pais

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xPais        |  Não          |  Texto               |  Até 60 caracteres           |  

### telefone

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  fone        |  Não           |  Numérico            |  De 6 a 14 carateres         |  