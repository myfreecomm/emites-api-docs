# Tipos de emissão

## Processamento Síncrono

O processamento síncrono corresponde a entrega da resposta do processamento da NF-e/NFC-e,
sem a geração de um recibo de lote para consulta futura. Portanto, obtendo o status do documento na mesma conexão.

<aside class="notice">
  Só é possível processar <b>1 documento</b> por requisição utilizando esse modo.
</aside>

Para utilizar esse tipo de emissão, utilize as instruções contidas nas seções [Emissão de NF-e](#emiss-o-de-nf-e) ou [Emissão de NCF-e](#emiss-o-de-nfc-e).

A resposta de forma síncrona é critério da SEFAZ de cada UF. E caso não esteja disponível, a requisição retornará um erro.

Ex:

```
{
  "errors": [
    {
      "uf": [
        "uf 35 não habilitada para o modo síncrono. Utilize o endpoint para emissão em lote (/api/v1/organizations/1/nfe_batch)."
      ]
    }
  ]
}
```

## Processamento Assíncrono

O processamento assíncrono corresponde ao envio de um lote de NF-e/NFC-e, e o recebimento de um Recibo de Lote da SEFAZ. Em posse desse recibo, o Emites realizará uma consulta dentro de alguns segundos em uma nova conexão para obter o status de cada documento do lote.

<aside class="notice">
  É possível processar de <b>1 a 50 documentos</b> por requisição utilizando esse modo.
</aside>

Para utilizar esse tipo de emissão, utilize as instruções contidas nas seções [Emissão em lote de NF-e](#emiss-o-em-lote-de-nf-e) ou [Emissão em lote de NFC-e](#emiss-o-em-lote-de-nfc-e).

A resposta de forma assíncrona está disponível para todas as UF's.

## Processamento Híbrido

Nesse tipo de emissão, fica a critério do Emites definir qual o modo de processamento será utilizado na conexão com a SEFAZ, baseado na melhor opção possível.

O modo síncrono será utilizado:

  - Se a SEFAZ da UF de origem disponibilizar esse serviço.
  - Se o lote enviado conter apenas um documento.

Caso contrário, o modo assíncrono será utilizado na conexão com a SEFAZ.

Para utilizar esse tipo de emissão, utilize as instruções contidas nas seções [Emissão Híbrida de NF-e](#emiss-o-h-brida-de-nf-e) ou [Emissão Híbrida de NFC-e](#emiss-o-h-brida-de-nfc-e).
