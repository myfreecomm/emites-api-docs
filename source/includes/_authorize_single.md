# Autorização de XML

## Autorização de XML de NF-e

Para autorizar o XML de uma NF-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe/authorize</h6>
    </div>
</div>

<aside class="warning">
  Todos os campos de texto da NF-e não aceitam caracteres acentuados como, por exemplo "á", "é", "â", "ã" etc. Também não aceitam "ç".
</aside>

Os campos utilizados para esse tipo de emissão são os mesmos praticados na Emissão de NF-e, com exceção do **xml_assinado**.

O valor desse campo deve conter o XML da NF-e assinado utilizando o método de codificação **Base64**.

<aside class="notice">
    <b>Atenção</b>: É importante que os campos <b>nfe_numero</b> e <b>serie</b> contidos em dados_gerais sejam os mesmos que foram utilizados para compôr o XML enviado no <b>xml_assinado</b>. Caso contrário, as respostas obtidas na SEFAZ não serão persistidos na NF-e.
</aside>

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfe/authorize \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json' \
  -d '{
    "nfe": {
      "contingencia": false,
        "xml_assinado": "PGVudmlORmUgeG1sbnM9Imh0dHA6Ly93d3cucG9ydGFsZmlzY2FsLmluZi5ici9uZmUiIHZlcnNhbz0iNC4wMCI+PGlkTG90ZT4xMDA8L2lkTG90ZT48aW5kU2luYz4xPC9pbmRTaW5jPjxORmU+PGluZk5GZSBJZD0iTkZlMzUxOTAyMjI3Njk1MzAwMDAxMzE1NTAwMDAwMDAwMDEwMDE1NTgyNzc2MDMiIHZlcnNhbz0iNC4wMCI+PGlkZT48Y1VGPjM1PC9jVUY+PGNORj41NTgyNzc2MDwvY05GPjxuYXRPcD5WZW5kYSBtZXJjLiBhZHEuIHJlYy4gdGVyYy4gZWZldC4gZm9yYSBlc3RhYi48L25hdE9wPjxtb2Q+NTU8L21vZD48c2VyaWU+PC9zZXJpZT48bk5GPjEwMDwvbk5GPjxkaEVtaT4yMDE5LTAyLTE1VDA5OjU5OjE3LTAyOjAwPC9kaEVtaT48ZGhTYWlFbnQ+MjAxOC0wOS0yOFQxNzowNzozNS0wMzowMDwvZGhTYWlFbnQ+PHRwTkY+MTwvdHBORj48aWREZXN0PjE8L2lkRGVzdD48Y011bkZHPjM1MjU5MDQ8L2NNdW5GRz48dHBJbXA+MTwvdHBJbXA+PHRwRW1pcz4xPC90cEVtaXM+PGNEVj4zPC9jRFY+PHRwQW1iPjI8L3RwQW1iPjxmaW5ORmU+MTwvZmluTkZlPjxpbmRGaW5hbD4wPC9pbmRGaW5hbD48aW5kUHJlcz45PC9pbmRQcmVzPjxwcm9jRW1pPjA8L3Byb2NFbWk+PHZlclByb2M+NC4wMDwvdmVyUHJvYz48L2lkZT48ZW1pdD48Q05QSj4yMjc2OTUzMDAwMDEzMTwvQ05QSj48eE5vbWU+T3JnYW5pemFjYW8gVGVzdGUgTkZDZS9ERjwveE5vbWU+PHhGYW50Pk9yZ2FuaXphY2FvIFRlc3RlIE5GQ2UgLyBERjwveEZhbnQ+PGVuZGVyRW1pdD48eExncj5TQVVTIFF1YWRyYSA0IExvdGUgOS8xMDwveExncj48bnJvPjA0PC9ucm8+PHhDcGw+Q29tcGxlbWVudG88L3hDcGw+PHhCYWlycm8+QXNhIFN1bDwveEJhaXJybz48Y011bj41MzAwMTA4PC9jTXVuPjx4TXVuPkJyYXNpbGlhPC94TXVuPjxVRj5ERjwvVUY+PENFUD43MDA3MDkzODwvQ0VQPjxjUGFpcz4xMDU4PC9jUGFpcz48eFBhaXM+QnJhc2lsPC94UGFpcz48Zm9uZT4xNTM1MzEyMTY0PC9mb25lPjwvZW5kZXJFbWl0PjxJRT43NzI3MzM3MDAxMjA8L0lFPjxDUlQ+MzwvQ1JUPjwvZW1pdD48ZGVzdD48Q05QSj40NjcyODc1NDAwMDE2MzwvQ05QSj48eE5vbWU+TkYtRSBFTUlUSURBIEVNIEFNQklFTlRFIERFIEhPTU9MT0dBQ0FPIC0gU0VNIFZBTE9SIEZJU0NBTDwveE5vbWU+PGVuZGVyRGVzdD48eExncj5BViBHVUlMSEVSTUUgUE9SQ0FSSTwveExncj48bnJvPlMgTjwvbnJvPjx4QmFpcnJvPk1FREVJUk9TPC94QmFpcnJvPjxjTXVuPjM1MjU5MDQ8L2NNdW4+PHhNdW4+SlVORElBSTwveE11bj48VUY+U1A8L1VGPjxDRVA+MTMyMTIyNTU8L0NFUD48Y1BhaXM+MTA1ODwvY1BhaXM+PHhQYWlzPkJSQVNJTDwveFBhaXM+PGZvbmU+OTk5OTk5OTk8L2ZvbmU+PC9lbmRlckRlc3Q+PGluZElFRGVzdD4xPC9pbmRJRURlc3Q+PElFPjQwNzA1NjIyODExMzwvSUU+PGVtYWlsPnRlc3RlQG5leGFhcy5jb20uYnI8L2VtYWlsPjwvZGVzdD48ZGV0IG5JdGVtPSIxIj48cHJvZD48Y1Byb2Q+MTIzNDU2PC9jUHJvZD48Y0VBTj5TRU0gR1RJTjwvY0VBTj48eFByb2Q+TklUUk9HRU5JTyBDSUwgNTBMIDEwTTM8L3hQcm9kPjxOQ00+MjgwNDMwMDA8L05DTT48Q0ZPUD41MTA0PC9DRk9QPjx1Q29tPk0zPC91Q29tPjxxQ29tPjY8L3FDb20+PHZVbkNvbT4xNi40OTQ4NTwvdlVuQ29tPjx2UHJvZD45OC45NzwvdlByb2Q+PGNFQU5UcmliPlNFTSBHVElOPC9jRUFOVHJpYj48dVRyaWI+TTM8L3VUcmliPjxxVHJpYj42PC9xVHJpYj48dlVuVHJpYj4xNi40OTQ4NTwvdlVuVHJpYj48aW5kVG90PjE8L2luZFRvdD48eFBlZD5TMDEwMDI0OTEzNDwveFBlZD48bkl0ZW1QZWQ+MTwvbkl0ZW1QZWQ+PC9wcm9kPjxpbXBvc3RvPjx2VG90VHJpYj4yNjkuNjQ8L3ZUb3RUcmliPjxJQ01TPjxJQ01TMDA+PG9yaWc+Mzwvb3JpZz48Q1NUPjAwPC9DU1Q+PG1vZEJDPjM8L21vZEJDPjx2QkM+OTg5LjY5PC92QkM+PHBJQ01TPjE4LjAwMDA8L3BJQ01TPjx2SUNNUz4xNzguMTQ8L3ZJQ01TPjwvSUNNUzAwPjwvSUNNUz48SVBJPjxjU2Vsbz4wPC9jU2Vsbz48cVNlbG8+MDwvcVNlbG8+PGNFbnE+OTk5PC9jRW5xPjxJUElOVD48Q1NUPjAxPC9DU1Q+PC9JUElOVD48L0lQST48UElTPjxQSVNBbGlxPjxDU1Q+MDE8L0NTVD48dkJDPjk4OS42OTwvdkJDPjxwUElTPjEuNjUwMDwvcFBJUz48dlBJUz4xNi4zMDwvdlBJUz48L1BJU0FsaXE+PC9QSVM+PENPRklOUz48Q09GSU5TQWxpcT48Q1NUPjAxPC9DU1Q+PHZCQz45ODkuNjk8L3ZCQz48cENPRklOUz43LjYwMDA8L3BDT0ZJTlM+PHZDT0ZJTlM+NzUuMjA8L3ZDT0ZJTlM+PC9DT0ZJTlNBbGlxPjwvQ09GSU5TPjwvaW1wb3N0bz48L2RldD48dG90YWw+PElDTVNUb3Q+PHZCQz45ODkuNjk8L3ZCQz48dklDTVM+MTc4LjE0PC92SUNNUz48dklDTVNEZXNvbj4wLjAwPC92SUNNU0Rlc29uPjx2RkNQVUZEZXN0PjAuMDA8L3ZGQ1BVRkRlc3Q+PHZJQ01TVUZEZXN0PjAuMDA8L3ZJQ01TVUZEZXN0Pjx2SUNNU1VGUmVtZXQ+MC4wMDwvdklDTVNVRlJlbWV0Pjx2RkNQPjAuMDA8L3ZGQ1A+PHZCQ1NUPjAuMDA8L3ZCQ1NUPjx2U1Q+MC4wMDwvdlNUPjx2RkNQU1Q+MC4wMDwvdkZDUFNUPjx2RkNQU1RSZXQ+MC4wMDwvdkZDUFNUUmV0Pjx2UHJvZD45OC45NzwvdlByb2Q+PHZGcmV0ZT4wLjAwPC92RnJldGU+PHZTZWc+MC4wMDwvdlNlZz48dkRlc2M+MC4wMDwvdkRlc2M+PHZJST4wLjAwPC92SUk+PHZJUEk+MC4wMDwvdklQST48dklQSURldm9sPjAuMDA8L3ZJUElEZXZvbD48dlBJUz4xNi4zMDwvdlBJUz48dkNPRklOUz43NS4yMDwvdkNPRklOUz48dk91dHJvPjAuMDA8L3ZPdXRybz48dk5GPjk4Ljk3PC92TkY+PHZUb3RUcmliPjI2OS42NDwvdlRvdFRyaWI+PC9JQ01TVG90PjwvdG90YWw+PHRyYW5zcD48bW9kRnJldGU+OTwvbW9kRnJldGU+PHZvbD48cVZvbD4xPC9xVm9sPjxlc3A+Q2lsaW5kcm88L2VzcD48bWFyY2E+MDwvbWFyY2E+PG5Wb2w+MDwvblZvbD48cGVzb0w+NjYuNzgwPC9wZXNvTD48cGVzb0I+NDUwLjc4MDwvcGVzb0I+PC92b2w+PC90cmFuc3A+PHBhZz48ZGV0UGFnPjx0UGFnPjAxPC90UGFnPjx2UGFnPjUwLjAwPC92UGFnPjwvZGV0UGFnPjxkZXRQYWc+PHRQYWc+MDM8L3RQYWc+PHZQYWc+OC45NzwvdlBhZz48L2RldFBhZz48ZGV0UGFnPjx0UGFnPjAzPC90UGFnPjx2UGFnPjQwLjAwPC92UGFnPjxjYXJkPjx0cEludGVncmE+MTwvdHBJbnRlZ3JhPjxDTlBKPjk5OTk5OTk5OTk5OTk5PC9DTlBKPjx0QmFuZD4wMjwvdEJhbmQ+PGNBdXQ+OTk5OTk5OTk5OTk5OTk5OTk5OTk8L2NBdXQ+PC9jYXJkPjwvZGV0UGFnPjwvcGFnPjxpbmZBZGljPjxpbmZBZEZpc2NvPkNsaWVudGU6IDExMi4gUmVtZXNzYTogMDAwMDYxMDc0LTAxMjM8L2luZkFkRmlzY28+PC9pbmZBZGljPjwvaW5mTkZlPjxTaWduYXR1cmUgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvMDkveG1sZHNpZyMiPjxTaWduZWRJbmZvPjxDYW5vbmljYWxpemF0aW9uTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvVFIvMjAwMS9SRUMteG1sLWMxNG4tMjAwMTAzMTUiPjwvQ2Fub25pY2FsaXphdGlvbk1ldGhvZD48U2lnbmF0dXJlTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxkc2lnI3JzYS1zaGExIj48L1NpZ25hdHVyZU1ldGhvZD48UmVmZXJlbmNlIFVSST0iI05GZTM1MTkwMjIyNzY5NTMwMDAwMTMxNTUwMDAwMDAwMDAxMDAxNTU4Mjc3NjAzIj48VHJhbnNmb3Jtcz48VHJhbnNmb3JtIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxkc2lnI2VudmVsb3BlZC1zaWduYXR1cmUiPjwvVHJhbnNmb3JtPjxUcmFuc2Zvcm0gQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy14bWwtYzE0bi0yMDAxMDMxNSI+PC9UcmFuc2Zvcm0+PC9UcmFuc2Zvcm1zPjxEaWdlc3RNZXRob2QgQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwLzA5L3htbGRzaWcjc2hhMSI+PC9EaWdlc3RNZXRob2Q+PERpZ2VzdFZhbHVlPkZiY1RiWkVwZG9KYm95bFFKWHNoZ3k2QlZucz08L0RpZ2VzdFZhbHVlPjwvUmVmZXJlbmNlPjwvU2lnbmVkSW5mbz48U2lnbmF0dXJlVmFsdWU+RklHTmVmejl6TnJuOG95Zm5QSGdwVlo2d20yMkVUM3NsZUxGdHJhL2hCKzIva2JJTUI0RjNqcnNlUkhHaSt2TURiWTF3dUtKSytxUVJSUXpRVnl5QlhER21VNnF5MUs3bklWOXd2cGw5WExaTDhaMWl4dS9SVW1mQWdxK1RHUExNQ0lWa1RUWkdMb2JZOUN0WFczOGJGN29qR2t1MVZTK2R2b1pwSkdiTVdoOFQ2RGxyYjZYbExweERPTXlhVjlOeHVqVnNHS0l5RnZpZUwvNG9DdGhiZVk1UFhUOCtHNzEyWDZpVnl6Vi9QYVFac2hhUnNadmcxWEg5ZUhlWTlhOE1ZRGt3dmcvYVQwQkJaU3ZnajNHbUM4RzNJV1FHUUNrN2QxSkhybVVLaUxNYVIwb2xVZit3SUJOempVZWllM0dWakRMZGk1ZEpDVHk0eFBsTGJ5d2NBPT08L1NpZ25hdHVyZVZhbHVlPjxLZXlJbmZvPjxYNTA5RGF0YT48WDUwOUNlcnRpZmljYXRlPk1JSUhyRENDQlpTZ0F3SUJBZ0lJRWQ0WUJ3UllwZkF3RFFZSktvWklodmNOQVFFTEJRQXdnWWt4Q3pBSkJnTlZCQVlUQWtKU01STXdFUVlEVlFRS0V3cEpRMUF0UW5KaGMybHNNVFF3TWdZRFZRUUxFeXRCZFhSdmNtbGtZV1JsSUVObGNuUnBabWxqWVdSdmNtRWdVbUZwZWlCQ2NtRnphV3hsYVhKaElIWXlNUkl3RUFZRFZRUUxFd2xCUXlCVFQweFZWRWt4R3pBWkJnTlZCQU1URWtGRElGTlBURlZVU1NCTmRXeDBhWEJzWVRBZUZ3MHhPREEzTURReU1UVTJOVFphRncweE9UQTNNRFF4T0RFek1EQmFNSUhWTVFzd0NRWURWUVFHRXdKQ1VqRVRNQkVHQTFVRUNoTUtTVU5RTFVKeVlYTnBiREUwTURJR0ExVUVDeE1yUVhWMGIzSnBaR0ZrWlNCRFpYSjBhV1pwWTJGa2IzSmhJRkpoYVhvZ1FuSmhjMmxzWldseVlTQjJNakVTTUJBR0ExVUVDeE1KUVVNZ1UwOU1WVlJKTVJzd0dRWURWUVFMRXhKQlF5QlRUMHhWVkVrZ1RYVnNkR2x3YkdFeEdqQVlCZ05WQkFzVEVVTmxjblJwWm1sallXUnZJRkJLSUVFeE1TNHdMQVlEVlFRREV5VlFSRlpGVGtRZ1ZFVkRUazlNVDBkSlFTQk1WRVJCT2pJeU56WTVOVE13TURBd01UTXhNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUZBQU9DQVE4QU1JSUJDZ0tDQVFFQTBnWDgvbEV0bFFNZ1Fnc3QwZkxNQzV4R3UwbGZ1L0dZRWk4M0oyVGtWaVUvWjdpL0QyN1ZhYTRwcXZwZElqVm4zTytiZzdVdFBPSVBMNHFMTDE3dnJ2SWI1V0FtNzJIUDgvaFRoRkZ1VjV3NjZITmgwNEd0TEF1NDhRempaVk4yU2FYdElWeldSczM2YnZFNUdSRzE4bHdqOWV6NlRiZjhaN3p6d2d2cWRWaC9nNWI5NU9vaVRTMkhmV1Z1Ry9QY2xEK1hjZHZtcklsWDlWZVhXaWxrZjAwd2l2ajdjMkJmMmZZY1RWTUg5OUwyaXVDcHhSV0lEL3JhTWlpb1o1VkI5cko3THF1aVIvdFRDWVBheWVMMjhHZGtBTTRwQUg0WVJqZFF1NjBmS0hDMmhKTnhFSWYrUGhZeTBYRFQybENsa2M1elFFdVd2ZjJyK2dtc1oyQ1Ewd0lEQVFBQm80SUN5RENDQXNRd1ZBWUlLd1lCQlFVSEFRRUVTREJHTUVRR0NDc0dBUVVGQnpBQ2hqaG9kSFJ3T2k4dlkyTmtMbUZqYzI5c2RYUnBMbU52YlM1aWNpOXNZM0l2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExuQTNZakFkQmdOVkhRNEVGZ1FVVE1oa2lReFBIY1hhZERSUzFIRjdNV1VJckRvd0NRWURWUjBUQkFJd0FEQWZCZ05WSFNNRUdEQVdnQlExcmpFVTlsN1NlazlZL2pTb0dtZVhDc1NiQnpCZUJnTlZIU0FFVnpCVk1GTUdCbUJNQVFJQkpqQkpNRWNHQ0NzR0FRVUZCd0lCRmp0b2RIUndjem92TDJOalpDNWhZM052YkhWMGFTNWpiMjB1WW5JdlpHOWpjeTlrY0dNdFlXTXRjMjlzZFhScExXMTFiSFJwY0d4aExuQmtaakNCM2dZRFZSMGZCSUhXTUlIVE1ENmdQS0E2aGpob2RIUndPaTh2WTJOa0xtRmpjMjlzZFhScExtTnZiUzVpY2k5c1kzSXZZV010YzI5c2RYUnBMVzExYkhScGNHeGhMWFl4TG1OeWJEQS9vRDJnTzRZNWFIUjBjRG92TDJOalpESXVZV056YjJ4MWRHa3VZMjl0TG1KeUwyeGpjaTloWXkxemIyeDFkR2t0YlhWc2RHbHdiR0V0ZGpFdVkzSnNNRkNnVHFCTWhrcG9kSFJ3T2k4dmNtVndiM05wZEc5eWFXOHVhV053WW5KaGMybHNMbWR2ZGk1aWNpOXNZM0l2UVVOVFQweFZWRWt2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExtTnliREFPQmdOVkhROEJBZjhFQkFNQ0JlQXdIUVlEVlIwbEJCWXdGQVlJS3dZQkJRVUhBd0lHQ0NzR0FRVUZCd01FTUlHd0JnTlZIUkVFZ2Fnd2dhV0JFMkp5ZFc1dlFIQmtkbVZ1WkM1amIyMHVZbktnSUFZRllFd0JBd0tnRnhNVlFsSlZUazhnVmtWTVQxTlBJRVpGVWxKRlNWSkJvQmtHQldCTUFRTURvQkFURGpJeU56WTVOVE13TURBd01UTXhvRGdHQldCTUFRTUVvQzhUTFRJek1EZ3hPVGcxTURBMk5ESXlNakl4Tnpjd01EQXdNREF3TURBd01EQXdNREF3TURBd01EQXdNREF3TUtBWEJnVmdUQUVEQjZBT0V3d3dNREF3TURBd01EQXdNREF3RFFZSktvWklodmNOQVFFTEJRQURnZ0lCQUR4ek12YWpTbFVRMkd4cko5SU96SXB6V0V2cDhUb003MXpqclhCK2R3VnMxRDVjUlFBOGh2bzAxeHdaNDVzNlBNbW1qSng4WElSUVdCM2RMVi82bUtwTkdDY1BXN2d1bit4M1ZMa1JMVG9mUW1WVnJxaldUeitZdW14ejk0eHdSMmtKR2g2dTNueHY5MmhUaVhkKzd2UmZNUGNzQU8wVnR2aFg3eHF0Y2JPdVVyZmU4UW5FRlE2WmI2aE1aUVBtSVE1K1dWY2R5TzdVZytZR1NZeWZ2UHhySWpBQk5XcGpuTUZJUEZwcTgvalhlbFhzVXlvbThTc3hOdGJ4OThLc0dLd3Q1ZkRPb2NvdnFGNmpKOHpzak1uL2pZV2lhTkhRMnBLbzNFbWl0YW82b2JCT1hGdU5xV2M1VXo4V01tK2lUTXlKbjh4b3R6cmhrYTZjNVl1SjBieEovcFBsS0pBT2tEVFZZb1RBMTkwM1gvMG51blQyZDdJMVYzRDRNYmxvMWxDV1VnakZuVENtdlJGZmhoQzh1TXdYc2M5UkprVm1UeCs3cU9oWXpDRkVKTnFLb0FvZUJJTHZOWXltRTUxaG1tbmFhTEw0QkJuUmhHZllIRUhOWGRrOU81MlBNOWVXSHZ5c0xlWEpMRjBXVHh0L0V5QThxbGtZM2JLN1Z5VllWM2tOVWRPeHJ4NTA3VjZRSVVTYTdXc05janprM3JBN0U1dklRbkNLR2ZlbVJoOEFSc1dIaGltVG4yYkQ2bGhXYlBMN0ZkWWo4eVlFMCt0T2V3OHhQVXQ1Y2pDekJhZDBuZXFvNkkzVTUyaEV4bWhUVUNMcVk1RG5PeGhWRHNtWS9pUUtNalBXR3lETUtkTGJCbFozelYyeE5EMktlcVlVblRxYlduNGk3amppPC9YNTA5Q2VydGlmaWNhdGU+PC9YNTA5RGF0YT48L0tleUluZm8+PC9TaWduYXR1cmU+PC9ORmU+PC9lbnZpTkZlPg==",
      "cliente": {
        "cpf_cnpj": "46728754000163",
        "email": "teste@nexaas.com.br",
        "indicador_inscricao_estadual": 1,
        "inscricao_estadual": "407056228113",
        "inscricao_municipal": "",
        "inscricao_suframa": "",
        "nome": "NF-E EMITIDA EM AMBIENTE DE HOMOLOGACAO - SEM VALOR FISCAL",
        "pessoa_fisica_juridica": "company",
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
          "telefone": "99999999",
          "uf": "SP"
        }
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
        "data_saida_entrada": "2018-09-28T17:07:35-03:00",
        "destino_operacao": "1",
        "finalidade_nfe": "1",
        "indicador_consumidor_final": "0",
        "indicador_presenca": "9",
        "natureza_operacao": "Venda merc. adq. rec. terc. efet. fora estab.",
        "tipo_operacao": "1",
        "uf": 35,
        "nfe_numero": 101,
        "serie": 1
      },
      "forma_de_pagamento": [
        {
          "tipo_de_pagamento": "01",
          "valor_do_pagamento": 50
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
          "valor_do_pagamento": 40
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
          "outras_despesas": 0,
          "producao_escala": "S",
          "quantidade_comercial": 6,
          "quantidade_tributaria": 6,
          "unidade_comercial": "M3",
          "unidade_tributaria": "M3",
          "valor_desconto": 0,
          "valor_frete": 0,
          "valor_seguro": 0,
          "valor_total_produto": "98.97",
          "valor_unitario_comercial": 16.49485,
          "valor_unitario_tributario": 16.49485,
          "tributacao": {
            "valor_aproximado_total": 269.64,
            "cofins": {
              "aliquota_cofins": "7.60",
              "aliquota_cofins_reais": 0,
              "aliquota_cofins_st_reais": 0,
              "aliquota_st": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_st": 0,
              "valor_cofins": 75.2,
              "valor_cofins_st": 0
            },
            "icms": {
              "aliquota_consumidor_final": 0,
              "aliquota_fcp": 0,
              "aliquota_fcp_st": 0,
              "aliquota_fcp_st_retido": 0,
              "aliquota_icms": "18.00",
              "aliquota_icms_simples_nacional": 0,
              "aliquota_icms_st": 0,
              "aliquota_interestadual": 0,
              "aliquota_interna_interestadual": 0,
              "base_icmsst_retido": 0,
              "codigo_origem_produto": 3,
              "credito_icms_simples_nacional": 0,
              "modalidade_base_calculo": 3,
              "modalidade_base_calculo_st": "3",
              "motivo_desoneracao": "",
              "perc_diferimento": 0,
              "perc_fcp_interestadual": 0,
              "perc_mva_icms_st": 0,
              "perc_provisorio_interestadual": 0,
              "perc_reducao_base_calculo": 0,
              "perc_reducao_base_calculo_st": 0,
              "situacao_simples_nacional": 0,
              "situacao_tributaria": "00",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_fcp": 0,
              "valor_base_calculo_fcp_st": 0,
              "valor_base_calculo_fcp_st_retido": 0,
              "valor_base_calculo_st": 0,
              "valor_base_calculo_uf_dest": 0,
              "valor_fcp": 0,
              "valor_fcp_interestadual": 0,
              "valor_fcp_st": 0,
              "valor_fcp_st_retido": 0,
              "valor_icms": 178.14,
              "valor_icms_desonerado": 0,
              "valor_icms_diferido": 0,
              "valor_icms_operacao": 0,
              "valor_icms_st": 0,
              "valor_icmsst_retido": 0,
              "valor_uf_destinatario_interestadual": 0,
              "valor_uf_rementente": 0,
              "valor_uf_remetente_interestadual": 0
            },
            "importacao": {
              "base_calculo_importacao": "",
              "valor_despesas_aduaneiras": "",
              "valor_imposto_importacao": "",
              "valor_iof": ""
            },
            "ipi": {
              "aliquota_ipi": "0.00",
              "cnpj_produtor": "",
              "codigo_enquadramento": 999,
              "codigo_selo_controle": 0,
              "quantidade_selo_controle": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": "989.69",
              "valor_ipi": "0.00",
              "valor_unidade": ""
            },
            "pis": {
              "aliquota_pis": 1.65,
              "aliquota_pis_reais": 0,
              "aliquota_pis_reais_st": 0,
              "aliquota_st": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_st": 0,
              "valor_pis": 16.3,
              "valor_pis_st": 0
            }
          },
          "declaracao_importacao": [
            {
              "cnpj": "",
              "codigo_exportador": "",
              "data_desembaraco": "",
              "data_importacao": "",
              "documento_importacao": "",
              "forma_importacao": "",
              "local_desembaraco": "",
              "uf_adquirente": "",
              "uf_desembaraco": "",
              "valor_afrmm": "",
              "via_transporte": "",
              "adicoes": [
                {
                  "codigo_fabricante": "",
                  "numero_adicao": "",
                  "numero_drawback": "",
                  "numero_sequencial": "",
                  "valor_desconto": ""
                }
              ]
            }
          ]
        }
      ],
      "retencao_tributos": {
        "base_calculo_retencao_previdencia": 0,
        "valor_base_calculo_irrf": 0,
        "valor_irrf": 0,
        "valor_retencao_previdencia": 0,
        "valor_retido_cofins": 0,
        "valor_retido_csll": 0,
        "valor_retido_pis": 0
      },
      "transporte": {
        "codigo_modalidade": 9,
        "retencao_icms": {
          "aliquota_retencao": 0,
          "cfop": "",
          "codigo_municipio": "",
          "uf": "",
          "valor_base_calculo": 0,
          "valor_retido": 0,
          "valor_servico": 0
        },
        "transportadora": {
          "cnpj_cpf": "",
          "endereco_completo": "",
          "inscricao_estadual": "",
          "municipio": "",
          "razao_social": "",
          "uf": ""
        },
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
  }'


EXEMPLO DE RESPOSTA

{
  "nfe": {
    "id": 10990,
    "status": "processing"
  }
}
```

## Autorização de XML de NFC-e

Para autorizar o XML de uma NFC-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfce/authorize</h6>
    </div>
</div>

<aside class="warning">
  Todos os campos de texto da NFC-e não aceitam caracteres acentuados como, por exemplo "á", "é", "â", "ã" etc. Também não aceitam "ç".
</aside>

Os campos utilizados para esse tipo de emissão são os mesmos praticados na Emissão de NFC-e, com exceção do **xml_assinado**.

O valor desse campo deve conter o XML da NFC-e assinado utilizando o método de codificação **Base64**.

<aside class="notice">
    <b>Atenção</b>: É importante que os campos <b>nfe_numero</b> e <b>serie</b> contidos em dados_gerais sejam os mesmos que foram utilizados para compôr o XML enviado no <b>xml_assinado</b>. Caso contrário, as respostas obtidas na SEFAZ não serão persistidos na NFC-e.
</aside>

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfce/authorize \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json' \
  -d '{
    "nfce": {
      "xml_assinado": "PGVudmlORmUgeG1sbnM9Imh0dHA6Ly93d3cucG9ydGFsZmlzY2FsLmluZi5ici9uZmUiIHZlcnNhbz0iNC4wMCI+PGlkTG90ZT4xMDA8L2lkTG90ZT48aW5kU2luYz4xPC9pbmRTaW5jPjxORmU+PGluZk5GZSBJZD0iTkZlMzUxOTAyMjI3Njk1MzAwMDAxMzE1NTAwMDAwMDAwMDEwMDE1NTgyNzc2MDMiIHZlcnNhbz0iNC4wMCI+PGlkZT48Y1VGPjM1PC9jVUY+PGNORj41NTgyNzc2MDwvY05GPjxuYXRPcD5WZW5kYSBtZXJjLiBhZHEuIHJlYy4gdGVyYy4gZWZldC4gZm9yYSBlc3RhYi48L25hdE9wPjxtb2Q+NTU8L21vZD48c2VyaWU+PC9zZXJpZT48bk5GPjEwMDwvbk5GPjxkaEVtaT4yMDE5LTAyLTE1VDA5OjU5OjE3LTAyOjAwPC9kaEVtaT48ZGhTYWlFbnQ+MjAxOC0wOS0yOFQxNzowNzozNS0wMzowMDwvZGhTYWlFbnQ+PHRwTkY+MTwvdHBORj48aWREZXN0PjE8L2lkRGVzdD48Y011bkZHPjM1MjU5MDQ8L2NNdW5GRz48dHBJbXA+MTwvdHBJbXA+PHRwRW1pcz4xPC90cEVtaXM+PGNEVj4zPC9jRFY+PHRwQW1iPjI8L3RwQW1iPjxmaW5ORmU+MTwvZmluTkZlPjxpbmRGaW5hbD4wPC9pbmRGaW5hbD48aW5kUHJlcz45PC9pbmRQcmVzPjxwcm9jRW1pPjA8L3Byb2NFbWk+PHZlclByb2M+NC4wMDwvdmVyUHJvYz48L2lkZT48ZW1pdD48Q05QSj4yMjc2OTUzMDAwMDEzMTwvQ05QSj48eE5vbWU+T3JnYW5pemFjYW8gVGVzdGUgTkZDZS9ERjwveE5vbWU+PHhGYW50Pk9yZ2FuaXphY2FvIFRlc3RlIE5GQ2UgLyBERjwveEZhbnQ+PGVuZGVyRW1pdD48eExncj5TQVVTIFF1YWRyYSA0IExvdGUgOS8xMDwveExncj48bnJvPjA0PC9ucm8+PHhDcGw+Q29tcGxlbWVudG88L3hDcGw+PHhCYWlycm8+QXNhIFN1bDwveEJhaXJybz48Y011bj41MzAwMTA4PC9jTXVuPjx4TXVuPkJyYXNpbGlhPC94TXVuPjxVRj5ERjwvVUY+PENFUD43MDA3MDkzODwvQ0VQPjxjUGFpcz4xMDU4PC9jUGFpcz48eFBhaXM+QnJhc2lsPC94UGFpcz48Zm9uZT4xNTM1MzEyMTY0PC9mb25lPjwvZW5kZXJFbWl0PjxJRT43NzI3MzM3MDAxMjA8L0lFPjxDUlQ+MzwvQ1JUPjwvZW1pdD48ZGVzdD48Q05QSj40NjcyODc1NDAwMDE2MzwvQ05QSj48eE5vbWU+TkYtRSBFTUlUSURBIEVNIEFNQklFTlRFIERFIEhPTU9MT0dBQ0FPIC0gU0VNIFZBTE9SIEZJU0NBTDwveE5vbWU+PGVuZGVyRGVzdD48eExncj5BViBHVUlMSEVSTUUgUE9SQ0FSSTwveExncj48bnJvPlMgTjwvbnJvPjx4QmFpcnJvPk1FREVJUk9TPC94QmFpcnJvPjxjTXVuPjM1MjU5MDQ8L2NNdW4+PHhNdW4+SlVORElBSTwveE11bj48VUY+U1A8L1VGPjxDRVA+MTMyMTIyNTU8L0NFUD48Y1BhaXM+MTA1ODwvY1BhaXM+PHhQYWlzPkJSQVNJTDwveFBhaXM+PGZvbmU+OTk5OTk5OTk8L2ZvbmU+PC9lbmRlckRlc3Q+PGluZElFRGVzdD4xPC9pbmRJRURlc3Q+PElFPjQwNzA1NjIyODExMzwvSUU+PGVtYWlsPnRlc3RlQG5leGFhcy5jb20uYnI8L2VtYWlsPjwvZGVzdD48ZGV0IG5JdGVtPSIxIj48cHJvZD48Y1Byb2Q+MTIzNDU2PC9jUHJvZD48Y0VBTj5TRU0gR1RJTjwvY0VBTj48eFByb2Q+TklUUk9HRU5JTyBDSUwgNTBMIDEwTTM8L3hQcm9kPjxOQ00+MjgwNDMwMDA8L05DTT48Q0ZPUD41MTA0PC9DRk9QPjx1Q29tPk0zPC91Q29tPjxxQ29tPjY8L3FDb20+PHZVbkNvbT4xNi40OTQ4NTwvdlVuQ29tPjx2UHJvZD45OC45NzwvdlByb2Q+PGNFQU5UcmliPlNFTSBHVElOPC9jRUFOVHJpYj48dVRyaWI+TTM8L3VUcmliPjxxVHJpYj42PC9xVHJpYj48dlVuVHJpYj4xNi40OTQ4NTwvdlVuVHJpYj48aW5kVG90PjE8L2luZFRvdD48eFBlZD5TMDEwMDI0OTEzNDwveFBlZD48bkl0ZW1QZWQ+MTwvbkl0ZW1QZWQ+PC9wcm9kPjxpbXBvc3RvPjx2VG90VHJpYj4yNjkuNjQ8L3ZUb3RUcmliPjxJQ01TPjxJQ01TMDA+PG9yaWc+Mzwvb3JpZz48Q1NUPjAwPC9DU1Q+PG1vZEJDPjM8L21vZEJDPjx2QkM+OTg5LjY5PC92QkM+PHBJQ01TPjE4LjAwMDA8L3BJQ01TPjx2SUNNUz4xNzguMTQ8L3ZJQ01TPjwvSUNNUzAwPjwvSUNNUz48SVBJPjxjU2Vsbz4wPC9jU2Vsbz48cVNlbG8+MDwvcVNlbG8+PGNFbnE+OTk5PC9jRW5xPjxJUElOVD48Q1NUPjAxPC9DU1Q+PC9JUElOVD48L0lQST48UElTPjxQSVNBbGlxPjxDU1Q+MDE8L0NTVD48dkJDPjk4OS42OTwvdkJDPjxwUElTPjEuNjUwMDwvcFBJUz48dlBJUz4xNi4zMDwvdlBJUz48L1BJU0FsaXE+PC9QSVM+PENPRklOUz48Q09GSU5TQWxpcT48Q1NUPjAxPC9DU1Q+PHZCQz45ODkuNjk8L3ZCQz48cENPRklOUz43LjYwMDA8L3BDT0ZJTlM+PHZDT0ZJTlM+NzUuMjA8L3ZDT0ZJTlM+PC9DT0ZJTlNBbGlxPjwvQ09GSU5TPjwvaW1wb3N0bz48L2RldD48dG90YWw+PElDTVNUb3Q+PHZCQz45ODkuNjk8L3ZCQz48dklDTVM+MTc4LjE0PC92SUNNUz48dklDTVNEZXNvbj4wLjAwPC92SUNNU0Rlc29uPjx2RkNQVUZEZXN0PjAuMDA8L3ZGQ1BVRkRlc3Q+PHZJQ01TVUZEZXN0PjAuMDA8L3ZJQ01TVUZEZXN0Pjx2SUNNU1VGUmVtZXQ+MC4wMDwvdklDTVNVRlJlbWV0Pjx2RkNQPjAuMDA8L3ZGQ1A+PHZCQ1NUPjAuMDA8L3ZCQ1NUPjx2U1Q+MC4wMDwvdlNUPjx2RkNQU1Q+MC4wMDwvdkZDUFNUPjx2RkNQU1RSZXQ+MC4wMDwvdkZDUFNUUmV0Pjx2UHJvZD45OC45NzwvdlByb2Q+PHZGcmV0ZT4wLjAwPC92RnJldGU+PHZTZWc+MC4wMDwvdlNlZz48dkRlc2M+MC4wMDwvdkRlc2M+PHZJST4wLjAwPC92SUk+PHZJUEk+MC4wMDwvdklQST48dklQSURldm9sPjAuMDA8L3ZJUElEZXZvbD48dlBJUz4xNi4zMDwvdlBJUz48dkNPRklOUz43NS4yMDwvdkNPRklOUz48dk91dHJvPjAuMDA8L3ZPdXRybz48dk5GPjk4Ljk3PC92TkY+PHZUb3RUcmliPjI2OS42NDwvdlRvdFRyaWI+PC9JQ01TVG90PjwvdG90YWw+PHRyYW5zcD48bW9kRnJldGU+OTwvbW9kRnJldGU+PHZvbD48cVZvbD4xPC9xVm9sPjxlc3A+Q2lsaW5kcm88L2VzcD48bWFyY2E+MDwvbWFyY2E+PG5Wb2w+MDwvblZvbD48cGVzb0w+NjYuNzgwPC9wZXNvTD48cGVzb0I+NDUwLjc4MDwvcGVzb0I+PC92b2w+PC90cmFuc3A+PHBhZz48ZGV0UGFnPjx0UGFnPjAxPC90UGFnPjx2UGFnPjUwLjAwPC92UGFnPjwvZGV0UGFnPjxkZXRQYWc+PHRQYWc+MDM8L3RQYWc+PHZQYWc+OC45NzwvdlBhZz48L2RldFBhZz48ZGV0UGFnPjx0UGFnPjAzPC90UGFnPjx2UGFnPjQwLjAwPC92UGFnPjxjYXJkPjx0cEludGVncmE+MTwvdHBJbnRlZ3JhPjxDTlBKPjk5OTk5OTk5OTk5OTk5PC9DTlBKPjx0QmFuZD4wMjwvdEJhbmQ+PGNBdXQ+OTk5OTk5OTk5OTk5OTk5OTk5OTk8L2NBdXQ+PC9jYXJkPjwvZGV0UGFnPjwvcGFnPjxpbmZBZGljPjxpbmZBZEZpc2NvPkNsaWVudGU6IDExMi4gUmVtZXNzYTogMDAwMDYxMDc0LTAxMjM8L2luZkFkRmlzY28+PC9pbmZBZGljPjwvaW5mTkZlPjxTaWduYXR1cmUgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvMDkveG1sZHNpZyMiPjxTaWduZWRJbmZvPjxDYW5vbmljYWxpemF0aW9uTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvVFIvMjAwMS9SRUMteG1sLWMxNG4tMjAwMTAzMTUiPjwvQ2Fub25pY2FsaXphdGlvbk1ldGhvZD48U2lnbmF0dXJlTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxkc2lnI3JzYS1zaGExIj48L1NpZ25hdHVyZU1ldGhvZD48UmVmZXJlbmNlIFVSST0iI05GZTM1MTkwMjIyNzY5NTMwMDAwMTMxNTUwMDAwMDAwMDAxMDAxNTU4Mjc3NjAzIj48VHJhbnNmb3Jtcz48VHJhbnNmb3JtIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxkc2lnI2VudmVsb3BlZC1zaWduYXR1cmUiPjwvVHJhbnNmb3JtPjxUcmFuc2Zvcm0gQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy14bWwtYzE0bi0yMDAxMDMxNSI+PC9UcmFuc2Zvcm0+PC9UcmFuc2Zvcm1zPjxEaWdlc3RNZXRob2QgQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwLzA5L3htbGRzaWcjc2hhMSI+PC9EaWdlc3RNZXRob2Q+PERpZ2VzdFZhbHVlPkZiY1RiWkVwZG9KYm95bFFKWHNoZ3k2QlZucz08L0RpZ2VzdFZhbHVlPjwvUmVmZXJlbmNlPjwvU2lnbmVkSW5mbz48U2lnbmF0dXJlVmFsdWU+RklHTmVmejl6TnJuOG95Zm5QSGdwVlo2d20yMkVUM3NsZUxGdHJhL2hCKzIva2JJTUI0RjNqcnNlUkhHaSt2TURiWTF3dUtKSytxUVJSUXpRVnl5QlhER21VNnF5MUs3bklWOXd2cGw5WExaTDhaMWl4dS9SVW1mQWdxK1RHUExNQ0lWa1RUWkdMb2JZOUN0WFczOGJGN29qR2t1MVZTK2R2b1pwSkdiTVdoOFQ2RGxyYjZYbExweERPTXlhVjlOeHVqVnNHS0l5RnZpZUwvNG9DdGhiZVk1UFhUOCtHNzEyWDZpVnl6Vi9QYVFac2hhUnNadmcxWEg5ZUhlWTlhOE1ZRGt3dmcvYVQwQkJaU3ZnajNHbUM4RzNJV1FHUUNrN2QxSkhybVVLaUxNYVIwb2xVZit3SUJOempVZWllM0dWakRMZGk1ZEpDVHk0eFBsTGJ5d2NBPT08L1NpZ25hdHVyZVZhbHVlPjxLZXlJbmZvPjxYNTA5RGF0YT48WDUwOUNlcnRpZmljYXRlPk1JSUhyRENDQlpTZ0F3SUJBZ0lJRWQ0WUJ3UllwZkF3RFFZSktvWklodmNOQVFFTEJRQXdnWWt4Q3pBSkJnTlZCQVlUQWtKU01STXdFUVlEVlFRS0V3cEpRMUF0UW5KaGMybHNNVFF3TWdZRFZRUUxFeXRCZFhSdmNtbGtZV1JsSUVObGNuUnBabWxqWVdSdmNtRWdVbUZwZWlCQ2NtRnphV3hsYVhKaElIWXlNUkl3RUFZRFZRUUxFd2xCUXlCVFQweFZWRWt4R3pBWkJnTlZCQU1URWtGRElGTlBURlZVU1NCTmRXeDBhWEJzWVRBZUZ3MHhPREEzTURReU1UVTJOVFphRncweE9UQTNNRFF4T0RFek1EQmFNSUhWTVFzd0NRWURWUVFHRXdKQ1VqRVRNQkVHQTFVRUNoTUtTVU5RTFVKeVlYTnBiREUwTURJR0ExVUVDeE1yUVhWMGIzSnBaR0ZrWlNCRFpYSjBhV1pwWTJGa2IzSmhJRkpoYVhvZ1FuSmhjMmxzWldseVlTQjJNakVTTUJBR0ExVUVDeE1KUVVNZ1UwOU1WVlJKTVJzd0dRWURWUVFMRXhKQlF5QlRUMHhWVkVrZ1RYVnNkR2x3YkdFeEdqQVlCZ05WQkFzVEVVTmxjblJwWm1sallXUnZJRkJLSUVFeE1TNHdMQVlEVlFRREV5VlFSRlpGVGtRZ1ZFVkRUazlNVDBkSlFTQk1WRVJCT2pJeU56WTVOVE13TURBd01UTXhNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUZBQU9DQVE4QU1JSUJDZ0tDQVFFQTBnWDgvbEV0bFFNZ1Fnc3QwZkxNQzV4R3UwbGZ1L0dZRWk4M0oyVGtWaVUvWjdpL0QyN1ZhYTRwcXZwZElqVm4zTytiZzdVdFBPSVBMNHFMTDE3dnJ2SWI1V0FtNzJIUDgvaFRoRkZ1VjV3NjZITmgwNEd0TEF1NDhRempaVk4yU2FYdElWeldSczM2YnZFNUdSRzE4bHdqOWV6NlRiZjhaN3p6d2d2cWRWaC9nNWI5NU9vaVRTMkhmV1Z1Ry9QY2xEK1hjZHZtcklsWDlWZVhXaWxrZjAwd2l2ajdjMkJmMmZZY1RWTUg5OUwyaXVDcHhSV0lEL3JhTWlpb1o1VkI5cko3THF1aVIvdFRDWVBheWVMMjhHZGtBTTRwQUg0WVJqZFF1NjBmS0hDMmhKTnhFSWYrUGhZeTBYRFQybENsa2M1elFFdVd2ZjJyK2dtc1oyQ1Ewd0lEQVFBQm80SUN5RENDQXNRd1ZBWUlLd1lCQlFVSEFRRUVTREJHTUVRR0NDc0dBUVVGQnpBQ2hqaG9kSFJ3T2k4dlkyTmtMbUZqYzI5c2RYUnBMbU52YlM1aWNpOXNZM0l2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExuQTNZakFkQmdOVkhRNEVGZ1FVVE1oa2lReFBIY1hhZERSUzFIRjdNV1VJckRvd0NRWURWUjBUQkFJd0FEQWZCZ05WSFNNRUdEQVdnQlExcmpFVTlsN1NlazlZL2pTb0dtZVhDc1NiQnpCZUJnTlZIU0FFVnpCVk1GTUdCbUJNQVFJQkpqQkpNRWNHQ0NzR0FRVUZCd0lCRmp0b2RIUndjem92TDJOalpDNWhZM052YkhWMGFTNWpiMjB1WW5JdlpHOWpjeTlrY0dNdFlXTXRjMjlzZFhScExXMTFiSFJwY0d4aExuQmtaakNCM2dZRFZSMGZCSUhXTUlIVE1ENmdQS0E2aGpob2RIUndPaTh2WTJOa0xtRmpjMjlzZFhScExtTnZiUzVpY2k5c1kzSXZZV010YzI5c2RYUnBMVzExYkhScGNHeGhMWFl4TG1OeWJEQS9vRDJnTzRZNWFIUjBjRG92TDJOalpESXVZV056YjJ4MWRHa3VZMjl0TG1KeUwyeGpjaTloWXkxemIyeDFkR2t0YlhWc2RHbHdiR0V0ZGpFdVkzSnNNRkNnVHFCTWhrcG9kSFJ3T2k4dmNtVndiM05wZEc5eWFXOHVhV053WW5KaGMybHNMbWR2ZGk1aWNpOXNZM0l2UVVOVFQweFZWRWt2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExtTnliREFPQmdOVkhROEJBZjhFQkFNQ0JlQXdIUVlEVlIwbEJCWXdGQVlJS3dZQkJRVUhBd0lHQ0NzR0FRVUZCd01FTUlHd0JnTlZIUkVFZ2Fnd2dhV0JFMkp5ZFc1dlFIQmtkbVZ1WkM1amIyMHVZbktnSUFZRllFd0JBd0tnRnhNVlFsSlZUazhnVmtWTVQxTlBJRVpGVWxKRlNWSkJvQmtHQldCTUFRTURvQkFURGpJeU56WTVOVE13TURBd01UTXhvRGdHQldCTUFRTUVvQzhUTFRJek1EZ3hPVGcxTURBMk5ESXlNakl4Tnpjd01EQXdNREF3TURBd01EQXdNREF3TURBd01EQXdNREF3TUtBWEJnVmdUQUVEQjZBT0V3d3dNREF3TURBd01EQXdNREF3RFFZSktvWklodmNOQVFFTEJRQURnZ0lCQUR4ek12YWpTbFVRMkd4cko5SU96SXB6V0V2cDhUb003MXpqclhCK2R3VnMxRDVjUlFBOGh2bzAxeHdaNDVzNlBNbW1qSng4WElSUVdCM2RMVi82bUtwTkdDY1BXN2d1bit4M1ZMa1JMVG9mUW1WVnJxaldUeitZdW14ejk0eHdSMmtKR2g2dTNueHY5MmhUaVhkKzd2UmZNUGNzQU8wVnR2aFg3eHF0Y2JPdVVyZmU4UW5FRlE2WmI2aE1aUVBtSVE1K1dWY2R5TzdVZytZR1NZeWZ2UHhySWpBQk5XcGpuTUZJUEZwcTgvalhlbFhzVXlvbThTc3hOdGJ4OThLc0dLd3Q1ZkRPb2NvdnFGNmpKOHpzak1uL2pZV2lhTkhRMnBLbzNFbWl0YW82b2JCT1hGdU5xV2M1VXo4V01tK2lUTXlKbjh4b3R6cmhrYTZjNVl1SjBieEovcFBsS0pBT2tEVFZZb1RBMTkwM1gvMG51blQyZDdJMVYzRDRNYmxvMWxDV1VnakZuVENtdlJGZmhoQzh1TXdYc2M5UkprVm1UeCs3cU9oWXpDRkVKTnFLb0FvZUJJTHZOWXltRTUxaG1tbmFhTEw0QkJuUmhHZllIRUhOWGRrOU81MlBNOWVXSHZ5c0xlWEpMRjBXVHh0L0V5QThxbGtZM2JLN1Z5VllWM2tOVWRPeHJ4NTA3VjZRSVVTYTdXc05janprM3JBN0U1dklRbkNLR2ZlbVJoOEFSc1dIaGltVG4yYkQ2bGhXYlBMN0ZkWWo4eVlFMCt0T2V3OHhQVXQ1Y2pDekJhZDBuZXFvNkkzVTUyaEV4bWhUVUNMcVk1RG5PeGhWRHNtWS9pUUtNalBXR3lETUtkTGJCbFozelYyeE5EMktlcVlVblRxYlduNGk3amppPC9YNTA5Q2VydGlmaWNhdGU+PC9YNTA5RGF0YT48L0tleUluZm8+PC9TaWduYXR1cmU+PC9ORmU+PC9lbnZpTkZlPg==",
      "cliente": {
        "cpf_cnpj": "46728754000163",
        "email": "teste@nexaas.com.br",
        "indicador_inscricao_estadual": 1,
        "inscricao_estadual": "407056228113",
        "inscricao_municipal": "",
        "inscricao_suframa": "",
        "nome": "NF-E EMITIDA EM AMBIENTE DE HOMOLOGACAO - SEM VALOR FISCAL",
        "pessoa_fisica_juridica": "company",
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
          "telefone": "99999999",
          "uf": "SP"
        }
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
        "data_saida_entrada": "2018-09-28T17:07:35-03:00",
        "destino_operacao": "1",
        "finalidade_nfe": "1",
        "indicador_consumidor_final": "0",
        "indicador_presenca": "9",
        "natureza_operacao": "Venda merc. adq. rec. terc. efet. fora estab.",
        "tipo_operacao": "1",
        "uf": 35,
        "nfe_numero": 101,
        "serie": 1
      },
      "forma_de_pagamento": [
        {
          "tipo_de_pagamento": "01",
          "valor_do_pagamento": 50
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
          "valor_do_pagamento": 40
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
          "outras_despesas": 0,
          "producao_escala": "S",
          "quantidade_comercial": 6,
          "quantidade_tributaria": 6,
          "unidade_comercial": "M3",
          "unidade_tributaria": "M3",
          "valor_desconto": 0,
          "valor_frete": 0,
          "valor_seguro": 0,
          "valor_total_produto": "98.97",
          "valor_unitario_comercial": 16.49485,
          "valor_unitario_tributario": 16.49485,
          "tributacao": {
            "valor_aproximado_total": 269.64,
            "cofins": {
              "aliquota_cofins": "7.60",
              "aliquota_cofins_reais": 0,
              "aliquota_cofins_st_reais": 0,
              "aliquota_st": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_st": 0,
              "valor_cofins": 75.2,
              "valor_cofins_st": 0
            },
            "icms": {
              "aliquota_consumidor_final": 0,
              "aliquota_fcp": 0,
              "aliquota_fcp_st": 0,
              "aliquota_fcp_st_retido": 0,
              "aliquota_icms": "18.00",
              "aliquota_icms_simples_nacional": 0,
              "aliquota_icms_st": 0,
              "aliquota_interestadual": 0,
              "aliquota_interna_interestadual": 0,
              "base_icmsst_retido": 0,
              "codigo_origem_produto": 3,
              "credito_icms_simples_nacional": 0,
              "modalidade_base_calculo": 3,
              "modalidade_base_calculo_st": "3",
              "motivo_desoneracao": "",
              "perc_diferimento": 0,
              "perc_fcp_interestadual": 0,
              "perc_mva_icms_st": 0,
              "perc_provisorio_interestadual": 0,
              "perc_reducao_base_calculo": 0,
              "perc_reducao_base_calculo_st": 0,
              "situacao_simples_nacional": 0,
              "situacao_tributaria": "00",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_fcp": 0,
              "valor_base_calculo_fcp_st": 0,
              "valor_base_calculo_fcp_st_retido": 0,
              "valor_base_calculo_st": 0,
              "valor_base_calculo_uf_dest": 0,
              "valor_fcp": 0,
              "valor_fcp_interestadual": 0,
              "valor_fcp_st": 0,
              "valor_fcp_st_retido": 0,
              "valor_icms": 178.14,
              "valor_icms_desonerado": 0,
              "valor_icms_diferido": 0,
              "valor_icms_operacao": 0,
              "valor_icms_st": 0,
              "valor_icmsst_retido": 0,
              "valor_uf_destinatario_interestadual": 0,
              "valor_uf_rementente": 0,
              "valor_uf_remetente_interestadual": 0
            },
            "importacao": {
              "base_calculo_importacao": "",
              "valor_despesas_aduaneiras": "",
              "valor_imposto_importacao": "",
              "valor_iof": ""
            },
            "ipi": {
              "aliquota_ipi": "0.00",
              "cnpj_produtor": "",
              "codigo_enquadramento": 999,
              "codigo_selo_controle": 0,
              "quantidade_selo_controle": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": "989.69",
              "valor_ipi": "0.00",
              "valor_unidade": ""
            },
            "pis": {
              "aliquota_pis": 1.65,
              "aliquota_pis_reais": 0,
              "aliquota_pis_reais_st": 0,
              "aliquota_st": 0,
              "situacao_tributaria": "01",
              "valor_base_calculo": 989.69,
              "valor_base_calculo_st": 0,
              "valor_pis": 16.3,
              "valor_pis_st": 0
            }
          },
          "declaracao_importacao": [
            {
              "cnpj": "",
              "codigo_exportador": "",
              "data_desembaraco": "",
              "data_importacao": "",
              "documento_importacao": "",
              "forma_importacao": "",
              "local_desembaraco": "",
              "uf_adquirente": "",
              "uf_desembaraco": "",
              "valor_afrmm": "",
              "via_transporte": "",
              "adicoes": [
                {
                  "codigo_fabricante": "",
                  "numero_adicao": "",
                  "numero_drawback": "",
                  "numero_sequencial": "",
                  "valor_desconto": ""
                }
              ]
            }
          ]
        }
      ],
      "retencao_tributos": {
        "base_calculo_retencao_previdencia": 0,
        "valor_base_calculo_irrf": 0,
        "valor_irrf": 0,
        "valor_retencao_previdencia": 0,
        "valor_retido_cofins": 0,
        "valor_retido_csll": 0,
        "valor_retido_pis": 0
      },
      "transporte": {
        "codigo_modalidade": 9,
        "retencao_icms": {
          "aliquota_retencao": 0,
          "cfop": "",
          "codigo_municipio": "",
          "uf": "",
          "valor_base_calculo": 0,
          "valor_retido": 0,
          "valor_servico": 0
        },
        "transportadora": {
          "cnpj_cpf": "",
          "endereco_completo": "",
          "inscricao_estadual": "",
          "municipio": "",
          "razao_social": "",
          "uf": ""
        },
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
  }'


EXEMPLO DE RESPOSTA

{
  "nfce": {
    "id": 10990,
    "status": "processing"
  }
}
```
