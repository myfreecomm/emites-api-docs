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
 
### endereco (XML: enderEmit)  

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

### endereco (XML: enderDest)

Grupo de informações relacionadas ao endereço do destinatário. Seus atributos são:

### logradouro   

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
  xMun         |  Sim          |  Texto               |  Até 60 caracteres           |  

### cep

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CEP          |  Sim          |  Numérico            |  8 dígitos                   |  

### uf

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  UF           |  Sim          |  Texto               |  2 caracteres                | Sigla do estado  

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

## produto (XML: prod)  

Contém informações sobre os produtos contidos na NF-e. No XML, o nó  prod  é subitem do nó  det  e pode conter uma ou mais ocorrência. Seus atributos são:  

### codigo_produto  

Codificação própria da empresa. Preencher com CFOP, caso se trate de itens não relacionados com mercadorias/produtos e se o contribuinte não possuir codificação própria. Caso preenchido com CFOP, utilizar o formato "CFOP9999".  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cProd        |  Sim          |  Texto e/ou número   |  Até 60 caracteres           |  

### codigo_ean

Código de barras. Preencher com o código de barra GTIN-8, GTIN-12, GTIN-13 ou GTIN-14 (antigos códigos EAN, UPC e DUN- 14). Não informar este campo se o produto não possuir este código.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cEAN         |  Não          |  Numérico            |  8, 12, 13 ou 14 dígitos     |  

### descricao

Descrição do produto.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xProd        |  Sim          |  Texto               |  Até 120 caracteres          |  

### ncm

Nomenclatura comum do Mercosul.  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
NCM            |  Sim          |  Numérico            |  8 dígitos                   |  Itens específicos que não possuem NCM podem informar somente o código “00”.

###cest

Código Especificador de Substituição Tributária.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CEST         |               |                      |                              |  
  
### extipi

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  EXTIPI       |  Não          |  Numérico            |  De 2 a 3 dígitos            |  

### cfop

Código Fiscal de Operações e Prestações.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CFOP         |  Sim          |  Numérico            |  4 dígitos                   |  

### produto_especifico

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
       -       |       -       |         -            |          -                   |  -
               
### idade_comercial

Unidade de comercialização do produto.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  uCom         |  Sim          |  Texto               |  Até 6 caracteres            |  
  
### qantidade_comercial

Quantidade de comercialização do produto.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  qCom         |  Sim          |  Decimal             |  Até 11 dígitos, 4 casas decimais |  

### valor_unitario_comercial

Valor unitário de comercialização.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vUnCom       |  Sim          |  Decimal             |  Até 11 dígitos, 4 casas decimais|  

### ean_unidade_trib

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  cEANTrib     |  Não          |  Numérico            |  8, 12, 13 ou 14 dígitos     |  
  
### unidade_tributaria

Unidade tributável do produto.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  uTrib        |  Sim          |  Texto               |  Até 6 caracteres            |  

### qantidade_tributaria

Quantidade tributável do produto.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  qTrib        |  Sim          |  Decimal             |  Até 11 dígitos, 4 casas decimais|  

### valor_unitario_tributario

Valor unitário de tributação.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vUnTrib      |  Sim          |  Decimal             |  Até 11 dígitos, 10 casas decimais |   

### valor_frete

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vFrete       |  Não          |  Decimal             |  Até 13 dígitos, 2 casas decimais |   

### valor_seguro

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vSeg         |  Não          |  Decimal             |  Até 13 dígitos, 2 casas decimais|  
  
### valor_desconto

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vDesc        |  Não          |  Decimal             |  Até 13 dígitos, 2 casas decimais |   

### outras_despesas

Outras despesas acessórias.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vOutro       |  Não          |  Decimal             |  Até 13 dígitos, 2 casas decimais |  

### num_pedido

Número do pedido de compra, se houver.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  xPed         |  Não          |  Texto e/ou número   |  Até 15 caracteres           |  

### num_item_pedido

Item do pedido de compra.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  nItemPed     |  Não          |  Numérico            |  Até 6 dígitos               |  

### num_controle_fci

Número de controle da FCI - Ficha de Conteúdo de Importação.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  nFCI         |  Não          |  Texto               |  Até 36 caracteres           |  

### ind_valor_total

Informa se o valor dos produtos compõem o valor total da nota. Seleção entre:
0 = Valor do item não compõem o valor total da NF-e;
1 = Valor do item compõem o valor total da NF-e.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  indTotal     |  Sim          |  Numérico            |  1 dígito                    |  

## tributação (XML: imposto)

Grupo de informações relacionadas à tributação de ICMS, IPI, PIS, COFINS e Importação.

### valor_aproximado_total

Valor aproximado total de tributos federais, estaduais e municipais.

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  vTotalTrib   |  Não          |  Decimal             |  Até 13 dígitos, 2 casas decimais  |  

### icms (XML: ICMS)

Informações relacionadas ao ICMS. O atributos são variáveis de acordo com a situação tributária. Atributos comuns a todas as situações tributárias

### situacao_tributaria

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  CST          |  Sim          |  Numérico            |  2 dígitos                   |  

