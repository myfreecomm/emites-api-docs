# Campos da emissão de nota

## Emissão em lote 

Todas as notas fiscais são emitidas em lote, mesmo em caso de emissão de uma única nota. A emissão em lote gera um pacote de transmissão de diversas notas fiscais eletrônicas, que são processadas em conjunto. Isto permite maior agilidade para emissão de um grande volume de notas. Cada lote pode conter até 50 NF-e ou NFC-e. Os atributos do lote da nota são:

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    lote                        | idLote          |   Sim         |     Numérico            |    De 1 a 15 dígitos         |    Identificador de controle do envio do lote. Deve ser um número sequencial e autoincremental, sendo um identificador único do lote.
    sincronicidade              | indSinc         |   Sim         |     Numérico            |    1 dígitos                 |    0 = Não<br>1 = Empresa solicita processamento síncrono do Lote de NF-e (sem a geração de Recibo para consulta futura)<br>O processamento síncrono do Lote corresponde a entrega da resposta do processamento das NF-e do Lote, sem a geração de um Recibo de Lote para consulta futura. A resposta de forma síncrona pela SEFAZ Autorizadora só ocorrerá se:<br>- a empresa solicitar e constar unicamente uma NFe
    uf                          | -               |   Sim         |     Numérico            |    2 dígitos                 |    Campo interno do Emites para indicar o estado de emissão da NF-e/NFC-e e direcionar ao servidor da SEFAZ correspondente
    nfes                        | NF-e            |   Sim         |     Array               |    Até 50 itens              |    Conjunto de NF-e transmitidas, máximo de 50 NF-e


## dados_gerais (XML: ide)  

Contém informações gerais e metadados sobre a NF-e. Seus atributos são:

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    uf                          |   cUF           |  Sim          |     Numérico            |    2 dígitos                 |   Código da UF do emitente do Documento Fiscal.
    serie                       |   serie         |  Sim          |     Numérico            |    Até 3 dígitos             |   Série do Documento Fiscal. Informar 0 (zero) para série única.
    codigo_mun_ocorrencia       |   cMunFG        |  Sim          |     Numérico            |    7 dígitos                 |   Código do Município de Ocorrência do Fato Gerador.
    nfe_numero                  |   nNF           |  Sim          |     Numérico            |                              |   Número do Documento Fiscal.
    data_saida_entrada          |   dhSaiEnt      |  Não          |     Data                |    aaaa-mm-ddThh:mm:ss-03:00 |   Data e hora de Saída ou da Entrada da Mercadoria/Produto.  
    tipo_operacao               |   tpNF          |  Sim          |     Numérico            |    1 dígito                  |   Tipo de Operação, sendo 0 = Entrada e 1 = Saída.  
    tipo_emissão                |   tpEmiss       |  Sim          |     Numérico            |    1 dígito                  |   1 = Emissão normal (não em contingência); <br> 2 = Contingência FS-IA, com impressão do DANFE em formulário de segurança; <br> 3 = Contingência SCAN (Sistema de Contingência do Ambiente Nacional); <br> 4 = Contingência DPEC (Declaração Prévia da Emissão em Contingência); <br> 5 = Contingência FS-DA, com impressão do DANFE em formulário de segurança; <br> 6 = Contingência SVC-AN (SEFAZ Virtual de Contingência do AN); <br> 7 = Contingência SVC-RS (SEFAZ Virtual de Contingência do RS); <br> 9 = Contingência off-line da NFC-e (as demais opções de contingência são válidas também para a NFC-e).
    destino_operacao            |   idDest        |  Sim          |     Numérico            |    1 dígito                  |   Identificador de Local de destino da operação (1 - Interna; 2 - Interestadual; 3 - Exterior).
    natureza_operacao           |   natOp         |  Sim          |     Texto  e/ou número  |    1 a 60 caracteres         |   Informar a natureza da operação de que decorrer a saída ou a entrada, tais como venda, compra, transferência, devolução, importação, consignação, remessa (para fins de demonstração, de industrialização ou outra), conforme previsto na alínea 'i', inciso I, do art. 19 do Convênio s/nº de 15 de dezembro de 1970. 
    indicador_pagamento         |   indPag        |  Sim          |     Numérico            |    1 dígito                  |   Indicador da forma de pagamento. Seleção entre:   0 = pagamento a vista   1 = pagamento a prazo   2 = outros. 
    indicador_consumidor_final  |   indFinal      |  Sim          |     Numérico            |    1 dígito                  |   Indica se a NF-e foi emitida para consumidor final, sendo 0 = Não e 1 = Sim.  
    indicador_presenca          |   indPres       |  Sim          |     Numérico            |    1 dígito                  |   Indicador de presença do comprador no estabelecimento comercial no momento da operação. Seleção entre:<br>0 = Não se aplica (por exemplo, Nota Fiscal complementar ou de ajuste);<br>1 = Operação presencial;<br>2 = Operação não presencial, pela Internet;<br>3   = Operação não presencial, Teleatendimento;<br>4 = NFC-e em operação com entrega a domicílio;<br>9 = Operação não presencial, outros.<br>
    finalidade_nfe              |   finNFe        |  Sim          |     Numérico            |    1 dígito                  |   Finalidade de emissão da NF-e. Seleção entre:   1 - NF-e normal   2 - NF-e complementar   3 - NF-e de ajuste  
    valor_total_nota            |   vNF           |  Sim          |     Decimal             |                              |   Somatória do Valor Total dos Produtos ou Serviços e determinados impostos. Calculado automaticamente pelo Emites.  
    indicador_incentivo_fiscal  |   indIncentivo  |  Sim          |     Numérico            |    1 dígito                  |   Indicador de incentivo fiscal, sendo 1 = Sim, 2 = Não.  

