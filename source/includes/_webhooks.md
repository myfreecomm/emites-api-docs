# Webhooks

Os Webhooks são notificações assíncronas enviadas para todos os eventos solicitados ao Emites.  
Sendo assim, ao receber um evento, o sistema envia uma requisição HTTP para a url configurada no Emites com as informações relacionadas ao evento.
Os webhooks também são conhecidos como Callbacks ou Reverse API .  

Para adicionar uma nova url, acesse a interface do Emites, clique no ícone do menu, depois em conta, no final da página terá um botão para a adição do novo webhook.  

Após adicionado, a cada requisição efetuada ao Emites, será retornada uma notificação sobre o estado do evento.  

Por exemplo, a cada nota emitida será disparado o payload:  

```
{
    "object_type":"NFe",
    "object_id":2646,
    "organization_id":13,
    "event":"succeeded"
}
```