### codigo_origem_produto

Origem da mercadoria. Seleção entre:  
0 = Nacional, exceto as indicadas nos códigos 3, 4, 5 e 8;  
1 = Estrangeira - Importação direta, exceto a indicada no código 6;  
2 = Estrangeira - Adquirida no mercado interno, exceto a indicada no código 7;  
3 = Nacional, mercadoria ou bem com Conteúdo de Importação superior a 40% e inferior ou igual a 70%;  
4 = Nacional, cuja produção tenha sido feita em conformidade com os processos produtivos básicos de que tratam as legislações citadas nos Ajustes;  
5 = Nacional, mercadoria ou bem com Conteúdo de Importação inferior ou igual a 40%;  
6 = Estrangeira - Importação direta, sem similar nacional, constante em lista da CAMEX e gás natural;  
7 = Estrangeira - Adquirida no mercado interno, sem similar nacional, constante lista CAMEX e gás natural.  
8 = Nacional, mercadoria ou bem com Conteúdo de Importação superior a 70%.  

  Campo no XML |  Obrigatório  |  Tipo                |  Formato e tamanho           | Observações
---------------|---------------|----------------------|------------------------------|------------
  orig         |  Sim          |  Numérico            |  1 dígito                    |  


### ICMS interestadual (XML: ICMSUFDest)  

Grupo a ser informado nas vendas interestaduais para consumidor final, não contribuinte de ICMS.  

  Campo                                 |  XML            |  Obrigatório  |  Tipo     |  Formato e tamanho                 | Observações
----------------------------------------|-----------------|---------------|-----------|------------------------------------|------------
  valor_base_calculo_uf_dest            |  vBCUFDest      |  Não          |  Decimal  | Até 13 dígitos, 2 casas decimais   |
  aliquota_interna_interestadual        |  pICMSUFDest    |  Não          |  Decimal  | Até 3 dígitos, 4 casas decimais    |
  aliquota_interestadual                |  pICMSInter     |  Não          |  Decimal  | Até 3 dígitos, 4 casas decimais    |
  perc_provisorio_interestadual         |  pICMSInterPart |  Não          |  Decimal  | Até 3 dígitos, 4 casas decimais    |
  valor_uf_remetente_interestadual      |  vICMSUFRemet   |  Não          |  Decimal  | Até 13 dígitos, 2 casas decimais   |
  valor_uf_destinatario_interestadual   |  vICMSUFDest    |  Não          |  Decimal  | Até 13 dígitos, 2 casas decimais   |
  perc_fcp_interestadual                |  pFCPUFDest     |  Não          |  Decimal  | Até 3 dígitos, 4 casas decimais    |
  valor_fcp_interestadual               |  vFCPUFDest     |  Não          |  Decimal  | Até 13 dígitos, 2 casas decimais   |

### situacao_tributaria = 00

Tributada integralmente.

  Campo no XML                | XML           |  Obrigatório  |  Tipo      |  Formato e tamanho                 | Observações
------------------------------|---------------|---------------|------------|------------------------------------|------------
  modalidade_base_calculo     | modBC         |  Sim          |  Numérico  |  1 dígito                          | 0=Margem Valor Agregado (%);  <br>1=Pauta (Valor);  <br>2=Preço Tabelado Máx. (valor);  <br>3=Valor da operação.
  valor_base_calculo          | vBC           |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais  | 
  aliquota_icms               | pICMS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais  | 
  valor_icms                  | vICMS         |  SIm          |  Decimal   |  Até 13 dígitos, 2 casas decimais  | 

### situacao_tributaria = 10

Tributada com cobrança de ICMS por ST.

  Campo                         |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
  modalidade_base_calculo       |  modBC        |  Sim          |  Numérico  |  Numérico                           | 1 dígito 0=Margem Valor Agregado (%); <br>1=Pauta (Valor); <br>2=Preço Tabelado Máx. (valor); <br>3=Valor da operação.   
  valor_base_calculo            |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
  aliquota_icms                 |  pICMS        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  
  valor_icms                    |  vICMS        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
  modalidade_base_calculo_st    |  modBCST      |  Sim          |  Numérico  |  1 dígito                           | 0=Preço tabelado ou máximo sugerido; <br>1=Lista Negativa (valor); <br>2=Lista Positiva (valor); <br>3=Lista Neutra (valor);  4=Margem Valor Agregado (%); 5=Pauta (valor).
  valor_base_calculo_st         |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
  perc_reducao_base_calculo_st  |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |   
  perc_mva_icms_st              |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    | 
  aliquota_icms_st              |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  
  valor_icms_st                 |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |   

com partilha do ICMS entre a UF de origem e a UF de destino ou a UF definida na legislação  

  Campo                         |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
  base_calculo_operacao_propria |  pBCOp        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  Percentual para determinação do valor da Base de Cálculo da operação própria.
  uf_icmsst_devido              |  UFST         |  Sim          |  Texto     |  2 carac.                           |  Sigla da UF para qual é devido o ICMS ST da operação.

### situacao_tributaria = 20

Com redução de base de cálculo.

  Campo                         |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