## cliente (XML: dest)  

Contém informações sobre o destinatário da aquisição dos produtos do emitente (nota de saída) ou venda dos produtos para o emitente (nota de entrada). Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|----------------------------------------------------------- 
    cpf_cnpj                    |   CPF ou CNPJ   |  Sim          |  Numérico               |  11 ou 14 dígitos            |  CPF ou CNPJ do destinatário, somente números.
    nome                        |   xNome         |  Sim          |  Texto                  |  Até 60 caracteres           |  Razão social ou nome do destinatário  
    pessoa_fisica_juridica      |   -             |  Sim          |  Texto                  |  -                           |  Campo de controle do Emites para indicar se o destinatário é pessoa física (“person”) ou jurídica (“company”).
    inscricao_estadual          |   IE            |  Não          |  Numérico               |  Até 14 dígitos              |  Informar somente os algarismos, sem ponto, hífen, barra, etc.  
    inscricao_suframa           |   ISUF          |  Não          |  Numérico               |  De 8 a 9 dígitos            |  Obrigatório nas operações que se beneficiam de incentivos fiscais existentes nas áreas sob controle da SUFRAMA. A omissão desta informação impede o processamento da operação pelo Sistema de Mercadoria Nacional da SUFRAMA e a liberação da Declaração de Ingresso, prejudicando a comprovação do ingresso / internamento da mercadoria nestas áreas.
    inscricao_municipal         |   IM            |  Não          |  Texto                  |  Até 15 caracteres           |  
    indicador_inscricao_estadual|   indIEDest     |  Sim          |  Numérico               |  1 dígito                    |  Indica se o destinatário é contribuinte do ICMS. Seleção entre:<br>1 = Contribuinte ICMS (informar a IE do destinatário);<br> 2  = Contribuinte isento de Inscrição no cadastro de Contribuintes do ICMS;<br>9 = Não Contribuinte, que pode ou não possuir Inscrição Estadual no Cadastro de Contribuintes do ICMS.
    email                       |   email         |  Não          |  Texto                  |  Até 60 caracteres           |  

