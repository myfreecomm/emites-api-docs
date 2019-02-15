# Autorização de XML em lote

## Autorização de XML em lote de NF-e

Para autorizar o XML de um lote de NF-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfe_batch/authorize</h6>
    </div>
</div>

<aside class="warning">
  Todos os campos de texto da NF-e não aceitam caracteres acentuados como, por exemplo "á", "é", "â", "ã" etc. Também não aceitam "ç".
</aside>

Os campos utilizados para esse tipo de emissão são os mesmos praticados na Emissão de NF-e em lote, com exceção do **xml_assinado**.

O valor desse campo deve conter o XML do lote de NF-e assinado utilizando o método de codificação **Base64**.

<aside class="notice">
    <b>Atenção</b>: É importante que os campos <b>nfe_numero</b> e <b>serie</b> contidos em dados_gerais de cada NF-e sejam os mesmos que foram utilizados para compôr o XML do lote enviado no <b>xml_assinado</b>. Caso contrário, as respostas obtidas na SEFAZ não serão persistidos na NF-e.
</aside>

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfe_batch/authorize \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json' \
  -d '{
        "nfe_batch": {
          "lote": 1,
          "serie": 1,
          "sincronicidade": 0,
          "uf": 35,
          "xml_assinado": "PGVudmlORmUgeG1sbnM9Imh0dHA6Ly93d3cucG9ydGFsZmlzY2FsLmluZi5i
          ci9uZmUiIHZlcnNhbz0iNC4wMCI+PGlkTG90ZT4xMDA8L2lkTG90ZT48aW5k
          U2luYz4xPC9pbmRTaW5jPjxORmU+PGluZk5GZSBJZD0iTkZlMzUxOTAyMjI3
          Njk1MzAwMDAxMzE1NTAwMDAwMDAwMDEwMDE1NTgyNzc2MDMiIHZlcnNhbz0i
          NC4wMCI+PGlkZT48Y1VGPjM1PC9jVUY+PGNORj41NTgyNzc2MDwvY05GPjxu
          YXRPcD5WZW5kYSBtZXJjLiBhZHEuIHJlYy4gdGVyYy4gZWZldC4gZm9yYSBl
          c3RhYi48L25hdE9wPjxtb2Q+NTU8L21vZD48c2VyaWU+PC9zZXJpZT48bk5G
          PjEwMDwvbk5GPjxkaEVtaT4yMDE5LTAyLTE1VDA5OjU5OjE3LTAyOjAwPC9k
          aEVtaT48ZGhTYWlFbnQ+MjAxOC0wOS0yOFQxNzowNzozNS0wMzowMDwvZGhT
          YWlFbnQ+PHRwTkY+MTwvdHBORj48aWREZXN0PjE8L2lkRGVzdD48Y011bkZH
          PjM1MjU5MDQ8L2NNdW5GRz48dHBJbXA+MTwvdHBJbXA+PHRwRW1pcz4xPC90
          cEVtaXM+PGNEVj4zPC9jRFY+PHRwQW1iPjI8L3RwQW1iPjxmaW5ORmU+MTwv
          ZmluTkZlPjxpbmRGaW5hbD4wPC9pbmRGaW5hbD48aW5kUHJlcz45PC9pbmRQ
          cmVzPjxwcm9jRW1pPjA8L3Byb2NFbWk+PHZlclByb2M+NC4wMDwvdmVyUHJv
          Yz48L2lkZT48ZW1pdD48Q05QSj4yMjc2OTUzMDAwMDEzMTwvQ05QSj48eE5v
          bWU+T3JnYW5pemFjYW8gVGVzdGUgTkZDZS9ERjwveE5vbWU+PHhGYW50Pk9y
          Z2FuaXphY2FvIFRlc3RlIE5GQ2UgLyBERjwveEZhbnQ+PGVuZGVyRW1pdD48
          eExncj5TQVVTIFF1YWRyYSA0IExvdGUgOS8xMDwveExncj48bnJvPjA0PC9u
          cm8+PHhDcGw+Q29tcGxlbWVudG88L3hDcGw+PHhCYWlycm8+QXNhIFN1bDwv
          eEJhaXJybz48Y011bj41MzAwMTA4PC9jTXVuPjx4TXVuPkJyYXNpbGlhPC94
          TXVuPjxVRj5ERjwvVUY+PENFUD43MDA3MDkzODwvQ0VQPjxjUGFpcz4xMDU4
          PC9jUGFpcz48eFBhaXM+QnJhc2lsPC94UGFpcz48Zm9uZT4xNTM1MzEyMTY0
          PC9mb25lPjwvZW5kZXJFbWl0PjxJRT43NzI3MzM3MDAxMjA8L0lFPjxDUlQ+
          MzwvQ1JUPjwvZW1pdD48ZGVzdD48Q05QSj40NjcyODc1NDAwMDE2MzwvQ05Q
          Sj48eE5vbWU+TkYtRSBFTUlUSURBIEVNIEFNQklFTlRFIERFIEhPTU9MT0dB
          Q0FPIC0gU0VNIFZBTE9SIEZJU0NBTDwveE5vbWU+PGVuZGVyRGVzdD48eExn
          cj5BViBHVUlMSEVSTUUgUE9SQ0FSSTwveExncj48bnJvPlMgTjwvbnJvPjx4
          QmFpcnJvPk1FREVJUk9TPC94QmFpcnJvPjxjTXVuPjM1MjU5MDQ8L2NNdW4+
          PHhNdW4+SlVORElBSTwveE11bj48VUY+U1A8L1VGPjxDRVA+MTMyMTIyNTU8
          L0NFUD48Y1BhaXM+MTA1ODwvY1BhaXM+PHhQYWlzPkJSQVNJTDwveFBhaXM+
          PGZvbmU+OTk5OTk5OTk8L2ZvbmU+PC9lbmRlckRlc3Q+PGluZElFRGVzdD4x
          PC9pbmRJRURlc3Q+PElFPjQwNzA1NjIyODExMzwvSUU+PGVtYWlsPnRlc3Rl
          QG5leGFhcy5jb20uYnI8L2VtYWlsPjwvZGVzdD48ZGV0IG5JdGVtPSIxIj48
          cHJvZD48Y1Byb2Q+MTIzNDU2PC9jUHJvZD48Y0VBTj5TRU0gR1RJTjwvY0VB
          Tj48eFByb2Q+TklUUk9HRU5JTyBDSUwgNTBMIDEwTTM8L3hQcm9kPjxOQ00+
          MjgwNDMwMDA8L05DTT48Q0ZPUD41MTA0PC9DRk9QPjx1Q29tPk0zPC91Q29t
          PjxxQ29tPjY8L3FDb20+PHZVbkNvbT4xNi40OTQ4NTwvdlVuQ29tPjx2UHJv
          ZD45OC45NzwvdlByb2Q+PGNFQU5UcmliPlNFTSBHVElOPC9jRUFOVHJpYj48
          dVRyaWI+TTM8L3VUcmliPjxxVHJpYj42PC9xVHJpYj48dlVuVHJpYj4xNi40
          OTQ4NTwvdlVuVHJpYj48aW5kVG90PjE8L2luZFRvdD48eFBlZD5TMDEwMDI0
          OTEzNDwveFBlZD48bkl0ZW1QZWQ+MTwvbkl0ZW1QZWQ+PC9wcm9kPjxpbXBv
          c3RvPjx2VG90VHJpYj4yNjkuNjQ8L3ZUb3RUcmliPjxJQ01TPjxJQ01TMDA+
          PG9yaWc+Mzwvb3JpZz48Q1NUPjAwPC9DU1Q+PG1vZEJDPjM8L21vZEJDPjx2
          QkM+OTg5LjY5PC92QkM+PHBJQ01TPjE4LjAwMDA8L3BJQ01TPjx2SUNNUz4x
          NzguMTQ8L3ZJQ01TPjwvSUNNUzAwPjwvSUNNUz48SVBJPjxjU2Vsbz4wPC9j
          U2Vsbz48cVNlbG8+MDwvcVNlbG8+PGNFbnE+OTk5PC9jRW5xPjxJUElOVD48
          Q1NUPjAxPC9DU1Q+PC9JUElOVD48L0lQST48UElTPjxQSVNBbGlxPjxDU1Q+
          MDE8L0NTVD48dkJDPjk4OS42OTwvdkJDPjxwUElTPjEuNjUwMDwvcFBJUz48
          dlBJUz4xNi4zMDwvdlBJUz48L1BJU0FsaXE+PC9QSVM+PENPRklOUz48Q09G
          SU5TQWxpcT48Q1NUPjAxPC9DU1Q+PHZCQz45ODkuNjk8L3ZCQz48cENPRklO
          Uz43LjYwMDA8L3BDT0ZJTlM+PHZDT0ZJTlM+NzUuMjA8L3ZDT0ZJTlM+PC9D
          T0ZJTlNBbGlxPjwvQ09GSU5TPjwvaW1wb3N0bz48L2RldD48dG90YWw+PElD
          TVNUb3Q+PHZCQz45ODkuNjk8L3ZCQz48dklDTVM+MTc4LjE0PC92SUNNUz48
          dklDTVNEZXNvbj4wLjAwPC92SUNNU0Rlc29uPjx2RkNQVUZEZXN0PjAuMDA8
          L3ZGQ1BVRkRlc3Q+PHZJQ01TVUZEZXN0PjAuMDA8L3ZJQ01TVUZEZXN0Pjx2
          SUNNU1VGUmVtZXQ+MC4wMDwvdklDTVNVRlJlbWV0Pjx2RkNQPjAuMDA8L3ZG
          Q1A+PHZCQ1NUPjAuMDA8L3ZCQ1NUPjx2U1Q+MC4wMDwvdlNUPjx2RkNQU1Q+
          MC4wMDwvdkZDUFNUPjx2RkNQU1RSZXQ+MC4wMDwvdkZDUFNUUmV0Pjx2UHJv
          ZD45OC45NzwvdlByb2Q+PHZGcmV0ZT4wLjAwPC92RnJldGU+PHZTZWc+MC4w
          MDwvdlNlZz48dkRlc2M+MC4wMDwvdkRlc2M+PHZJST4wLjAwPC92SUk+PHZJ
          UEk+MC4wMDwvdklQST48dklQSURldm9sPjAuMDA8L3ZJUElEZXZvbD48dlBJ
          Uz4xNi4zMDwvdlBJUz48dkNPRklOUz43NS4yMDwvdkNPRklOUz48dk91dHJv
          PjAuMDA8L3ZPdXRybz48dk5GPjk4Ljk3PC92TkY+PHZUb3RUcmliPjI2OS42
          NDwvdlRvdFRyaWI+PC9JQ01TVG90PjwvdG90YWw+PHRyYW5zcD48bW9kRnJl
          dGU+OTwvbW9kRnJldGU+PHZvbD48cVZvbD4xPC9xVm9sPjxlc3A+Q2lsaW5k
          cm88L2VzcD48bWFyY2E+MDwvbWFyY2E+PG5Wb2w+MDwvblZvbD48cGVzb0w+
          NjYuNzgwPC9wZXNvTD48cGVzb0I+NDUwLjc4MDwvcGVzb0I+PC92b2w+PC90
          cmFuc3A+PHBhZz48ZGV0UGFnPjx0UGFnPjAxPC90UGFnPjx2UGFnPjUwLjAw
          PC92UGFnPjwvZGV0UGFnPjxkZXRQYWc+PHRQYWc+MDM8L3RQYWc+PHZQYWc+
          OC45NzwvdlBhZz48L2RldFBhZz48ZGV0UGFnPjx0UGFnPjAzPC90UGFnPjx2
          UGFnPjQwLjAwPC92UGFnPjxjYXJkPjx0cEludGVncmE+MTwvdHBJbnRlZ3Jh
          PjxDTlBKPjk5OTk5OTk5OTk5OTk5PC9DTlBKPjx0QmFuZD4wMjwvdEJhbmQ+
          PGNBdXQ+OTk5OTk5OTk5OTk5OTk5OTk5OTk8L2NBdXQ+PC9jYXJkPjwvZGV0
          UGFnPjwvcGFnPjxpbmZBZGljPjxpbmZBZEZpc2NvPkNsaWVudGU6IDExMi4g
          UmVtZXNzYTogMDAwMDYxMDc0LTAxMjM8L2luZkFkRmlzY28+PC9pbmZBZGlj
          PjwvaW5mTkZlPjxTaWduYXR1cmUgeG1sbnM9Imh0dHA6Ly93d3cudzMub3Jn
          LzIwMDAvMDkveG1sZHNpZyMiPjxTaWduZWRJbmZvPjxDYW5vbmljYWxpemF0
          aW9uTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvVFIvMjAw
          MS9SRUMteG1sLWMxNG4tMjAwMTAzMTUiPjwvQ2Fub25pY2FsaXphdGlvbk1l
          dGhvZD48U2lnbmF0dXJlTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53
          My5vcmcvMjAwMC8wOS94bWxkc2lnI3JzYS1zaGExIj48L1NpZ25hdHVyZU1l
          dGhvZD48UmVmZXJlbmNlIFVSST0iI05GZTM1MTkwMjIyNzY5NTMwMDAwMTMx
          NTUwMDAwMDAwMDAxMDAxNTU4Mjc3NjAzIj48VHJhbnNmb3Jtcz48VHJhbnNm
          b3JtIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxk
          c2lnI2VudmVsb3BlZC1zaWduYXR1cmUiPjwvVHJhbnNmb3JtPjxUcmFuc2Zv
          cm0gQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy14
          bWwtYzE0bi0yMDAxMDMxNSI+PC9UcmFuc2Zvcm0+PC9UcmFuc2Zvcm1zPjxE
          aWdlc3RNZXRob2QgQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy8yMDAw
          LzA5L3htbGRzaWcjc2hhMSI+PC9EaWdlc3RNZXRob2Q+PERpZ2VzdFZhbHVl
          PkZiY1RiWkVwZG9KYm95bFFKWHNoZ3k2QlZucz08L0RpZ2VzdFZhbHVlPjwv
          UmVmZXJlbmNlPjwvU2lnbmVkSW5mbz48U2lnbmF0dXJlVmFsdWU+RklHTmVm
          ejl6TnJuOG95Zm5QSGdwVlo2d20yMkVUM3NsZUxGdHJhL2hCKzIva2JJTUI0
          RjNqcnNlUkhHaSt2TURiWTF3dUtKSytxUVJSUXpRVnl5QlhER21VNnF5MUs3
          bklWOXd2cGw5WExaTDhaMWl4dS9SVW1mQWdxK1RHUExNQ0lWa1RUWkdMb2JZ
          OUN0WFczOGJGN29qR2t1MVZTK2R2b1pwSkdiTVdoOFQ2RGxyYjZYbExweERP
          TXlhVjlOeHVqVnNHS0l5RnZpZUwvNG9DdGhiZVk1UFhUOCtHNzEyWDZpVnl6
          Vi9QYVFac2hhUnNadmcxWEg5ZUhlWTlhOE1ZRGt3dmcvYVQwQkJaU3ZnajNH
          bUM4RzNJV1FHUUNrN2QxSkhybVVLaUxNYVIwb2xVZit3SUJOempVZWllM0dW
          akRMZGk1ZEpDVHk0eFBsTGJ5d2NBPT08L1NpZ25hdHVyZVZhbHVlPjxLZXlJ
          bmZvPjxYNTA5RGF0YT48WDUwOUNlcnRpZmljYXRlPk1JSUhyRENDQlpTZ0F3
          SUJBZ0lJRWQ0WUJ3UllwZkF3RFFZSktvWklodmNOQVFFTEJRQXdnWWt4Q3pB
          SkJnTlZCQVlUQWtKU01STXdFUVlEVlFRS0V3cEpRMUF0UW5KaGMybHNNVFF3
          TWdZRFZRUUxFeXRCZFhSdmNtbGtZV1JsSUVObGNuUnBabWxqWVdSdmNtRWdV
          bUZwZWlCQ2NtRnphV3hsYVhKaElIWXlNUkl3RUFZRFZRUUxFd2xCUXlCVFQw
          eFZWRWt4R3pBWkJnTlZCQU1URWtGRElGTlBURlZVU1NCTmRXeDBhWEJzWVRB
          ZUZ3MHhPREEzTURReU1UVTJOVFphRncweE9UQTNNRFF4T0RFek1EQmFNSUhW
          TVFzd0NRWURWUVFHRXdKQ1VqRVRNQkVHQTFVRUNoTUtTVU5RTFVKeVlYTnBi
          REUwTURJR0ExVUVDeE1yUVhWMGIzSnBaR0ZrWlNCRFpYSjBhV1pwWTJGa2Iz
          SmhJRkpoYVhvZ1FuSmhjMmxzWldseVlTQjJNakVTTUJBR0ExVUVDeE1KUVVN
          Z1UwOU1WVlJKTVJzd0dRWURWUVFMRXhKQlF5QlRUMHhWVkVrZ1RYVnNkR2x3
          YkdFeEdqQVlCZ05WQkFzVEVVTmxjblJwWm1sallXUnZJRkJLSUVFeE1TNHdM
          QVlEVlFRREV5VlFSRlpGVGtRZ1ZFVkRUazlNVDBkSlFTQk1WRVJCT2pJeU56
          WTVOVE13TURBd01UTXhNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUZBQU9DQVE4
          QU1JSUJDZ0tDQVFFQTBnWDgvbEV0bFFNZ1Fnc3QwZkxNQzV4R3UwbGZ1L0dZ
          RWk4M0oyVGtWaVUvWjdpL0QyN1ZhYTRwcXZwZElqVm4zTytiZzdVdFBPSVBM
          NHFMTDE3dnJ2SWI1V0FtNzJIUDgvaFRoRkZ1VjV3NjZITmgwNEd0TEF1NDhR
          empaVk4yU2FYdElWeldSczM2YnZFNUdSRzE4bHdqOWV6NlRiZjhaN3p6d2d2
          cWRWaC9nNWI5NU9vaVRTMkhmV1Z1Ry9QY2xEK1hjZHZtcklsWDlWZVhXaWxr
          ZjAwd2l2ajdjMkJmMmZZY1RWTUg5OUwyaXVDcHhSV0lEL3JhTWlpb1o1VkI5
          cko3THF1aVIvdFRDWVBheWVMMjhHZGtBTTRwQUg0WVJqZFF1NjBmS0hDMmhK
          TnhFSWYrUGhZeTBYRFQybENsa2M1elFFdVd2ZjJyK2dtc1oyQ1Ewd0lEQVFB
          Qm80SUN5RENDQXNRd1ZBWUlLd1lCQlFVSEFRRUVTREJHTUVRR0NDc0dBUVVG
          QnpBQ2hqaG9kSFJ3T2k4dlkyTmtMbUZqYzI5c2RYUnBMbU52YlM1aWNpOXNZ
          M0l2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExuQTNZakFkQmdOVkhR
          NEVGZ1FVVE1oa2lReFBIY1hhZERSUzFIRjdNV1VJckRvd0NRWURWUjBUQkFJ
          d0FEQWZCZ05WSFNNRUdEQVdnQlExcmpFVTlsN1NlazlZL2pTb0dtZVhDc1Ni
          QnpCZUJnTlZIU0FFVnpCVk1GTUdCbUJNQVFJQkpqQkpNRWNHQ0NzR0FRVUZC
          d0lCRmp0b2RIUndjem92TDJOalpDNWhZM052YkhWMGFTNWpiMjB1WW5JdlpH
          OWpjeTlrY0dNdFlXTXRjMjlzZFhScExXMTFiSFJwY0d4aExuQmtaakNCM2dZ
          RFZSMGZCSUhXTUlIVE1ENmdQS0E2aGpob2RIUndPaTh2WTJOa0xtRmpjMjlz
          ZFhScExtTnZiUzVpY2k5c1kzSXZZV010YzI5c2RYUnBMVzExYkhScGNHeGhM
          WFl4TG1OeWJEQS9vRDJnTzRZNWFIUjBjRG92TDJOalpESXVZV056YjJ4MWRH
          a3VZMjl0TG1KeUwyeGpjaTloWXkxemIyeDFkR2t0YlhWc2RHbHdiR0V0ZGpF
          dVkzSnNNRkNnVHFCTWhrcG9kSFJ3T2k4dmNtVndiM05wZEc5eWFXOHVhV053
          WW5KaGMybHNMbWR2ZGk1aWNpOXNZM0l2UVVOVFQweFZWRWt2WVdNdGMyOXNk
          WFJwTFcxMWJIUnBjR3hoTFhZeExtTnliREFPQmdOVkhROEJBZjhFQkFNQ0Jl
          QXdIUVlEVlIwbEJCWXdGQVlJS3dZQkJRVUhBd0lHQ0NzR0FRVUZCd01FTUlH
          d0JnTlZIUkVFZ2Fnd2dhV0JFMkp5ZFc1dlFIQmtkbVZ1WkM1amIyMHVZbktn
          SUFZRllFd0JBd0tnRnhNVlFsSlZUazhnVmtWTVQxTlBJRVpGVWxKRlNWSkJv
          QmtHQldCTUFRTURvQkFURGpJeU56WTVOVE13TURBd01UTXhvRGdHQldCTUFR
          TUVvQzhUTFRJek1EZ3hPVGcxTURBMk5ESXlNakl4Tnpjd01EQXdNREF3TURB
          d01EQXdNREF3TURBd01EQXdNREF3TUtBWEJnVmdUQUVEQjZBT0V3d3dNREF3
          TURBd01EQXdNREF3RFFZSktvWklodmNOQVFFTEJRQURnZ0lCQUR4ek12YWpT
          bFVRMkd4cko5SU96SXB6V0V2cDhUb003MXpqclhCK2R3VnMxRDVjUlFBOGh2
          bzAxeHdaNDVzNlBNbW1qSng4WElSUVdCM2RMVi82bUtwTkdDY1BXN2d1bit4
          M1ZMa1JMVG9mUW1WVnJxaldUeitZdW14ejk0eHdSMmtKR2g2dTNueHY5MmhU
          aVhkKzd2UmZNUGNzQU8wVnR2aFg3eHF0Y2JPdVVyZmU4UW5FRlE2WmI2aE1a
          UVBtSVE1K1dWY2R5TzdVZytZR1NZeWZ2UHhySWpBQk5XcGpuTUZJUEZwcTgv
          alhlbFhzVXlvbThTc3hOdGJ4OThLc0dLd3Q1ZkRPb2NvdnFGNmpKOHpzak1u
          L2pZV2lhTkhRMnBLbzNFbWl0YW82b2JCT1hGdU5xV2M1VXo4V01tK2lUTXlK
          bjh4b3R6cmhrYTZjNVl1SjBieEovcFBsS0pBT2tEVFZZb1RBMTkwM1gvMG51
          blQyZDdJMVYzRDRNYmxvMWxDV1VnakZuVENtdlJGZmhoQzh1TXdYc2M5Ukpr
          Vm1UeCs3cU9oWXpDRkVKTnFLb0FvZUJJTHZOWXltRTUxaG1tbmFhTEw0QkJu
          UmhHZllIRUhOWGRrOU81MlBNOWVXSHZ5c0xlWEpMRjBXVHh0L0V5QThxbGtZ
          M2JLN1Z5VllWM2tOVWRPeHJ4NTA3VjZRSVVTYTdXc05janprM3JBN0U1dklR
          bkNLR2ZlbVJoOEFSc1dIaGltVG4yYkQ2bGhXYlBMN0ZkWWo4eVlFMCt0T2V3
          OHhQVXQ1Y2pDekJhZDBuZXFvNkkzVTUyaEV4bWhUVUNMcVk1RG5PeGhWRHNt
          WS9pUUtNalBXR3lETUtkTGJCbFozelYyeE5EMktlcVlVblRxYlduNGk3ampp
          PC9YNTA5Q2VydGlmaWNhdGU+PC9YNTA5RGF0YT48L0tleUluZm8+PC9TaWdu
          YXR1cmU+PC9ORmU+PC9lbnZpTkZlPg==",
          "nfes": [
            {
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
                  "unidade_comercial": "M3",
                  "unidade_tributaria": "M3",
                  "valor_desconto": 0.0,
                  "valor_frete": 0.0,
                  "valor_seguro": 0.0,
                  "valor_total_produto": "98.97",
                  "valor_unitario_comercial": 16.49485,
                  "valor_unitario_tributario": 16.49485,
                  "tributacao": {
                    "valor_aproximado_total": 269.64,
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
                      "aliquota_st": 0.0,
                      "situacao_tributaria": "01",
                      "valor_base_calculo": 989.69,
                      "valor_base_calculo_st": 0.0,
                      "valor_pis": 16.3,
                      "valor_pis_st": 0.0
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


EXEMPLO DE RESPOSTA

{
  "nfe_batch": {
    "id": 1099,
    "key": null,
    "nfes": [
      {
        "id": 10990,
        "status": "processing"
      }
    ]
  }
}
```

## Autorização de XML em lote de NFC-e

Para autorizar o XML de um lote de NFC-e, é necessário realizar uma requisição POST para o seguinte endereço:

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-get">POST</i>
        <h6>/api/v1/organizations/{organization_id}/nfce_batch/authorize</h6>
    </div>
</div>

<aside class="warning">
  Todos os campos de texto da NFC-e não aceitam caracteres acentuados como, por exemplo "á", "é", "â", "ã" etc. Também não aceitam "ç".
</aside>

Os campos utilizados para esse tipo de emissão são os mesmos praticados na Emissão de NFC-e em lote, com exceção do **xml_assinado**.

O valor desse campo deve conter o XML do lote de NFC-e assinado utilizando o método de codificação **Base64**.

<aside class="notice">
    <b>Atenção</b>: É importante que os campos <b>nfe_numero</b> e <b>serie</b> contidos em dados_gerais de cada NFC-e sejam os mesmos que foram utilizados para compôr o XML do lote enviado no <b>xml_assinado</b>. Caso contrário, as respostas obtidas na SEFAZ não serão persistidos na NFC-e.
</aside>

```shell
EXEMPLO DE REQUISIÇÃO

curl -X POST \
  https://app.emites.com.br/api/v1/organizations/11/nfce_batch/authorize \
  -H 'authorization: Token token=6f42433270bc61d746556b17605db1s4' \
  -H 'content-type: application/json' \
  -d '{
        "nfce_batch": {
          "lote": 1,
          "serie": 1,
          "sincronicidade": 0,
          "uf": 35,
          "xml_assinado": "PGVudmlORmUgeG1sbnM9Imh0dHA6Ly93d3cucG9ydGFsZmlzY2FsLmluZi5i
          ci9uZmUiIHZlcnNhbz0iNC4wMCI+PGlkTG90ZT4xMDA8L2lkTG90ZT48aW5k
          U2luYz4xPC9pbmRTaW5jPjxORmU+PGluZk5GZSBJZD0iTkZlMzUxOTAyMjI3
          Njk1MzAwMDAxMzE1NTAwMDAwMDAwMDEwMDE1NTgyNzc2MDMiIHZlcnNhbz0i
          NC4wMCI+PGlkZT48Y1VGPjM1PC9jVUY+PGNORj41NTgyNzc2MDwvY05GPjxu
          YXRPcD5WZW5kYSBtZXJjLiBhZHEuIHJlYy4gdGVyYy4gZWZldC4gZm9yYSBl
          c3RhYi48L25hdE9wPjxtb2Q+NTU8L21vZD48c2VyaWU+PC9zZXJpZT48bk5G
          PjEwMDwvbk5GPjxkaEVtaT4yMDE5LTAyLTE1VDA5OjU5OjE3LTAyOjAwPC9k
          aEVtaT48ZGhTYWlFbnQ+MjAxOC0wOS0yOFQxNzowNzozNS0wMzowMDwvZGhT
          YWlFbnQ+PHRwTkY+MTwvdHBORj48aWREZXN0PjE8L2lkRGVzdD48Y011bkZH
          PjM1MjU5MDQ8L2NNdW5GRz48dHBJbXA+MTwvdHBJbXA+PHRwRW1pcz4xPC90
          cEVtaXM+PGNEVj4zPC9jRFY+PHRwQW1iPjI8L3RwQW1iPjxmaW5ORmU+MTwv
          ZmluTkZlPjxpbmRGaW5hbD4wPC9pbmRGaW5hbD48aW5kUHJlcz45PC9pbmRQ
          cmVzPjxwcm9jRW1pPjA8L3Byb2NFbWk+PHZlclByb2M+NC4wMDwvdmVyUHJv
          Yz48L2lkZT48ZW1pdD48Q05QSj4yMjc2OTUzMDAwMDEzMTwvQ05QSj48eE5v
          bWU+T3JnYW5pemFjYW8gVGVzdGUgTkZDZS9ERjwveE5vbWU+PHhGYW50Pk9y
          Z2FuaXphY2FvIFRlc3RlIE5GQ2UgLyBERjwveEZhbnQ+PGVuZGVyRW1pdD48
          eExncj5TQVVTIFF1YWRyYSA0IExvdGUgOS8xMDwveExncj48bnJvPjA0PC9u
          cm8+PHhDcGw+Q29tcGxlbWVudG88L3hDcGw+PHhCYWlycm8+QXNhIFN1bDwv
          eEJhaXJybz48Y011bj41MzAwMTA4PC9jTXVuPjx4TXVuPkJyYXNpbGlhPC94
          TXVuPjxVRj5ERjwvVUY+PENFUD43MDA3MDkzODwvQ0VQPjxjUGFpcz4xMDU4
          PC9jUGFpcz48eFBhaXM+QnJhc2lsPC94UGFpcz48Zm9uZT4xNTM1MzEyMTY0
          PC9mb25lPjwvZW5kZXJFbWl0PjxJRT43NzI3MzM3MDAxMjA8L0lFPjxDUlQ+
          MzwvQ1JUPjwvZW1pdD48ZGVzdD48Q05QSj40NjcyODc1NDAwMDE2MzwvQ05Q
          Sj48eE5vbWU+TkYtRSBFTUlUSURBIEVNIEFNQklFTlRFIERFIEhPTU9MT0dB
          Q0FPIC0gU0VNIFZBTE9SIEZJU0NBTDwveE5vbWU+PGVuZGVyRGVzdD48eExn
          cj5BViBHVUlMSEVSTUUgUE9SQ0FSSTwveExncj48bnJvPlMgTjwvbnJvPjx4
          QmFpcnJvPk1FREVJUk9TPC94QmFpcnJvPjxjTXVuPjM1MjU5MDQ8L2NNdW4+
          PHhNdW4+SlVORElBSTwveE11bj48VUY+U1A8L1VGPjxDRVA+MTMyMTIyNTU8
          L0NFUD48Y1BhaXM+MTA1ODwvY1BhaXM+PHhQYWlzPkJSQVNJTDwveFBhaXM+
          PGZvbmU+OTk5OTk5OTk8L2ZvbmU+PC9lbmRlckRlc3Q+PGluZElFRGVzdD4x
          PC9pbmRJRURlc3Q+PElFPjQwNzA1NjIyODExMzwvSUU+PGVtYWlsPnRlc3Rl
          QG5leGFhcy5jb20uYnI8L2VtYWlsPjwvZGVzdD48ZGV0IG5JdGVtPSIxIj48
          cHJvZD48Y1Byb2Q+MTIzNDU2PC9jUHJvZD48Y0VBTj5TRU0gR1RJTjwvY0VB
          Tj48eFByb2Q+TklUUk9HRU5JTyBDSUwgNTBMIDEwTTM8L3hQcm9kPjxOQ00+
          MjgwNDMwMDA8L05DTT48Q0ZPUD41MTA0PC9DRk9QPjx1Q29tPk0zPC91Q29t
          PjxxQ29tPjY8L3FDb20+PHZVbkNvbT4xNi40OTQ4NTwvdlVuQ29tPjx2UHJv
          ZD45OC45NzwvdlByb2Q+PGNFQU5UcmliPlNFTSBHVElOPC9jRUFOVHJpYj48
          dVRyaWI+TTM8L3VUcmliPjxxVHJpYj42PC9xVHJpYj48dlVuVHJpYj4xNi40
          OTQ4NTwvdlVuVHJpYj48aW5kVG90PjE8L2luZFRvdD48eFBlZD5TMDEwMDI0
          OTEzNDwveFBlZD48bkl0ZW1QZWQ+MTwvbkl0ZW1QZWQ+PC9wcm9kPjxpbXBv
          c3RvPjx2VG90VHJpYj4yNjkuNjQ8L3ZUb3RUcmliPjxJQ01TPjxJQ01TMDA+
          PG9yaWc+Mzwvb3JpZz48Q1NUPjAwPC9DU1Q+PG1vZEJDPjM8L21vZEJDPjx2
          QkM+OTg5LjY5PC92QkM+PHBJQ01TPjE4LjAwMDA8L3BJQ01TPjx2SUNNUz4x
          NzguMTQ8L3ZJQ01TPjwvSUNNUzAwPjwvSUNNUz48SVBJPjxjU2Vsbz4wPC9j
          U2Vsbz48cVNlbG8+MDwvcVNlbG8+PGNFbnE+OTk5PC9jRW5xPjxJUElOVD48
          Q1NUPjAxPC9DU1Q+PC9JUElOVD48L0lQST48UElTPjxQSVNBbGlxPjxDU1Q+
          MDE8L0NTVD48dkJDPjk4OS42OTwvdkJDPjxwUElTPjEuNjUwMDwvcFBJUz48
          dlBJUz4xNi4zMDwvdlBJUz48L1BJU0FsaXE+PC9QSVM+PENPRklOUz48Q09G
          SU5TQWxpcT48Q1NUPjAxPC9DU1Q+PHZCQz45ODkuNjk8L3ZCQz48cENPRklO
          Uz43LjYwMDA8L3BDT0ZJTlM+PHZDT0ZJTlM+NzUuMjA8L3ZDT0ZJTlM+PC9D
          T0ZJTlNBbGlxPjwvQ09GSU5TPjwvaW1wb3N0bz48L2RldD48dG90YWw+PElD
          TVNUb3Q+PHZCQz45ODkuNjk8L3ZCQz48dklDTVM+MTc4LjE0PC92SUNNUz48
          dklDTVNEZXNvbj4wLjAwPC92SUNNU0Rlc29uPjx2RkNQVUZEZXN0PjAuMDA8
          L3ZGQ1BVRkRlc3Q+PHZJQ01TVUZEZXN0PjAuMDA8L3ZJQ01TVUZEZXN0Pjx2
          SUNNU1VGUmVtZXQ+MC4wMDwvdklDTVNVRlJlbWV0Pjx2RkNQPjAuMDA8L3ZG
          Q1A+PHZCQ1NUPjAuMDA8L3ZCQ1NUPjx2U1Q+MC4wMDwvdlNUPjx2RkNQU1Q+
          MC4wMDwvdkZDUFNUPjx2RkNQU1RSZXQ+MC4wMDwvdkZDUFNUUmV0Pjx2UHJv
          ZD45OC45NzwvdlByb2Q+PHZGcmV0ZT4wLjAwPC92RnJldGU+PHZTZWc+MC4w
          MDwvdlNlZz48dkRlc2M+MC4wMDwvdkRlc2M+PHZJST4wLjAwPC92SUk+PHZJ
          UEk+MC4wMDwvdklQST48dklQSURldm9sPjAuMDA8L3ZJUElEZXZvbD48dlBJ
          Uz4xNi4zMDwvdlBJUz48dkNPRklOUz43NS4yMDwvdkNPRklOUz48dk91dHJv
          PjAuMDA8L3ZPdXRybz48dk5GPjk4Ljk3PC92TkY+PHZUb3RUcmliPjI2OS42
          NDwvdlRvdFRyaWI+PC9JQ01TVG90PjwvdG90YWw+PHRyYW5zcD48bW9kRnJl
          dGU+OTwvbW9kRnJldGU+PHZvbD48cVZvbD4xPC9xVm9sPjxlc3A+Q2lsaW5k
          cm88L2VzcD48bWFyY2E+MDwvbWFyY2E+PG5Wb2w+MDwvblZvbD48cGVzb0w+
          NjYuNzgwPC9wZXNvTD48cGVzb0I+NDUwLjc4MDwvcGVzb0I+PC92b2w+PC90
          cmFuc3A+PHBhZz48ZGV0UGFnPjx0UGFnPjAxPC90UGFnPjx2UGFnPjUwLjAw
          PC92UGFnPjwvZGV0UGFnPjxkZXRQYWc+PHRQYWc+MDM8L3RQYWc+PHZQYWc+
          OC45NzwvdlBhZz48L2RldFBhZz48ZGV0UGFnPjx0UGFnPjAzPC90UGFnPjx2
          UGFnPjQwLjAwPC92UGFnPjxjYXJkPjx0cEludGVncmE+MTwvdHBJbnRlZ3Jh
          PjxDTlBKPjk5OTk5OTk5OTk5OTk5PC9DTlBKPjx0QmFuZD4wMjwvdEJhbmQ+
          PGNBdXQ+OTk5OTk5OTk5OTk5OTk5OTk5OTk8L2NBdXQ+PC9jYXJkPjwvZGV0
          UGFnPjwvcGFnPjxpbmZBZGljPjxpbmZBZEZpc2NvPkNsaWVudGU6IDExMi4g
          UmVtZXNzYTogMDAwMDYxMDc0LTAxMjM8L2luZkFkRmlzY28+PC9pbmZBZGlj
          PjwvaW5mTkZlPjxTaWduYXR1cmUgeG1sbnM9Imh0dHA6Ly93d3cudzMub3Jn
          LzIwMDAvMDkveG1sZHNpZyMiPjxTaWduZWRJbmZvPjxDYW5vbmljYWxpemF0
          aW9uTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvVFIvMjAw
          MS9SRUMteG1sLWMxNG4tMjAwMTAzMTUiPjwvQ2Fub25pY2FsaXphdGlvbk1l
          dGhvZD48U2lnbmF0dXJlTWV0aG9kIEFsZ29yaXRobT0iaHR0cDovL3d3dy53
          My5vcmcvMjAwMC8wOS94bWxkc2lnI3JzYS1zaGExIj48L1NpZ25hdHVyZU1l
          dGhvZD48UmVmZXJlbmNlIFVSST0iI05GZTM1MTkwMjIyNzY5NTMwMDAwMTMx
          NTUwMDAwMDAwMDAxMDAxNTU4Mjc3NjAzIj48VHJhbnNmb3Jtcz48VHJhbnNm
          b3JtIEFsZ29yaXRobT0iaHR0cDovL3d3dy53My5vcmcvMjAwMC8wOS94bWxk
          c2lnI2VudmVsb3BlZC1zaWduYXR1cmUiPjwvVHJhbnNmb3JtPjxUcmFuc2Zv
          cm0gQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy14
          bWwtYzE0bi0yMDAxMDMxNSI+PC9UcmFuc2Zvcm0+PC9UcmFuc2Zvcm1zPjxE
          aWdlc3RNZXRob2QgQWxnb3JpdGhtPSJodHRwOi8vd3d3LnczLm9yZy8yMDAw
          LzA5L3htbGRzaWcjc2hhMSI+PC9EaWdlc3RNZXRob2Q+PERpZ2VzdFZhbHVl
          PkZiY1RiWkVwZG9KYm95bFFKWHNoZ3k2QlZucz08L0RpZ2VzdFZhbHVlPjwv
          UmVmZXJlbmNlPjwvU2lnbmVkSW5mbz48U2lnbmF0dXJlVmFsdWU+RklHTmVm
          ejl6TnJuOG95Zm5QSGdwVlo2d20yMkVUM3NsZUxGdHJhL2hCKzIva2JJTUI0
          RjNqcnNlUkhHaSt2TURiWTF3dUtKSytxUVJSUXpRVnl5QlhER21VNnF5MUs3
          bklWOXd2cGw5WExaTDhaMWl4dS9SVW1mQWdxK1RHUExNQ0lWa1RUWkdMb2JZ
          OUN0WFczOGJGN29qR2t1MVZTK2R2b1pwSkdiTVdoOFQ2RGxyYjZYbExweERP
          TXlhVjlOeHVqVnNHS0l5RnZpZUwvNG9DdGhiZVk1UFhUOCtHNzEyWDZpVnl6
          Vi9QYVFac2hhUnNadmcxWEg5ZUhlWTlhOE1ZRGt3dmcvYVQwQkJaU3ZnajNH
          bUM4RzNJV1FHUUNrN2QxSkhybVVLaUxNYVIwb2xVZit3SUJOempVZWllM0dW
          akRMZGk1ZEpDVHk0eFBsTGJ5d2NBPT08L1NpZ25hdHVyZVZhbHVlPjxLZXlJ
          bmZvPjxYNTA5RGF0YT48WDUwOUNlcnRpZmljYXRlPk1JSUhyRENDQlpTZ0F3
          SUJBZ0lJRWQ0WUJ3UllwZkF3RFFZSktvWklodmNOQVFFTEJRQXdnWWt4Q3pB
          SkJnTlZCQVlUQWtKU01STXdFUVlEVlFRS0V3cEpRMUF0UW5KaGMybHNNVFF3
          TWdZRFZRUUxFeXRCZFhSdmNtbGtZV1JsSUVObGNuUnBabWxqWVdSdmNtRWdV
          bUZwZWlCQ2NtRnphV3hsYVhKaElIWXlNUkl3RUFZRFZRUUxFd2xCUXlCVFQw
          eFZWRWt4R3pBWkJnTlZCQU1URWtGRElGTlBURlZVU1NCTmRXeDBhWEJzWVRB
          ZUZ3MHhPREEzTURReU1UVTJOVFphRncweE9UQTNNRFF4T0RFek1EQmFNSUhW
          TVFzd0NRWURWUVFHRXdKQ1VqRVRNQkVHQTFVRUNoTUtTVU5RTFVKeVlYTnBi
          REUwTURJR0ExVUVDeE1yUVhWMGIzSnBaR0ZrWlNCRFpYSjBhV1pwWTJGa2Iz
          SmhJRkpoYVhvZ1FuSmhjMmxzWldseVlTQjJNakVTTUJBR0ExVUVDeE1KUVVN
          Z1UwOU1WVlJKTVJzd0dRWURWUVFMRXhKQlF5QlRUMHhWVkVrZ1RYVnNkR2x3
          YkdFeEdqQVlCZ05WQkFzVEVVTmxjblJwWm1sallXUnZJRkJLSUVFeE1TNHdM
          QVlEVlFRREV5VlFSRlpGVGtRZ1ZFVkRUazlNVDBkSlFTQk1WRVJCT2pJeU56
          WTVOVE13TURBd01UTXhNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUZBQU9DQVE4
          QU1JSUJDZ0tDQVFFQTBnWDgvbEV0bFFNZ1Fnc3QwZkxNQzV4R3UwbGZ1L0dZ
          RWk4M0oyVGtWaVUvWjdpL0QyN1ZhYTRwcXZwZElqVm4zTytiZzdVdFBPSVBM
          NHFMTDE3dnJ2SWI1V0FtNzJIUDgvaFRoRkZ1VjV3NjZITmgwNEd0TEF1NDhR
          empaVk4yU2FYdElWeldSczM2YnZFNUdSRzE4bHdqOWV6NlRiZjhaN3p6d2d2
          cWRWaC9nNWI5NU9vaVRTMkhmV1Z1Ry9QY2xEK1hjZHZtcklsWDlWZVhXaWxr
          ZjAwd2l2ajdjMkJmMmZZY1RWTUg5OUwyaXVDcHhSV0lEL3JhTWlpb1o1VkI5
          cko3THF1aVIvdFRDWVBheWVMMjhHZGtBTTRwQUg0WVJqZFF1NjBmS0hDMmhK
          TnhFSWYrUGhZeTBYRFQybENsa2M1elFFdVd2ZjJyK2dtc1oyQ1Ewd0lEQVFB
          Qm80SUN5RENDQXNRd1ZBWUlLd1lCQlFVSEFRRUVTREJHTUVRR0NDc0dBUVVG
          QnpBQ2hqaG9kSFJ3T2k4dlkyTmtMbUZqYzI5c2RYUnBMbU52YlM1aWNpOXNZ
          M0l2WVdNdGMyOXNkWFJwTFcxMWJIUnBjR3hoTFhZeExuQTNZakFkQmdOVkhR
          NEVGZ1FVVE1oa2lReFBIY1hhZERSUzFIRjdNV1VJckRvd0NRWURWUjBUQkFJ
          d0FEQWZCZ05WSFNNRUdEQVdnQlExcmpFVTlsN1NlazlZL2pTb0dtZVhDc1Ni
          QnpCZUJnTlZIU0FFVnpCVk1GTUdCbUJNQVFJQkpqQkpNRWNHQ0NzR0FRVUZC
          d0lCRmp0b2RIUndjem92TDJOalpDNWhZM052YkhWMGFTNWpiMjB1WW5JdlpH
          OWpjeTlrY0dNdFlXTXRjMjlzZFhScExXMTFiSFJwY0d4aExuQmtaakNCM2dZ
          RFZSMGZCSUhXTUlIVE1ENmdQS0E2aGpob2RIUndPaTh2WTJOa0xtRmpjMjlz
          ZFhScExtTnZiUzVpY2k5c1kzSXZZV010YzI5c2RYUnBMVzExYkhScGNHeGhM
          WFl4TG1OeWJEQS9vRDJnTzRZNWFIUjBjRG92TDJOalpESXVZV056YjJ4MWRH
          a3VZMjl0TG1KeUwyeGpjaTloWXkxemIyeDFkR2t0YlhWc2RHbHdiR0V0ZGpF
          dVkzSnNNRkNnVHFCTWhrcG9kSFJ3T2k4dmNtVndiM05wZEc5eWFXOHVhV053
          WW5KaGMybHNMbWR2ZGk1aWNpOXNZM0l2UVVOVFQweFZWRWt2WVdNdGMyOXNk
          WFJwTFcxMWJIUnBjR3hoTFhZeExtTnliREFPQmdOVkhROEJBZjhFQkFNQ0Jl
          QXdIUVlEVlIwbEJCWXdGQVlJS3dZQkJRVUhBd0lHQ0NzR0FRVUZCd01FTUlH
          d0JnTlZIUkVFZ2Fnd2dhV0JFMkp5ZFc1dlFIQmtkbVZ1WkM1amIyMHVZbktn
          SUFZRllFd0JBd0tnRnhNVlFsSlZUazhnVmtWTVQxTlBJRVpGVWxKRlNWSkJv
          QmtHQldCTUFRTURvQkFURGpJeU56WTVOVE13TURBd01UTXhvRGdHQldCTUFR
          TUVvQzhUTFRJek1EZ3hPVGcxTURBMk5ESXlNakl4Tnpjd01EQXdNREF3TURB
          d01EQXdNREF3TURBd01EQXdNREF3TUtBWEJnVmdUQUVEQjZBT0V3d3dNREF3
          TURBd01EQXdNREF3RFFZSktvWklodmNOQVFFTEJRQURnZ0lCQUR4ek12YWpT
          bFVRMkd4cko5SU96SXB6V0V2cDhUb003MXpqclhCK2R3VnMxRDVjUlFBOGh2
          bzAxeHdaNDVzNlBNbW1qSng4WElSUVdCM2RMVi82bUtwTkdDY1BXN2d1bit4
          M1ZMa1JMVG9mUW1WVnJxaldUeitZdW14ejk0eHdSMmtKR2g2dTNueHY5MmhU
          aVhkKzd2UmZNUGNzQU8wVnR2aFg3eHF0Y2JPdVVyZmU4UW5FRlE2WmI2aE1a
          UVBtSVE1K1dWY2R5TzdVZytZR1NZeWZ2UHhySWpBQk5XcGpuTUZJUEZwcTgv
          alhlbFhzVXlvbThTc3hOdGJ4OThLc0dLd3Q1ZkRPb2NvdnFGNmpKOHpzak1u
          L2pZV2lhTkhRMnBLbzNFbWl0YW82b2JCT1hGdU5xV2M1VXo4V01tK2lUTXlK
          bjh4b3R6cmhrYTZjNVl1SjBieEovcFBsS0pBT2tEVFZZb1RBMTkwM1gvMG51
          blQyZDdJMVYzRDRNYmxvMWxDV1VnakZuVENtdlJGZmhoQzh1TXdYc2M5Ukpr
          Vm1UeCs3cU9oWXpDRkVKTnFLb0FvZUJJTHZOWXltRTUxaG1tbmFhTEw0QkJu
          UmhHZllIRUhOWGRrOU81MlBNOWVXSHZ5c0xlWEpMRjBXVHh0L0V5QThxbGtZ
          M2JLN1Z5VllWM2tOVWRPeHJ4NTA3VjZRSVVTYTdXc05janprM3JBN0U1dklR
          bkNLR2ZlbVJoOEFSc1dIaGltVG4yYkQ2bGhXYlBMN0ZkWWo4eVlFMCt0T2V3
          OHhQVXQ1Y2pDekJhZDBuZXFvNkkzVTUyaEV4bWhUVUNMcVk1RG5PeGhWRHNt
          WS9pUUtNalBXR3lETUtkTGJCbFozelYyeE5EMktlcVlVblRxYlduNGk3ampp
          PC9YNTA5Q2VydGlmaWNhdGU+PC9YNTA5RGF0YT48L0tleUluZm8+PC9TaWdu
          YXR1cmU+PC9ORmU+PC9lbnZpTkZlPg==",
          "nfces": [
            {
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
                  "unidade_comercial": "M3",
                  "unidade_tributaria": "M3",
                  "valor_desconto": 0.0,
                  "valor_frete": 0.0,
                  "valor_seguro": 0.0,
                  "valor_total_produto": "98.97",
                  "valor_unitario_comercial": 16.49485,
                  "valor_unitario_tributario": 16.49485,
                  "tributacao": {
                    "valor_aproximado_total": 269.64,
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
                      "aliquota_st": 0.0,
                      "situacao_tributaria": "01",
                      "valor_base_calculo": 989.69,
                      "valor_base_calculo_st": 0.0,
                      "valor_pis": 16.3,
                      "valor_pis_st": 0.0
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


EXEMPLO DE RESPOSTA

{
  "nfce_batch": {
    "id": 1099,
    "key": null,
    "nfces": [
      {
        "id": 10990,
        "status": "processing"
      }
    ]
  }
}
```