modalidade_base_calculo         |  modBC        |  Sim          |  Numérico  |  1 dígito                           |  0=Margem Valor Agregado (%);<br>1=Pauta (Valor);<br>2=Preço Tabelado Máx. (valor);<br>3=Valor da operação.
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
perc_reducao_base_calculo       |  pRedBC       |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    | 
aliquota_icms                   |  pICMS        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms                      |  vICMS        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
valor_icms_desonerado           |  vICMSDeson   |  Não          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
motivo_desoneracao              |  motDesICMS   |  Não          |  Numérico  |  2 dígitos                          |  Informar o motivo da desoneração: <br>1 = Táxi<br> 3 = Produto Agropecuário <br>4 = Frotista/Locadora <br>5 = Diplomático/Consular <br>6 = Utilitários e Motocicletas da Amazônia Ocidental e Áreas de Livre Comércio <br>7 = SUFRAMA <br>8 = Venda a Órgão Público <br>9 = Outros <br>10 = Deficiente Condutor <br>11 = Deficiente Não Condutor <br>12 = Órgão de fomento e desenvolvimento agropecuário

### situacao_tributaria = 30

Isenta e não tributada e com cobrança de ICMS por ST.

  Campo                         |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
valor_icms_desonerado           |  vICMSDeson   |  Não          |  Decimal   | Até 13 dígitos, 2 casas decimais    |  
motivo_desoneracao              |  motDesICMS   |  Não          |  Numérico  | 2 dígitos                           |  Informar o motivo da desoneração: <br>1 = Táxi <br>3 = Produto Agropecuário <br>4 = Frotista/Locadora <br>5 = Diplomático/Consular <br>6 = Utilitários e  Motocicletas da Amazônia Ocidental e Áreas de Livre Comércio <br>7 = SUFRAMA <br>8 = Venda a Órgão Público <br>9 = Outros <br>10 = Deficiente Condutor <br>11 = Deficiente Não Condutor <br>12 = Órgão de fomento e desenvolvimento agropecuário 
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico   | 1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).
valor_base_calculo_st           |  vBCST      |  Sim          |  Decimal   | Até 13 dígitos, 2 casas decimais    |  
perc_reducao_base_calculo_st    |  pRedBCST   |  Não          |  Decimal   | Até 3 dígitos, 4 casas decimais     |  
perc_mva_icms_st                |  pMVAST     |  Não          |  Decimal   | Até 3 dígitos, 4 casas decimais     |  
aliquota_icms_st                |  pICMSST    |  Sim          |  Decimal   | Até 3 dígitos, 4 casas decimais     |
valor_icms_st                   |  vICMSST    |  Sim          |  Decimal   | Até 13 dígitos, 2 casas decimais    |

### situacao_tributaria = 40, 41 e 50

40 =  Isenta
41 =  Não tributada
50 =  Suspensão

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
valor_icms_desonerado           |  vICMSDeson   |  Não          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
motivo_desoneracao              |  motDesICMS   |  Não          |  Numérico  |  2 dígitos                          |  Informar o motivo da desoneração:<br>1 = Táxi<br>3 = Produto Agropecuário<br>4 = Frotista/Locadora<br>5 = Diplomático/Consular<br>6 = Utilitários e Motocicletas da Amazônia Ocidental e Áreas de Livre Comércio<br>7 = SUFRAMA<br>8 = Venda a Órgão Público<br>9 = Outros<br>10 = Deficiente Condutor<br>11 = Deficiente Não Condutor<br>12 = Órgão de fomento e desenvolvimento agropecuário<br>

### situacao_tributaria = 41 e ICMSST devido para a UF de destino

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
base_calculo_icmsst_remetente   |  vBCSTRet     |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
valor_icmsst_retido_remetente   |  vICMSSTRet   |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
base_calculo_icmsst_destino     |  vBCSTDest    |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   | 
valor_icmsst_retido_destino     |  vICMSSTDest  |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |


### situacao_tributaria = 51

Diferido.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
modalidade_base_calculo         |  modBC        |  Sim          |  Numérico  |  1 dígito                           |  0=Margem Valor Agregado (%);<br>1=Pauta (Valor);<br>2=Preço Tabelado Máx. (valor);<br>3=Valor da operação.<br>
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
perc_reducao_base_calculo       |  pRedBC       |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |    
aliquota_icms                   |  pICMS        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms                      |  vICMS        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
valor_icms_operacao             |  vICMSOp      |  Não          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor como se não tivesse o diferimento.
perc_diferimento                |  pDif         |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  No caso de diferimento total, informar o percentual de diferimento "100".
valor_icms_diferido             |  vICMSDif     |  Não          |            |  Até 13 dígitos, 2 casas decimais   |

### situacao_tributaria = 60  

Cobrado anteriormente por ST.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
base_icmsst_retido              |  vBCSTRet     |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor da Base de Cálculo do ICMS ST cobrado anteriormente por ST. O valor pode ser omitido quando a legislação não exigir a sua informação.
valor_icmsst_retido             |  vICMSSTRet   |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor do ICMS ST cobrado anteriormente por ST. O valor pode ser omitido quando a legislação não exigir a sua informação.