### endereco (XML: enderDest)  

Grupo de informações relacionadas ao endereço do destinatário. Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|----------------------------------------------------------- 
    logradouro                  |  xLgr           |  Sim          |  Texto                  |  Até 60 caracteres           |  
    numero                      |  nro            |  Sim          |  Texto                  |  Até 60 caracteres           |  
    complemento                 |  xCpl           |  Não          |  Texto                  |  Até 60 caracteres           |  
    bairro                      |  xBairro        |  Sim          |  Texto                  |  Até 60 caracteres           |  
    codigo_municipio            |  cMun           |  Sim          |  Numérico               |  7 dígitos                   |  
    nome_municipio              |  xMun           |  Sim          |  Texto                  |  Até 60 caracteres           |  
    cep                         |  CEP            |  Sim          |  Numérico               |  8 dígitos                   |  
    uf                          |  UF             |  Sim          |  Texto                  |  2 caracteres                |  
    codigo_pais                 |  cPais          |  Não          |  Numérico               |  4 dígitos                   |  
    nome_pais                   |  xPais          |  Não          |  Texto                  |  Até 60 caracteres           |  
    telefone                    |  fone           |  Não          |  Numérico               |  De 6 a 14 carateres         |  

## lista_autorizacao (XML: autXML)

Conjunto de pessoas ou empresas autorizadas a obter o XML. Seus atributos são:

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------|-----------------------------------------------------------
    Número do CNPJ ou CPF       |   CNPJ          |   Sim         |     Numérico            |    14 dígitos                |    Deve ser informado o CNPJ ou CPF
                                |   CPF           |   Sim         |     Numérico            |    11 dígitos                |


## produto (XML: prod)  

Contém informações sobre os produtos contidos na NF-e. No XML, o nó  prod  é subitem do nó  det  e pode conter uma ou mais ocorrência. Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho              |   Observações
--------------------------------|-----------------|---------------|-------------------------|-----------------------------------|----------------------------------------------------------- 
    codigo_produto              |    cProd        |  Sim          |     Texto e/ou número   |  Até 60 caracteres                |  Codificação própria da empresa. Preencher com CFOP, caso se trate de itens não relacionados com mercadorias/produtos e se o contribuinte não possuir codificação própria. Caso preenchido com CFOP, utilizar o formato "CFOP9999".  
    codigo_ean                  |    cEAN         |  Não          |     Numérico            |  8, 12, 13 ou 14 dígitos          |  Código de barras. Preencher com o código de barra GTIN-8, GTIN-12, GTIN-13 ou GTIN-14 (antigos códigos EAN, UPC e DUN- 14). Não informar este campo se o produto não possuir este código.
    descricao                   |    xProd        |  Sim          |     Texto               |  Até 120 caracteres               |  Descrição do produto.
    ncm                         |    NCM          |  Sim          |     Numérico            |  8 dígitos                        |  Nomenclatura comum do Mercosul. Itens específicos que não possuem NCM podem informar somente o código “00”.
    cest                        |    CEST         |               |                         |                                   |  Código Especificador de Substituição Tributária.
    extipi                      |    EXTIPI       |  Não          |     Numérico            |  De 2 a 3 dígitos                 |  
    cfop                        |    CFOP         |  Sim          |     Numérico            |  4 dígitos                        |  Código Fiscal de Operações e Prestações.
    produto_especifico          |         -       |       -       |            -            |          -                        |  -
    unidade_comercial           |    uCom         |  Sim          |     Texto               |  Até 6 caracteres                 |  Unidade de comercialização do produto.
    quantidade_comercial        |    qCom         |  Sim          |     Decimal             |  Até 11 dígitos, 4 casas decimais |  Quantidade de comercialização do produto.
    valor_unitario_comercial    |    vUnCom       |  Sim          |     Decimal             |  Até 11 dígitos, 4 casas decimais |  Valor unitário de comercialização.
    ean_unidade_trib            |    cEANTrib     |  Não          |     Numérico            |  8, 12, 13 ou 14 dígitos          |  
    unidade_tributaria          |    uTrib        |  Sim          |     Texto               |  Até 6 caracteres                 |  Unidade tributável do produto.
    quantidade_tributaria       |    qTrib        |  Sim          |     Decimal             |  Até 11 dígitos, 4 casas decimais |  Quantidade tributável do produto.
    valor_unitario_tributario   |    vUnTrib      |  Sim          |     Decimal             |  Até 11 dígitos, 10 casas decimais|  Valor unitário de tributação.
    valor_frete                 |    vFrete       |  Não          |     Decimal             |  Até 13 dígitos, 2 casas decimais |   
    valor_seguro                |  vSeg           |  Não          |     Decimal             |  Até 13 dígitos, 2 casas decimais |    
    valor_desconto              |  vDesc          |  Não          |     Decimal             |  Até 13 dígitos, 2 casas decimais |   
    outras_despesas             |  vOutro         |  Não          |     Decimal             |  Até 13 dígitos, 2 casas decimais |  Outras despesas acessórias.
    num_pedido                  |   xPed          |  Não          |     Texto e/ou número   |  Até 15 caracteres                |  Número do pedido de compra, se houver.
    num_item_pedido             |  nItemPed       |  Não          |     Numérico            |  Até 6 dígitos                    |  Item do pedido de compra.
    num_controle_fci            |   nFCI          |  Não          |     Texto               |  Até 36 caracteres                |  Número de controle da FCI - Ficha de Conteúdo de Importação.
    ind_valor_total             |  indTotal       |  Sim          |     Numérico            |  1 dígito                         |  Informa se o valor dos produtos compõem o valor total da nota. Seleção entre:<br>0 = Valor do item não compõem o valor total da NF-e;<br>1 = Valor do item compõem o valor total da NF-e.<br>

## tributação (XML: imposto)  

Grupo de informações relacionadas à tributação de ICMS, IPI, PIS, COFINS e Importação.  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    valor_aproximado_total      |  vTotalTrib     |  Não          |     Decimal             |  Até 13 dígitos, 2 casas decimais  |  Valor aproximado total de tributos federais, estaduais e municipais.

### icms (XML: ICMS)

Informações relacionadas ao ICMS. O atributos são variáveis de acordo com a situação tributária. Atributos comuns a todas as situações tributárias

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
situacao_tributaria             |  CST            |  Sim          |     Numérico            |    2 dígitos                       |  
codigo_origem_produto           |  orig           |  Sim          |     Numérico            |    1 dígito                        |  Origem da mercadoria. Seleção entre:<br>  0 = Nacional, exceto as indicadas nos códigos 3, 4, 5 e 8;  <br>1 = Estrangeira - Importação direta, exceto a indicada no código 6;  <br>2 = Estrangeira - Adquirida no mercado interno, exceto a indicada no código 7;  <br>3 = Nacional, mercadoria ou bem com Conteúdo de Importação superior a 40% e inferior ou igual a 70%;  <br>4 = Nacional, cuja produção tenha sido feita em conformidade com os processos produtivos básicos de que tratam as legislações citadas nos Ajustes;  <br>5 = Nacional, mercadoria ou bem com Conteúdo de Importação inferior ou igual a 40%;  <br>6 = Estrangeira - Importação direta, sem similar nacional, constante em lista da CAMEX e gás natural;  <br>7 = Estrangeira - Adquirida no mercado interno, sem similar nacional, constante lista CAMEX e gás natural.  <br>8 = Nacional, mercadoria ou bem com Conteúdo de Importação superior a 70%.  

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

#### com partilha do ICMS entre a UF de origem e a UF de destino ou a UF definida na legislação  

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