### situacao_tributaria = 70 e 90  

70 = Com redução da base de cálculo e cobrança por ST  
90 = Outras  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
modalidade_base_calculo         |  modBC        |  Sim          |  Numérico  |  1 dígito                           |  0=Margem Valor Agregado (%);<br>1=Pauta (Valor);<br>2=Preço Tabelado Máx. (valor);<br>3=Valor da operação.
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
perc_reducao_base_calculo       |  pRedBC       |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
aliquota_icms                   |  pICMS        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms                      |  vICMS        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
valor_icms_desonerado           |  vICMSDeson   |  Não          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |
motivo_desoneracao              |  motDesICMS   |  Não          |  Numérico  |  2 dígitos                          |  Informar o motivo da desoneração: <br>1 = Táxi<br>3 = Produto Agropecuário<br>4 = Frotista/Locadora<br>5 = Diplomático/Consular<br>6 = Utilitários e Motocicletas da Amazônia Ocidental e Áreas de Livre Comércio<br>7 = SUFRAMA<br>8 = Venda a Órgão Público<br>9 = Outros<br>10 = Deficiente Condutor<br>11 = Deficiente Não Condutor<br>12 = Órgão de fomento e desenvolvimento agropecuário<br>
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico  |  1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).<br>
valor_base_calculo_st           |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   | 
perc_reducao_base_calculo_st    |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
perc_mva_icms_st                |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
aliquota_icms_st                |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms_st                   |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |

com partilha do ICMS entre a UF de origem e a UF de destino ou a UF definida na legislação

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
base_calculo_operacao_propria   |  pBCOp        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  Percentual para determinação do valor da Base de Cálculo da operação própria.
uf_icmsst_devido                |  UFST         |  Sim          |  Texto     |  2 carac.                           |  Sigla da UF para qual é devido o ICMS ST da operação.

### situacao_tributaria = 101   

Tributada com permissão de crédito.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos                          |  situacao_simples_nacional
aliquota_icms_simples_nacional  |  pCredSN      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |  aliquota_icms_simples_nacional  
credito_icms_simples_nacional   |  vCredICMSSN  |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  credito_icms_simples_nacional

### situacao_tributaria = 102  

Tributada sem permissão de crédito.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |   Sim         |  Numérico  |  3 dígitos                          |

### situacao_tributaria = 103

Isenção de ICMS.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos                          |

### situacao_tributaria = 201

Tributada com permissão de crédito e com cobrança de ICMS por ST.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos                          |  
aliquota_icms_simples_nacional  |  pCredSN      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
credito_icms_simples_nacional   |  vCredICMSSN  |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico  |  1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).
valor_base_calculo_st           |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
perc_reducao_base_calculo_st    |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
perc_mva_icms_st                |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
aliquota_icms_st                |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms_st                   |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |

### situacao_tributaria = 202  

Tributada sem permissão de crédito e com cobrança de ICMS por ST.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico  |  1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).
valor_base_calculo_st           |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  
perc_reducao_base_calculo_st    |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
perc_mva_icms_st                |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
aliquota_icms_st                |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |
valor_icms_st                   |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |

### situacao_tributaria = 203  

Isenção de ICMS pela faixa de receita bruta e com cobrança de ICMS por ST.  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos                          
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico  |  1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).
valor_base_calculo_st           |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
perc_reducao_base_calculo_st    |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais
perc_mva_icms_st                |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais
aliquota_icms_st                |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_icms_st                   |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 300  

Imune.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos 

### situacao_tributaria = 400

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos

### situacao_tributaria = 500

ICMS cobrado anteriormente por ST ou antecipação.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos
base_icmsst_retido              |  vBCSTRet     |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor da Base de Cálculo do ICMS ST cobrado anteriormente por ST. O valor pode ser omitido quando a legislação não exigir a sua informação.
valor_icmsst_retido             |  vICMSSTRet   |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor do ICMS ST cobrado anteriormente por ST. O valor pode ser omitido quando a legislação não exigir a sua informação.

### situacao_tributaria = 900  

Outros.  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------|------------|-------------------------------------|------------
situacao_simples_nacional       |  CSOSN        |  Sim          |  Numérico  |  3 dígitos       
aliquota_icms_simples_nacional  |  pCredSN      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
credito_icms_simples_nacional   |  vCredICMSSN  |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
modalidade_base_calculo         |  modBC        |  Sim          |  Numérico  |  1 dígito                           |  0=Margem Valor Agregado (%);<br>1=Pauta (Valor);<br>2=Preço Tabelado Máx. (valor);<br>3=Valor da operação.
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais    
perc_reducao_base_calculo       |  pRedBC       |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
aliquota_icms                   |  pICMS        |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_icms                      |  vICMS        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
modalidade_base_calculo_st      |  modBCST      |  Sim          |  Numérico  |  1 dígito                           |  0=Preço tabelado ou máximo sugerido;<br>1=Lista Negativa (valor);<br>2=Lista Positiva (valor);<br>3=Lista Neutra (valor);<br>4=Margem Valor Agregado (%);<br>5=Pauta (valor).
valor_base_calculo_st           |  vBCST        |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   
perc_reducao_base_calculo_st    |  pRedBCST     |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais
perc_mva_icms_st                |  pMVAST       |  Não          |  Decimal   |  Até 3 dígitos, 4 casas decimais
aliquota_icms_st                |  pICMSST      |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_icms_st                   |  vICMSST      |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
valor_icms_operacao             |  vICMSOp      |  Não          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |  Valor como se não tivesse o diferimento.