#### com partilha do ICMS entre a UF de origem e a UF de destino ou a UF definida na legislação

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

Não tributada

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

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    situacao_tributaria         |  CST            |  Sim          |     Numérico            |  2 dígitos                         |
    classe_enquadramento        |  clEnq          |  Não          |     Texto               |  Até 5 caracteres                  |                    
    cnpj_produtor               |  CNPJProd       |  Não          |     Numérico            |  14 dígitos                        |
    codigo_selo_controle        |  cSelo          |  Não          |     Texto               |  Até 60 caracteres                 |  Código do selo de controle IPI
    quantidade_selo_controle    |  qSelo          |  Não          |     Numérico            |  Até 12 dígitos                    |  Quantidade de selo de controle
    cod_enquadramento           |  cEnq           |  Sim          |     Numérico            |  Até 3 dígitos                     |  Geralmente o valor informado é 999

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

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    perc_mercadoria_devolvida   |  pDevol         |  Sim          |     Decimal             |  Até 3 dígitos, 2 casas decimais   |
    valor_ipi_devolvido         |  vIPIDevol      |  Sim          |     Decimal             |  Até 13 dígitos, 2 casas decimais  |

### pis (XML: PIS)

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    situacao_tributaria         |  CST            |  Sim          |  Numérico               |  2 dígitos                         |   Atributos comuns a todas as situações tributárias

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

Contém informações sobre o frete e o transporte dos produtos ou serviços.  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    modalidade_frete            |  modFrete       |  Sim          |  Numérico               |  1 dígito                          |  Seleção entre:<br>0 = Por conta do emitente;<br>1 = Por conta do destinatário/remetente;<br>2 = Por conta de terceiros;<br>9 = Sem frete.<br>
    valor_frete                 |  vServ          |  Sim          |  Decimal                |  Até 13 dígitos, 2 casas decimais

### transportadora (XML: transporta)

Grupo de informações relacionadas à transportadora, caso haja frete.

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|----------------------------------------------------------- 
    razao_social                |  xNome          |  Não          |  Texto                  |  Até 60 caracteres                 |  Nome (pessoa física) ou Razão Social (Pessoa Jurídica).
    cnpj_cpf                    |  CNPJ ou CPF    |  Não          |  Numérico               |  14 ou 11 dígitos                  |
    inscricao_estadual          |  IE             |  Não          |  Texto e/ou número      |  De 2 a 14 caracteres              |  Inscrição Estadual do transportador contribuinte do ICMS, sem caracteres de formatação (ponto, barra, hífen, etc.). Pode ser informado o texto “ISENTO” para transportador isento de inscrição no cadastro de contribuintes ICMS. Não informar a tag para não contribuinte do ICMS. A UF deve ser informada se informado uma IE.  
    endereco_completo           |  xEnder         |  Não          |  Texto                  |  Até 60 caracteres                 |
    uf                          |  UF             |  Não          |  Texto                  |  2 caracteres                      |  Sigla da UF
    municipio                   |  xMun           |  Não          |  Texto                  |  Até 60 caracteres                 |

### retencao_icms (XML: retTransp)  

Informações de retenção de ICMS de transporte.  

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------|-------------------------|------------------------------------|-----------------------------------------------------------
    cfop                        |  CFOP           |  Não          |  Numérico               |  4 dígitos                         |  CFOP de serviço de transporte.  
    valor_base_calculo          |  vBCRet         |  Sim          |  Decimal                |  Até 13 dígitos, 2 casa decimais   |
    aliquota_retencao           |  pICMSRet       |  Sim          |  Decimal                |  Até 3 dígitos, de 2 a 4 casas decimais|
    valor_retido                |  vICMSRet       |  Sim          |  Decimal                |  Até 13 dígitos, 2 casas decimais  |
    uf                          |  -              |  Não          |  Texto                  |  2 caracteres                      |  Sigla da UF
    codigo_municipio            |  cMunFG         |  Sim          |  Numérico               |  7 dígitos                         |  Código do município de acordo com tabela do IBGE