### ipi (XML: IPI)

Atributos comuns a todas as situações tributárias

### situacao_tributaria

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
CST                             |  Sim          |  Numérico  |  2 dígitos                          |

### clss_enquadramento

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
clEnq                           |  Não          |  Texto     |  Até 5 caracteres                    

### cnpj_produtor

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
CNPJProd                        |  Não          |  Numérico  |  14 dígitos        

### codigo_selo_controle
 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
cSelo                           |  Não          |  Texto     |  Até 60 caracteres                  |

### qtd_selo_controle

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
qSelo                           |  Não          |  Numérico  |  Até 12 dígitos        

### codigo_enquadramento

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
cEnq                            |  Sim          |  Numérico  |  Até 3 dígitos                      |  Geralmente o valor informado é 999

### situacao_tributaria = 00, 49, 50 e 99

00 = Entrada com recuperação de crédito.  
49 = Outras entradas  
50 = Saída tributada  
99 = Outra saídas  

### Cálculo por alíquota  

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
valor_base_calculo              |  vBC          |  Sim       |  Decimal                            |  Até 13 dígitos, 2 casas decimais

### aliquota_ipi

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
pIPI                            |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais    |

### valor_ipi

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
vIPI                            |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   

### Cálculo por valor

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
quantidade_unidade_tributavel   |  qUnid        |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais | Quantidade total na unidade padrão para tributação (somente para os produtos tributados por unidade)
valor_unidade_tributavel        |  vUnid        |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais |
valor_ipi                       |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 01

Entrada tributada com alíquota zero. Não possui campos para informar alíquota.

### situacao_tributaria = 02
Entrada Isenta. Não possui campos para informar alíquota.

### situacao_tributaria = 03
Entrada não-tributada. Não possui campos para informar alíquota.

### situacao_tributaria = 04
Entrada imune. Não possui campos para informar alíquota.

### situacao_tributaria = 05
Entrada com suspensão. Não possui campos para informar alíquota.

### situacao_tributaria = 51
Saída tributada com alíquota zero. Não possui campos para informar alíquota.

### situacao_tributaria = 52
Saída isenta. Não possui campos para informar alíquota.

### situacao_tributaria = 53
Saída não-tributada. Não possui campos para informar alíquota.

### situacao_tributaria = 54
Saída imune. Não possui campos para informar alíquota.

### situacao_tributaria = 55
Saída com suspensão. Não possui campos para informar alíquota.

### imposto_devolvido (XML: impostoDevol)  

O motivo da devolução deverá ser informado pela empresa no campo de Informações Adicionais do Produto.  

### perc_mercadoria_devolvida

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
pDevol                          |  Sim          |  Decimal   |  Até 3 dígitos, 2 casas decimais    |

### valor_ipi_devolvido

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
vIPIDevol                       |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais   |

### pis (XML: PIS)

Atributos comuns a todas as situações tributárias

### situacao_tributaria

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
CST                             |  Sim          |  Numérico  |  2 dígitos   

### situacao_tributaria = 01 e 02  

01 = Operação Tributável com Alíquota Básica  
02 = Operação Tributável com Alíquota Diferenciada  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais    
aliquota_pis                    |  pPIS         |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais 
valor_pis                       |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 03  

Operação Tributável com Alíquota por Unidade de Medida de Produto.  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_pis_reais              |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais
quantidade_vendida              |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais
valor_pis                       |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 04, 06, 07, 08, 09  

04 = Operação Tributável Monofásica - Revenda a Alíquota Zero  
06 = Operação Tributável a Alíquota Zero  
07 = Operação Isenta da Contribuição  
08 = Operação sem Incidência da Contribuição  
09 = Operação com Suspensão da Contribuição  

Não há campos para informar alíquota.  

### situacao_tributaria = 05

Operação Tributável por Substituição Tributária.

### Cálculo por percentual

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo_st           |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
aliquota_st                     |  pPIS         |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_pis_st                    |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### Cálculo por valor

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_pis_reais_st           |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais
quantidade_vendida_st           |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais
valor_pis_st                    |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

situacao_tributaria = 49, 50, 51, 52, 53, 54, 55, 56, 60, 61, 62, 63, 64, 65, 66, 67, 70, 71, 72, 73, 74, 75, 98, 99  

49 = Outras Operações de Saída  
50 = Operação com Direito a Crédito - Vinculada Exclusivamente a Receita Tributada no Mercado Interno  
51 = Operação com Direito a Crédito – Vinculada Exclusivamente a Receita Não Tributada no Mercado Interno  
52 = Operação com Direito a Crédito - Vinculada Exclusivamente a Receita de Exportação  
53 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno  
54 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas no Mercado Interno e de Exportação  
55 = Operação com Direito a Crédito - Vinculada a Receitas Não-Tributadas no Mercado Interno e de Exportação  
56 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno, e de Exportação  
60 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita Tributada no Mercado Interno  
61 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita Não-Tributada no Mercado Interno  
62 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita de Exportação  
63 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno  
64 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas no Mercado Interno e de Exportação  
65 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Não-Tributadas no Mercado Interno e de Exportação  
66 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno, e de Exportação  
67 = Crédito Presumido - Outras Operações  
70 = Operação de Aquisição sem Direito a Crédito  
71 = Operação de Aquisição com Isenção  
72 = Operação de Aquisição com Suspensão  
73 = Operação de Aquisição a Alíquota Zero  
74 = Operação de Aquisição sem Incidência da Contribuição  
75 = Operação de Aquisição por Substituição Tributária  
98 = Outras Operações de Entrada  
99 = Outras Operações  

### Cálculo por percentual

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |   Até 13 dígitos, 2 casas decimais       
aliquota_pis                    |  pPIS         |  Sim          |  Decimal   |   Até 3 dígitos, 4 casas decimais
valor_pis                       |  vIPI         |  Sim          |  Decimal   |   Até 13 dígitos, 2 casas decimais  

### Cálculo por valor

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_pis_reais              |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais 
quantidade_vendida              |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais
valor_pis                       |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### cofins (XML: COFINS)  

Atributos comuns a todas as situações tributárias

### situacao_tributaria

 Campo XML  |  Obrigatório  |  Tipo      |  Formato e tamanho |  Observações
------------|---------------|------------|--------------------|------------
CST         |  Sim          |  Numérico  |  2 dígitos         |

### situacao_tributaria = 01 e 02  

01 = Operação Tributável com Alíquota Básica  
02 = Operação Tributável com Alíquota Diferenciada  

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
aliquota_cofins                 |  pPIS         |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_cofins                    |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 03  

Operação Tributável com Alíquota por Unidade de Medida de Produto.

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_cofins_reais           |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais |
quantidade_vendida              |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais |
valor_cofins                    |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais        |

### situacao_tributaria = 04, 06, 07, 08, 09   

04 = Operação Tributável Monofásica - Revenda a Alíquota Zero  
06 = Operação Tributável a Alíquota Zero  
07 = Operação Isenta da Contribuição  
08 = Operação sem Incidência da Contribuição  
09 = Operação com Suspensão da Contribuição  

Não há campos para informar alíquota.  

### situacao_tributaria = 05  

Operação Tributável por Substituição Tributária.

### Cálculo por percentual

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo_st           |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais        |
aliquota_st                     |  pPIS         |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais         |
valor_cofins_st                 |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais        |


### Cálculo por valor

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_cofins_reais_st        |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais
quantidade_vendida_st           |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais
valor_cofins_st                 |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### situacao_tributaria = 49, 50, 51, 52, 53, 54, 55, 56, 60, 61, 62, 63, 64, 65, 66, 67, 70, 71, 72, 73, 74, 75, 98, 99

49 = Outras Operações de Saída  
50 = Operação com Direito a Crédito - Vinculada Exclusivamente a Receita Tributada no Mercado Interno  
51 = Operação com Direito a Crédito – Vinculada Exclusivamente a Receita Não Tributada no Mercado Interno  
52 = Operação com Direito a Crédito - Vinculada Exclusivamente a Receita de Exportação  
53 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno  
54 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas no Mercado Interno e de Exportação  
55 = Operação com Direito a Crédito - Vinculada a Receitas Não-Tributadas no Mercado Interno e de Exportação  
56 = Operação com Direito a Crédito - Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno, e de Exportação  
60 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita Tributada no Mercado Interno  
61 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita Não-Tributada no Mercado Interno  
62 = Crédito Presumido - Operação de Aquisição Vinculada Exclusivamente a Receita de Exportação  
63 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno  
64 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas no Mercado Interno e de Exportação  
65 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Não-Tributadas no Mercado Interno e de Exportação  
66 = Crédito Presumido - Operação de Aquisição Vinculada a Receitas Tributadas e Não-Tributadas no Mercado Interno, e de Exportação  
67 = Crédito Presumido - Outras Operações  
70 = Operação de Aquisição sem Direito a Crédito  
71 = Operação de Aquisição com Isenção  
72 = Operação de Aquisição com Suspensão  
73 = Operação de Aquisição a Alíquota Zero  
74 = Operação de Aquisição sem Incidência da Contribuição  
75 = Operação de Aquisição por Substituição Tributária  
98 = Outras Operações de Entrada  
99 = Outras Operações  

### Cálculo por percentual

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
valor_base_calculo              |  vBC          |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais
aliquota_cofins                 |  pPIS         |  Sim          |  Decimal   |  Até 3 dígitos, 4 casas decimais
valor_cofins                    |  vIPI         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### Cálculo por valor

 Campo                          |  XML          |  Obrigatório  |  Tipo      |  Formato e tamanho                       |  Observações