### endereco_entrega (XML: entrega) (h3)

Identificação do local de entrega. Informar somente se diferente do endereço destinatário. Seus atributos são:

    Campo                       |  Campo no XML   |  Obrigatório  |     Tipo                    |    Formato e tamanho         |   Observações
--------------------------------|-----------------|---------------|-----------------------------|------------------------------|----------------------------------------------------------- 
    cpf_cnpj                    |  CPF/CNPJ       |  Sim          |     Numérico                |    0, 11 ou 14 caracteres    |    Informar CNPJ ou CPF. Preencher os zeros não significativos.     
    logradouro                  |  xLgr           |  Sim          |     Texto                   |    Até 60 caracteres         |  
    numero                      |  nro            |  Sim          |     Texto                   |    Até 60 caracteres         |  
    complemento                 |  xCpl           |  Não          |     Texto                   |    Até 60 caracteres         |  
    bairro                      |  xBairro        |  Sim          |     Texto                   |    Até 60 caracteres         |  
    codigo_municipio            |  cMun           |  Sim          |     Numérico                |    7 dígitos                 |    Informar ‘9999999 ‘para operações com o exterior.
    nome_municipio              |  xMun           |  Sim          |     Texto                   |    Até 60 caracteres         |    Informar ‘EXTERIOR ‘para operações com o exterior.  
    uf                          |  UF             |  Sim          |     Texto                   |    2 caracteres              |    Informar ‘EX’ para operações com o exterior.


### veiculo (XML: veicTransp)  

Dados do veículo utilizado para transporte, caso haja frete. O campo pode ser omitido caso não haja frete.
placa  

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    placa                       |  Sim            |  Texto e/ou número  |  7 caracteres           |                                    |  Informar em um dos seguintes formatos: XXX9999, XXX999, XX9999 ou XXXX999. Informar a placa em informações complementares quando a placa do veículo tiver lei de formação diversa.
    uf                          |  UF             |  Sim                |  Texto                  |  2 caracteres                      |  Sigla da UF
    rntc                        |  RNTC           |  Não                |  Texto                  |  Até 20 caracteres                 |  Registro Nacional de Transporte de Carga.   

### volume_transportado (XML: vol)  

Informações dos volumes transportados, se houver. Uma nota comporta até 5.000 volumes. Cada volume deve possuir os conjuntos de campos a seguir:

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    quantidade_volumes          |  qVol           |  Não                |  Numérico               |  Até 15 dígitos   
    especie                     |  esp            |  Não                |  Texto                  |  Até 60 caracteres
    marca                       |  marca          |  Não                |  Texto                  |  Até 60 caracteres
    numeracao_volumes           |  nVol           |  Não                |  Texto                  |  Até 60 caracteres                  |  Numeração dos volumes transportados
    peso_liquido                |  peslL          |  Não                |  Decimal                |  Até 12 dígitos, 3 casas decimais   |  Peso líquido em quilogramas (kG).
    peso_bruto                  |  pesoB          |  Não                |  Decimal                |  Até 12 dígitos, 3 casas decimais   |  Peso bruto em quilogramas (kG).

### lacres (XML: lacres)  

Cada volume transportador pode conter lacres, sendo até 5.000 por volume.  

### Item da coleção (array) de lacres  

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    Número do lacre             |  nLacre         |  Sim                |  Texto                  |  Até 60 caracteres                 |

## cobranca (XML: infNFe)

Informações opcionais de cobrança. Seus atributos são:  

### fatura (XML: fat)

Subgrupo de informações relacionadas aos dados da fatura. Possui somente uma ocorrência. Apresenta os seguintes atributos:

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |   Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    numero_fatura               |  nFat           |  Não                |  Texto e/ou número      |  Até 60 caracteres                 |  Número da fatura.
    valor_original              |  vOrig          |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |  Valor original (bruto) da fatura.  
    valor_desconto              |  vDesc          |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |  Valor aplicado de desconto.  
    valor_liquido               |  vLiq           |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |  Valor líquido da fatura.  

### duplicata (XML: dup)  

Subgrupo de informações relacionadas às duplicatas (parcelas da compra). Pode conter até 200 ocorrências e possui os seguintes atributos:  

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    numero                      |  nDup           |  Não                |  Texto e/ou número      |  Até 60 caracteres                 |  Número da duplicata.  
    data_vencimento             |  dVenc          |  Não                |  Data                   |  AAAA-MM-DD                        |  Data de vencimento da duplicata  
    valor                       |  vDup           |  Sim                |  Decimal                |  13 dígitos, 2 casas decimais      |  Valor da duplicata.  

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

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    codigo_uf_emitente          |  cUF            |  Sim                |  Numérico               |  2 dígitos                         |  Código de acordo com tabela IBGE
    ano_mes_emissao             |  AAMM           |  Sim                |  Numérico               |  ano (AA) e mês (MM) de emissão da NF
    modelo_documento            |  mod            |  Sim                |  Numérico               |  2 dígitos                         |  01 = modelo 01
    numero_documento            |  nNF            |  Sim                |  Numérico               |  Até 9 dígitos                     |
    serie_documento             |  serie          |  Sim                |  Numérico               |  Até 3 dígitos                     |  Informar zero se não utilizada a série do documento fiscal.
    cnpj_emitente               |  CNPJ           |  Sim                |  Numérico               |  14 dígitos

### tipo_documento = “Cupom”

Além dos campos similares à nota fiscal física, o cupom fiscal tem os seguintes atributos:  

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    numero_ecf                  |  nECF           |  Sim                |  Numérico               |  3 dígitos                         |  Número de ordem sequencial de ECF.
    numero_coo                  |  nCOO           |  Sim                |  Numérico               |  6 dígitos                         |  Número do Contador de Ordem de Operação (COO).

## retencoes (XML: retTrib)

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    valor_retido_pis            |  vRetPIS        |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |
    valor_retido_cofins         |  vRetCOFINS     |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |
    valor_retido_csll           |  vRetCSLL       |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |
    valor_base_calculo_irrf     |  vBCIRRF        |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |
    valor_irrf                  |  vIRRF          |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      | 
    base_calculo_retencao_previdencia|vBCRetPrev  |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |
    valor_retencao_previdencia  |  vRetPrev       |  Não                |  Decimal                |  13 dígitos, 2 casas decimais      |

## exporta (XML: exporta)  

Informações de comércio exterior.

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    uf_embarque                 |  UFSaidaPais    |  Sim                |  Texto                  |  2 caracteres                      |  Sigla da UF de Embarque ou de transposição de fronteira. 
    local_embarque              |  xLocExporta    |  Sim                |  Texto                  |  Até 60 caracteres                 |  Descrição do Local de Embarque ou de transposição de fronteira.
    local_despacho              |  xLocDespacho   |  Sim                |  Texto                  |  Até 60 caracteres                 |  Descrição do local de despacho. 

## informacoes_adicionais (XML: infAdic)  

Grupo de informações adicionais da NF-e. Seus atributos são:  

    Campo                       |  Campo no XML   |  Obrigatório        |     Tipo                |    Formato e tamanho               |  Observações
--------------------------------|-----------------|---------------------|-------------------------|------------------------------------|-----------------------------------------------------------
    informacoes_contribuinte    |  infCpl         |  Não                |  Texto                  |  Até 2.000 caracteres              |  Informações complementares de interesse do Contribuinte.
    informacoes_fisco           |    infAdFisco   |  Não                |  Texto                  |  Até 2.000 caracteres              |  Informações adicionais de interesse do Fisco.  