--------------------------------|---------------|---------------|------------|------------------------------------------|------------
aliquota_cofins_reais           |  vAliqProd    |  Sim          |  Decimal   |  Até 11 dígitos, de 0 a 4 casas decimais
quantidade_vendida              |  qBCProd      |  Sim          |  Decimal   |  Até 12 dígitos, de 0 a 4 casas decimais
valor_cofins                    |  vPIS         |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

## transporte (XML: transp)

Contém informações sobre o frete e o transporte dos produtos ou serviços. Seus atributos são:  

### modalidade_frete  

Seleção entre:
0 = Por conta do emitente;
1 = Por conta do destinatário/remetente;
2 = Por conta de terceiros;
9 = Sem frete.

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
modFrete                        |  Sim          |  Numérico  |  1 dígito

### valor_frete

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
vServ                           |  Sim          |  Decimal   |  Até 13 dígitos, 2 casas decimais

### transportadora (XML: transporta)

Grupo de informações relacionadas à transportadora, caso haja frete.

### razao_social

Nome (pessoa física) ou Razão Social (Pessoa Jurídica).

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
xNome                           |  Não          |  Texto     |  Até 60 caracteres

### cnpj_cpf
Campo no XML

 Campo                          |  Obrigatório  |  Tipo      |  Formato e tamanho                  |  Observações
--------------------------------|---------------|------------|-------------------------------------|------------
CNPJ ou CPF                     |  Não          |  Numérico  |  14 ou 11 dígitos

### inscricao_estadual  

Inscrição Estadual do transportador contribuinte do ICMS, sem caracteres de formatação (ponto, barra, hífen, etc.). Pode ser informado o texto “ISENTO” para transportador isento de inscrição no cadastro de contribuintes ICMS. Não informar a tag para não contribuinte do ICMS. A UF deve ser informada se informado uma IE.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
IE                              |  Não          |  Texto e/ou número  |  De 2 a 14 caracteres

### endereco_completo

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
xEnder                          |  Não          |  Texto              |  Até 60 caracteres                  |

### uf

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
UF                              |  Não          |  Texto              |  2 caracteres                       |  Sigla da UF

### municipio

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
xMun                            |  Não          |  Texto              |  Até 60 caracteres

### retencao_icms (XML: retTransp)  

Informações de retenção de ICMS de transporte.  

### cfop  

CFOP de serviço de transporte.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
CFOP                            |  Não          |  Numérico           |  4 dígitos                          |

### valor_base_calculo

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vBCRet                          |  Sim          |  Decimal            |  Até 13 dígitos, 2 casa decimais

### aliquota_retencao

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
pICMSRet                        |  Sim          |  Decimal            |  Até 3 dígitos, de 2 a 4 casas decimais

### valor_retido

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vICMSRet                        |  Sim          |  Decimal            |  Até 13 dígitos, 2 casas decimais

### uf

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
-                               |  Não          |  Texto              |  2 caracteres                       |  Sigla da UF

### codigo_municipio

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
cMunFG                          |  Sim          |  Numérico           |  7 dígitos                          |  Código do município de acordo com tabela do IBGE

### veiculo (XML: veicTransp)  

Dados do veículo utilizado para transporte, caso haja frete. O campo pode ser omitido caso não haja frete.
placa  

Informar em um dos seguintes formatos: XXX9999, XXX999, XX9999 ou XXXX999. Informar a placa em informações complementares quando a placa do veículo tiver lei de formação diversa.

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
placa                           |  Sim          |  Texto e/ou número  |  7 caracteres

### uf

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
UF                              |  Sim          |  Texto              |  2 caracteres                       |  Sigla da UF

### rntc  

Registro Nacional de Transporte de Carga.   

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
RNTC                            |  Não          |  Texto              |  Até 20 caracteres

### volume_transportado (XML: vol)  

Informações dos volumes transportados, se houver. Uma nota comporta até 5.000 volumes. Cada volume deve possuir os conjuntos de campos a seguir:

### quantidade_volumes

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
qVol                            |  Não          |  Numérico           |  Até 15 dígitos   

### especie

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
esp                             |  Não          |  Texto              |  Até 60 caracteres

### marca

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
marca                           |  Não          |  Texto              |  Até 60 caracteres

### numeracao

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nVol                            |  Não          |  Texto              |  Até 60 caracteres

### peso_liquido  

Peso líquido em quilogramas (kG).

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
peslL                           |  Não          |  Decimal            |  Até 12 dígitos, 3 casas decimais

### peso_bruto  

Peso bruto em quilogramas (kG).

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
pesoB                           |  Não          |  Decimal            |  Até 12 dígitos, 3 casas decimais

### lacres (XML: lacres)  

Cada volume transportador pode conter lacres, sendo até 5.000 por volume.  

### Item da coleção (array) de lacres  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nLacre                          |  Sim          |  Texto              |  Até 60 caracteres

## cobranca (XML: infNFe)

Informações opcionais de cobrança. Seus atributos são:  

### fatura (XML: fat)

Subgrupo de informações relacionadas aos dados da fatura. Possui somente uma ocorrência. Apresenta os seguintes atributos:

### numero_fatura  

Número da fatura.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nFat                            |  Não          |  Texto e/ou número  |  Até 60 caracteres

### valor_original  

Valor original (bruto) da fatura.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vOrig                           |  Não          |  Decimal            |  13 dígitos, 2 casas decimais       |

### valor_desconto  

Valor aplicado de desconto.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vDesc                           |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_liquido  

Valor líquido da fatura.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vLiq                            |  Não          |  Decimal            |  13 dígitos, 2 casas decimais       

### duplicata (XML: dup)  

Subgrupo de informações relacionadas às duplicatas (parcelas da compra). Pode conter até 200 ocorrências e possui os seguintes atributos:  

### numero  

Número da duplicata.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nDup                            |  Não          |  Texto e/ou número  |  Até 60 caracteres

### data_vencimento  

Data de vencimento da duplicata  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
dVenc                           |  Não          |  Data               |  AAAA-MM-DD                         |

### valor  

Valor da duplicata.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vDup                            |  Sim          |  Decimal            |  13 dígitos, 2 casas decimais

## documentos_referenciados (XML: infNFe)

Este campo é utilizado para referenciar uma Nota Fiscal, modelo 1 ou 1-A, ou NF-e emitida anteriormente e vinculada à NF-e que está sendo emitida. Cabe observar que esta informação será utilizada quando o regulamento do ICMS determinar indicação dos dados de outra nota fiscal referente àquela operação, como, por exemplo, nos casos de devolução de mercadoria, complementação de imposto etc.   

Seus atributos são:  

### tipo_documento  

Campo interno do Emites para indicar o tipo do documento. Os valores podem ser: NFe, NF ou Cupom.

### tipo_documento = “NFe”  

Para notas fiscais eletrônicas relacionadas, é necessário somente a chave de acesso.

### chave_acesso  

Referencia uma NF-e (modelo 55) emitida anteriormente, vinculada à NF-e atual, ou uma NFC-e (modelo 65).

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
refNFe                          |  Sim          |  Numérico           |  44 dígitos

### tipo_documento = “NF”  

Para notas fiscais físicas, os atributos são:  

### codigo_uf_emitente

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
cUF                             |  Sim          |  Numérico           |  2 dígitos                          |  Código de acordo com tabela IBGE

### ano_mes_emissao

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
AAMM                            |  Sim          |  Numérico           |  ano (AA) e mês (MM) de emissão da NF

### modelo_documento

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
mod                             |  Sim          |  Numérico           |  2 dígitos                          |  01 = modelo 01

### numero_documento
 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nNF                             |  Sim          |  Numérico           |  Até 9 dígitos

### serie_documento

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
serie                           |  Sim          |  Numérico           |  Até 3 dígitos                      |  Informar zero se não utilizada a série do documento fiscal.

### cnpj emitente

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
CNPJ                            |  Sim          |  Numérico           |  14 dígitos

### tipo_documento = “Cupom”

Além dos campos similares à nota fiscal física, o cupom fiscal tem os seguintes atributos:  

### numero_ecf

Número de ordem sequencial de ECF.

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nECF                            |  Sim          |  Numérico           |  3 dígitos                          |

### numero_coo

Número do Contador de Ordem de Operação (COO).

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
nCOO                            |  Sim          |  Numérico           |  6 dígitos  

## retencoes (XML: retTrib)

### valor_retido_pis

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vRetPIS                         |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_retido_cofins

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vRetCOFINS                      |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_retido_csll

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vRetCSLL                        |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_base_calculo_irrf

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vBCIRRF                         |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_irrf

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vIRRF                           |  Não          |  Decimal            |  13 dígitos, 2 casas decimais 

### base_calculo_retencao_previdencia

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vBCRetPrev                      |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

### valor_retencao_previdencia

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
vRetPrev                        |  Não          |  Decimal            |  13 dígitos, 2 casas decimais

## exporta (XML: exporta)  

Informações de comércio exterior.

### uf_embarque

Sigla da UF de Embarque ou de transposição de fronteira.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
UFSaidaPais                     |  Sim          |  Texto              |  2 caracteres                       |  Sigla da UF

### local_embarque

Descrição do Local de Embarque ou de transposição de fronteira.

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
xLocExporta                     |  Sim          |  Texto              |  Até 60 caracteres                  |

### local_despacho  

Descrição do local de despacho.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
xLocDespacho                    |  Sim          |  Texto              |  Até 60 caracteres

## informacoes_adicionais (XML: infAdic)  

Grupo de informações adicionais da NF-e. Seus atributos são:  

### informacoes_contribuinte  

Informações complementares de interesse do Contribuinte.

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
infCpl                          |  Não          |  Texto              |  Até 2.000 caracteres               

### informacoes_fisco  

Informações adicionais de interesse do Fisco.  

 Campo                          |  Obrigatório  |  Tipo               |  Formato e tamanho                  |  Observações
--------------------------------|---------------|---------------------|-------------------------------------|------------
infAdFisco                      |  Não          |  Texto              |  Até 2.000 caracteres


