

# Projeto Vacinação Postman

# Consumindo API de Vacinação de Covid-19 no Brasil

#### Fonte Oficial: https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao

#### Dicionário de Dados: https://opendatasus.saude.gov.br/dataset/b772ee55-07cd-44d8-958f-b12edd004e0b/resource/38ead83d-b115-4219-852e-7244792bc311/download/dicionario-de-dados-vacinacao.pdf

#### Manual para Consumo de API: https://opendatasus.saude.gov.br/dataset/b772ee55-07cd-44d8-958f-b12edd004e0b/resource/5916b3a4-81e7-4ad5-adb6-b884ff198dc1/download/manual_api_vacina_covid-19.pdf

![vacinacao_postman](https://github.com/heliton1986/Projeto_Vacinacao_Postman/assets/45739569/6887e6e0-1166-4cef-98c8-72647272b99b)

In [ ]:

```
!conda install requests -y
```

## Usando Postman

In [1]:

```
import requests
```

In [2]:

```
url = "https://imunizacao-es.saude.gov.br/_search"
```

In [3]:

```
payload={}
headers = {
  'Authorization': 'Basic aW11bml6YWNhb19wdWJsaWM6cWx0bzV0JjdyX0ArI1Rsc3RpZ2k=',
  'Cookie': 'ELASTIC-PROD=1622397687.657.1874.569037'
}
```

In [4]:

```
response = requests.request("GET", url, headers=headers, data=payload)
```

In [5]:

```
print(response.text)
{"took":10,"timed_out":false,"_shards":{"total":3,"successful":3,"skipped":0,"failed":0},"hits":{"total":{"value":10000,"relation":"gte"},"max_score":1.0,"hits":[{"_index":"desc-imunizacao","_type":"_doc","_id":"15bc4660-e65a-4d86-857e-697311978933-i0b0","_score":1.0,"_source":{"sistema_origem":"VACIVIDA","estabelecimento_valor":"2789132","vacina_categoria_codigo":"2","vacina_codigo":"85","paciente_dataNascimento":"1969-01-22","paciente_endereco_nmPais":"BRASIL","estabelecimento_municipio_codigo":"355030","vacina_categoria_nome":"Faixa Etária","paciente_endereco_nmMunicipio":"GUARULHOS","vacina_lote":"213VCD010VA","paciente_endereco_coPais":"10","vacina_nome":"Vacina Covid-19 - Covishield","paciente_endereco_uf":"SP","paciente_idade":52,"paciente_id":"6c62b4b30f72b5dea26d914c5ede09ec6d75e4bbe8f01bac4242a7cdc10f14c3","vacina_grupoAtendimento_nome":"Pessoas de 60 a 64 anos","vacina_fabricante_nome":"ASTRAZENECA/OXFORD","paciente_endereco_cep":"07083","vacina_dataAplicacao":"2021-04-29T00:00:00.000Z","estabelecimento_uf":"SP","vacina_grupoAtendimento_codigo":"000201","paciente_endereco_coIbgeMunicipio":"351880","estabelecimento_razaoSocial":"PREFEITURA DO MUNICIPIO DE SAO PAULO","@timestamp":"2021-05-
```

## Usando Requests Diretamente com Python

In [6]:

```
import requests
from requests.auth import HTTPBasicAuth
import pandas as pd
```

In [7]:

```
url = 'https://imunizacao-es.saude.gov.br/_search'
```

In [8]:

```
response = requests.get(url, auth=HTTPBasicAuth('imunizacao_public', 'qlto5t&7r_@+#Tlstigi'))
```

## Visualizando em Texto

In [9]:

```
response.text
```

Out[9]:

```
'{"took":6,"timed_out":false,"_shards":{"total":3,"successful":3,"skipped":0,"failed":0},"hits":{"total":{"value":10000,"relation":"gte"},"max_score":1.0,"hits":[{"_index":"desc-imunizacao","_type":"_doc","_id":"15bc4660-e65a-4d86-857e-697311978933-i0b0","_score":1.0,"_source":{"sistema_origem":"VACIVIDA","estabelecimento_valor":"2789132","vacina_categoria_codigo":"2","vacina_codigo":"85","paciente_dataNascimento":"1969-01-22","paciente_endereco_nmPais":"BRASIL","estabelecimento_municipio_codigo":"355030","vacina_categoria_nome":"Faixa Etária","paciente_endereco_nmMunicipio":"GUARULHOS","vacina_lote":"213VCD010VA","paciente_endereco_coPais":"10","vacina_nome":"Vacina Covid-19 - Covishield","paciente_endereco_uf":"SP","paciente_idade":52,"paciente_id":"6c62b4b30f72b5dea26d914c5ede09ec6d75e4bbe8f01bac4242a7cdc10f14c3","vacina_grupoAtendimento_nome":"Pessoas de 60 a 64 anos","vacina_fabricante_nome":"ASTRAZENECA/OXFORD","paciente_endereco_cep":"07083","vacina_dataAplicacao":"2021-04-29T00:00:00.000Z","estabelecimento_uf":"SP","vacina_grupoAtendimento_codigo":"000201","paciente_endereco_coIbgeMunicipio":"351880","estabelecimento_razaoSocial":"PREFEITURA DO MUNICIPIO DE SAO PAULO","@timestamp":"2021-05-
```

## Visualizando em Json

In [10]:

```
vacina = response.json()
```

In [11]:

```
vacina
```

Out[11]:

```
{'took': 6,
 'timed_out': False,
 '_shards': {'total': 3, 'successful': 3, 'skipped': 0, 'failed': 0},
 'hits': {'total': {'value': 10000, 'relation': 'gte'},
  'max_score': 1.0,
  'hits': [{'_index': 'desc-imunizacao',
    '_type': '_doc',
    '_id': '15bc4660-e65a-4d86-857e-697311978933-i0b0',
    '_score': 1.0,
    '_source': {'sistema_origem': 'VACIVIDA',
     'estabelecimento_valor': '2789132',
     'vacina_categoria_codigo': '2',
     'vacina_codigo': '85',
     'paciente_dataNascimento': '1969-01-22',
     'paciente_endereco_nmPais': 'BRASIL',
     'estabelecimento_municipio_codigo': '355030',
     'vacina_categoria_nome': 'Faixa Etária',
```

```
vacina['hits']['hits']
```

```
[{'_index': 'desc-imunizacao',
  '_type': '_doc',
  '_id': '15bc4660-e65a-4d86-857e-697311978933-i0b0',
  '_score': 1.0,
  '_source': {'sistema_origem': 'VACIVIDA',
   'estabelecimento_valor': '2789132',
   'vacina_categoria_codigo': '2',
   'vacina_codigo': '85',
   'paciente_dataNascimento': '1969-01-22',
   'paciente_endereco_nmPais': 'BRASIL',
   'estabelecimento_municipio_codigo': '355030',
   'vacina_categoria_nome': 'Faixa Etária',
   'paciente_endereco_nmMunicipio': 'GUARULHOS',
   'vacina_lote': '213VCD010VA',
   'paciente_endereco_coPais': '10',
   'vacina_nome': 'Vacina Covid-19 - Covishield',
   'paciente_endereco_uf': 'SP',
   'paciente_idade': 52,
```

## Usando o Pandas para Normalizar o Json

In [14]:

```
pd.json_normalize(vacina['hits']['hits'])
```

## Criando um Dataframe

In [15]:

```
df_vacina = pd.json_normalize(vacina['hits']['hits'])
```

In [16]:

```
df_vacina
```

Out[16]:

|      |          _index | _type |                                       _id | _score | _source.sistema_origem | _source.estabelecimento_valor | _source.vacina_categoria_codigo | _source.vacina_codigo | _source.paciente_dataNascimento | _source.paciente_endereco_nmPais |  ... |         _source.estalecimento_noFantasia | _source.paciente_nacionalidade_enumNacionalidade | _source.paciente_enumSexoBiologico | _source.vacina_descricao_dose | _source.data_importacao_rnds | _source.estabelecimento_municipio_nome | _source.@version | _source.id_sistema_origem | _source.paciente_racaCor_codigo |                       _source.document_id |
| ---: | --------------: | ----: | ----------------------------------------: | -----: | ---------------------: | ----------------------------: | ------------------------------: | --------------------: | ------------------------------: | -------------------------------: | ---: | ---------------------------------------: | -----------------------------------------------: | ---------------------------------: | ----------------------------: | ---------------------------: | -------------------------------------: | ---------------: | ------------------------: | ------------------------------: | ----------------------------------------: |
|    0 | desc-imunizacao |  _doc | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |    1.0 |               VACIVIDA |                       2789132 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                UBS V OLIMPIA MAX PERLMAN |                                                B |                                  M |                       1ª Dose |          2021-04-29 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |
|    1 | desc-imunizacao |  _doc | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |    1.0 |               VACIVIDA |                       2752131 |                               9 |                    86 |                      1969-01-22 |                           BRASIL |  ... |     SAE E DSTAIDS IPIRANGA JOSE F ARAUJO |                                                B |                                  M |                       2ª Dose |          2021-04-30 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |
|    2 | desc-imunizacao |  _doc | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |    1.0 |               VACIVIDA |                       2064537 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                              PAMO ESTIVA |                                                B |                                  M |                       1ª Dose |          2021-04-28 03:00:00 |                                TAUBATE |                1 |                     18262 |                              03 | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |
|    3 | desc-imunizacao |  _doc | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |    1.0 |               VACIVIDA |                       2746522 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                      UBS CAUCAIA DO ALTO |                                                B |                                  M |                       1ª Dose |          2021-05-03 03:00:00 |                                  COTIA |                1 |                     18262 |                              03 | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |
|    4 | desc-imunizacao |  _doc | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |    1.0 |               VACIVIDA |                       2705125 |                               2 |                    86 |                      1969-01-22 |                           BRASIL |  ... | UNIDADE BASICA DE SAUDE SARAPIRANGA PACS |                                                B |                                  M |                       2ª Dose |          2021-04-29 03:00:00 |                                JUNDIAI |                1 |                     18262 |                              03 | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |
|    5 | desc-imunizacao |  _doc | 4f2d0d67-656c-406a-a85c-1ff7d9837082-i0b0 |    1.0 |               VACIVIDA |                       2788152 |                               2 |                    86 |                      1969-01-22 |                           BRASIL |  ... |                     UBS JD NOVE DE JULHO |                                                B |                                  M |                       2ª Dose |          2021-04-12 03:04:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 4f2d0d67-656c-406a-a85c-1ff7d9837082-i0b0 |
|    6 | desc-imunizacao |  _doc | bf3d41f0-e5c4-4aac-9778-be29c0b59c21-i0b0 |    1.0 |               VACIVIDA |                       2788012 |                               9 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                    UBS CONJUNTO DO IPESP |                                                B |                                  M |                       1ª Dose |          2021-05-03 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | bf3d41f0-e5c4-4aac-9778-be29c0b59c21-i0b0 |
|    7 | desc-imunizacao |  _doc | cebe11a9-5370-4fdf-90c6-4251c2e75e85-i0b0 |    1.0 |               VACIVIDA |                       2788950 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |         AMA UBS INTEGRADA VILA GUILHERME |                                                B |                                  M |                       1ª Dose |          2021-04-23 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | cebe11a9-5370-4fdf-90c6-4251c2e75e85-i0b0 |
|    8 | desc-imunizacao |  _doc | fe5e7126-fe0e-469b-b2e6-7680823a8fa7-i0b0 |    1.0 |               VACIVIDA |                       2788012 |                               8 |                    86 |                      1969-01-22 |                           BRASIL |  ... |                    UBS CONJUNTO DO IPESP |                                                B |                                  M |                       2ª Dose |          2021-05-03 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | fe5e7126-fe0e-469b-b2e6-7680823a8fa7-i0b0 |
|    9 | desc-imunizacao |  _doc | bd24eb9b-3334-4d28-b3b1-9e763140fc3e-i0b0 |    1.0 |               VACIVIDA |                       2788853 |                               8 |                    86 |                      1969-01-22 |                           BRASIL |  ... |                       UBS VILA ESPANHOLA |                                                B |                                  M |                       2ª Dose |          2021-05-03 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | bd24eb9b-3334-4d28-b3b1-9e763140fc3e-i0b0 |

10 rows × 39 columns

## Puxando API com Postman de 10.000 Registros

In [17]:

```
import requests
import json
import pandas as pd
import numpy as np

url = "https://imunizacao-es.saude.gov.br/_search"

payload = json.dumps({
  "size": 10000
})
headers = {
  'Authorization': 'Basic aW11bml6YWNhb19wdWJsaWM6cWx0bzV0JjdyX0ArI1Rsc3RpZ2k=',
  'Content-Type': 'application/json',
  'Cookie': 'ELASTIC-PROD=1622397687.657.1874.569037'
}

response = requests.request("POST", url, headers=headers, data=payload)
```

In [18]:

```
vacina = response.json()
```

In [19]:

```
df = pd.json_normalize(vacina['hits']['hits'])
```

In [20]:

```
df.head()
```

Out[20]:

|      |          _index | _type |                                       _id | _score | _source.sistema_origem | _source.estabelecimento_valor | _source.vacina_categoria_codigo | _source.vacina_codigo | _source.paciente_dataNascimento | _source.paciente_endereco_nmPais |  ... |         _source.estalecimento_noFantasia | _source.paciente_nacionalidade_enumNacionalidade | _source.paciente_enumSexoBiologico | _source.vacina_descricao_dose | _source.data_importacao_rnds | _source.estabelecimento_municipio_nome | _source.@version | _source.id_sistema_origem | _source.paciente_racaCor_codigo |                       _source.document_id |
| ---: | --------------: | ----: | ----------------------------------------: | -----: | ---------------------: | ----------------------------: | ------------------------------: | --------------------: | ------------------------------: | -------------------------------: | ---: | ---------------------------------------: | -----------------------------------------------: | ---------------------------------: | ----------------------------: | ---------------------------: | -------------------------------------: | ---------------: | ------------------------: | ------------------------------: | ----------------------------------------: |
|    0 | desc-imunizacao |  _doc | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |    1.0 |               VACIVIDA |                       2789132 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                UBS V OLIMPIA MAX PERLMAN |                                                B |                                  M |                       1ª Dose |          2021-04-29 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |
|    1 | desc-imunizacao |  _doc | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |    1.0 |               VACIVIDA |                       2752131 |                               9 |                    86 |                      1969-01-22 |                           BRASIL |  ... |     SAE E DSTAIDS IPIRANGA JOSE F ARAUJO |                                                B |                                  M |                       2ª Dose |          2021-04-30 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |
|    2 | desc-imunizacao |  _doc | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |    1.0 |               VACIVIDA |                       2064537 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                              PAMO ESTIVA |                                                B |                                  M |                       1ª Dose |          2021-04-28 03:00:00 |                                TAUBATE |                1 |                     18262 |                              03 | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |
|    3 | desc-imunizacao |  _doc | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |    1.0 |               VACIVIDA |                       2746522 |                               2 |                    85 |                      1969-01-22 |                           BRASIL |  ... |                      UBS CAUCAIA DO ALTO |                                                B |                                  M |                       1ª Dose |          2021-05-03 03:00:00 |                                  COTIA |                1 |                     18262 |                              03 | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |
|    4 | desc-imunizacao |  _doc | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |    1.0 |               VACIVIDA |                       2705125 |                               2 |                    86 |                      1969-01-22 |                           BRASIL |  ... | UNIDADE BASICA DE SAUDE SARAPIRANGA PACS |                                                B |                                  M |                       2ª Dose |          2021-04-29 03:00:00 |                                JUNDIAI |                1 |                     18262 |                              03 | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |

5 rows × 39 columns

## Renomeando Algumas Colunas

In [21]:

```
df.rename(columns= {'_index': 'Índice',
                    '_type': 'Tipo',
                    '_id': 'Id',
                    '_score': 'Score',
                    '_source.sistema_origem': 'Sistema de Origem',
                    '_source.estabelecimento_valor': 'Código CNES de Vacinação',
                    '_source.vacina_categoria_codigo': 'Código da Categoria',
                    '_source.vacina_codigo': 'Código da Vacina',
                    '_source.paciente_dataNascimento': 'Data de Nascimento',
                    '_source.paciente_endereco_nmPais': 'País do Paciente'}, inplace=True)
```

In [22]:

```
df.head()
```

Out[22]:

|      |          Índice | Tipo |                                        Id | Score | Sistema de Origem | Código CNES de Vacinação | Código da Categoria | Código da Vacina | Data de Nascimento | País do Paciente |  ... |         _source.estalecimento_noFantasia | _source.paciente_nacionalidade_enumNacionalidade | _source.paciente_enumSexoBiologico | _source.vacina_descricao_dose | _source.data_importacao_rnds | _source.estabelecimento_municipio_nome | _source.@version | _source.id_sistema_origem | _source.paciente_racaCor_codigo |                       _source.document_id |
| ---: | --------------: | ---: | ----------------------------------------: | ----: | ----------------: | -----------------------: | ------------------: | ---------------: | -----------------: | ---------------: | ---: | ---------------------------------------: | -----------------------------------------------: | ---------------------------------: | ----------------------------: | ---------------------------: | -------------------------------------: | ---------------: | ------------------------: | ------------------------------: | ----------------------------------------: |
|    0 | desc-imunizacao | _doc | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |   1.0 |          VACIVIDA |                  2789132 |                   2 |               85 |         1969-01-22 |           BRASIL |  ... |                UBS V OLIMPIA MAX PERLMAN |                                                B |                                  M |                       1ª Dose |          2021-04-29 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 15bc4660-e65a-4d86-857e-697311978933-i0b0 |
|    1 | desc-imunizacao | _doc | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |   1.0 |          VACIVIDA |                  2752131 |                   9 |               86 |         1969-01-22 |           BRASIL |  ... |     SAE E DSTAIDS IPIRANGA JOSE F ARAUJO |                                                B |                                  M |                       2ª Dose |          2021-04-30 03:00:00 |                              SAO PAULO |                1 |                     18262 |                              03 | 74e4131f-ea0b-4e23-9d52-a8a44e212e2a-i0b0 |
|    2 | desc-imunizacao | _doc | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |   1.0 |          VACIVIDA |                  2064537 |                   2 |               85 |         1969-01-22 |           BRASIL |  ... |                              PAMO ESTIVA |                                                B |                                  M |                       1ª Dose |          2021-04-28 03:00:00 |                                TAUBATE |                1 |                     18262 |                              03 | 16d8dad5-bbf8-4b9f-98f5-aaa4790f3409-i0b0 |
|    3 | desc-imunizacao | _doc | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |   1.0 |          VACIVIDA |                  2746522 |                   2 |               85 |         1969-01-22 |           BRASIL |  ... |                      UBS CAUCAIA DO ALTO |                                                B |                                  M |                       1ª Dose |          2021-05-03 03:00:00 |                                  COTIA |                1 |                     18262 |                              03 | e7e3aa01-adba-491e-adba-4c36911dc633-i0b0 |
|    4 | desc-imunizacao | _doc | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |   1.0 |          VACIVIDA |                  2705125 |                   2 |               86 |         1969-01-22 |           BRASIL |  ... | UNIDADE BASICA DE SAUDE SARAPIRANGA PACS |                                                B |                                  M |                       2ª Dose |          2021-04-29 03:00:00 |                                JUNDIAI |                1 |                     18262 |                              03 | 59808724-12c2-4a55-98aa-a9f7edadfd4d-i0b0 |

5 rows × 39 columns

## Nomes das Colunas

In [23]:

```
df.columns
```

Out[23]:

```
Index(['Índice', 'Tipo', 'Id', 'Score', 'Sistema de Origem',
       'Código CNES de Vacinação', 'Código da Categoria', 'Código da Vacina',
       'Data de Nascimento', 'País do Paciente',
       '_source.estabelecimento_municipio_codigo',
       '_source.vacina_categoria_nome',
       '_source.paciente_endereco_nmMunicipio', '_source.vacina_lote',
       '_source.paciente_endereco_coPais', '_source.vacina_nome',
       '_source.paciente_endereco_uf', '_source.paciente_idade',
       '_source.paciente_id', '_source.vacina_grupoAtendimento_nome',
       '_source.vacina_fabricante_nome', '_source.paciente_endereco_cep',
       '_source.vacina_dataAplicacao', '_source.estabelecimento_uf',
       '_source.vacina_grupoAtendimento_codigo',
       '_source.paciente_endereco_coIbgeMunicipio',
       '_source.estabelecimento_razaoSocial', '_source.@timestamp',
       '_source.paciente_racaCor_valor', '_source.estalecimento_noFantasia',
       '_source.paciente_nacionalidade_enumNacionalidade',
       '_source.paciente_enumSexoBiologico', '_source.vacina_descricao_dose',
       '_source.data_importacao_rnds',
       '_source.estabelecimento_municipio_nome', '_source.@version',
       '_source.id_sistema_origem', '_source.paciente_racaCor_codigo',
       '_source.document_id'],
      dtype='object')
```

## Visualizando os Tipos de Dados das Colunas

In [24]:

```
df.dtypes
```

Out[24]:

```
Índice                                               object
Tipo                                                 object
Id                                                   object
Score                                               float64
Sistema de Origem                                    object
Código CNES de Vacinação                             object
Código da Categoria                                  object
Código da Vacina                                     object
Data de Nascimento                                   object
País do Paciente                                     object
_source.estabelecimento_municipio_codigo             object
_source.vacina_categoria_nome                        object
_source.paciente_endereco_nmMunicipio                object
_source.vacina_lote                                  object
_source.paciente_endereco_coPais                     object
_source.vacina_nome                                  object
_source.paciente_endereco_uf                         object
_source.paciente_idade                                int64
_source.paciente_id                                  object
_source.vacina_grupoAtendimento_nome                 object
_source.vacina_fabricante_nome                       object
_source.paciente_endereco_cep                        object
_source.vacina_dataAplicacao                         object
_source.estabelecimento_uf                           object
_source.vacina_grupoAtendimento_codigo               object
_source.paciente_endereco_coIbgeMunicipio            object
_source.estabelecimento_razaoSocial                  object
_source.@timestamp                                   object
_source.paciente_racaCor_valor                       object
_source.estalecimento_noFantasia                     object
_source.paciente_nacionalidade_enumNacionalidade     object
_source.paciente_enumSexoBiologico                   object
_source.vacina_descricao_dose                        object
_source.data_importacao_rnds                         object
_source.estabelecimento_municipio_nome               object
_source.@version                                     object
_source.id_sistema_origem                            object
_source.paciente_racaCor_codigo                      object
_source.document_id                                  object
dtype: object
```

In [25]:

```
df[['Data de Nascimento']]
```

Out[25]:

|      | Data de Nascimento |
| ---: | -----------------: |
|    0 |         1969-01-22 |
|    1 |         1969-01-22 |
|    2 |         1969-01-22 |
|    3 |         1969-01-22 |
|    4 |         1969-01-22 |
|  ... |                ... |
| 9995 |         1969-01-22 |
| 9996 |         1969-01-22 |
| 9997 |         1969-01-22 |
| 9998 |         1969-01-22 |
| 9999 |         1969-01-22 |

10000 rows × 1 columns

## Convertendo Object para Datetime

In [26]:

```
from datetime import datetime
```

In [27]:

```
df['Data de Nascimento'] = pd.to_datetime(df['Data de Nascimento'])
```

In [28]:

```
df[['Data de Nascimento']]
```

Out[28]:

|      | Data de Nascimento |
| ---: | -----------------: |
|    0 |         1969-01-22 |
|    1 |         1969-01-22 |
|    2 |         1969-01-22 |
|    3 |         1969-01-22 |
|    4 |         1969-01-22 |
|  ... |                ... |
| 9995 |         1969-01-22 |
| 9996 |         1969-01-22 |
| 9997 |         1969-01-22 |
| 9998 |         1969-01-22 |
| 9999 |         1969-01-22 |

10000 rows × 1 columns

In [29]:

```
df.dtypes
```

Out[29]:

```
Índice                                                      object
Tipo                                                        object
Id                                                          object
Score                                                      float64
Sistema de Origem                                           object
Código CNES de Vacinação                                    object
Código da Categoria                                         object
Código da Vacina                                            object
Data de Nascimento                                  datetime64[ns]
País do Paciente                                            object
_source.estabelecimento_municipio_codigo                    object
_source.vacina_categoria_nome                               object
_source.paciente_endereco_nmMunicipio                       object
_source.vacina_lote                                         object
_source.paciente_endereco_coPais                            object
_source.vacina_nome                                         object
_source.paciente_endereco_uf                                object
_source.paciente_idade                                       int64
_source.paciente_id                                         object
_source.vacina_grupoAtendimento_nome                        object
_source.vacina_fabricante_nome                              object
_source.paciente_endereco_cep                               object
_source.vacina_dataAplicacao                                object
_source.estabelecimento_uf                                  object
_source.vacina_grupoAtendimento_codigo                      object
_source.paciente_endereco_coIbgeMunicipio                   object
_source.estabelecimento_razaoSocial                         object
_source.@timestamp                                          object
_source.paciente_racaCor_valor                              object
_source.estalecimento_noFantasia                            object
_source.paciente_nacionalidade_enumNacionalidade            object
_source.paciente_enumSexoBiologico                          object
_source.vacina_descricao_dose                               object
_source.data_importacao_rnds                                object
_source.estabelecimento_municipio_nome                      object
_source.@version                                            object
_source.id_sistema_origem                                   object
_source.paciente_racaCor_codigo                             object
_source.document_id                                         object
dtype: object
```

## Criar um relatório em csv pela Pessoa de mais Idade e com 5.000 Registros

In [30]:

```
relatorio = df[['Sistema de Origem', 'Código CNES de Vacinação', 'Código da Categoria', 'Código da Vacina',
   'Data de Nascimento', 'País do Paciente']].sort_values('Data de Nascimento', ascending=True).head(5000)
```

In [31]:

```
relatorio
```

Out[31]:

|      | Sistema de Origem | Código CNES de Vacinação | Código da Categoria | Código da Vacina | Data de Nascimento | País do Paciente |
| ---: | ----------------: | -----------------------: | ------------------: | ---------------: | -----------------: | ---------------: |
| 2157 |          VACIVIDA |                  2745658 |                   3 |               85 |         1927-11-15 |           BRASIL |
| 3467 |          VACIVIDA |                  2030195 |                   2 |               85 |         1932-09-18 |           BRASIL |
| 1038 |       RN + Vacina |                  2407469 |                   9 |               86 |         1933-06-23 |           BRASIL |
| 1615 |         IDS Saúde |                  2491087 |                   9 |               85 |         1934-02-14 |           BRASIL |
| 3411 |         IDS Saúde |                  2401533 |                   2 |               86 |         1938-03-19 |           BRASIL |
|  ... |               ... |                      ... |                 ... |              ... |                ... |              ... |
| 8148 |          VACIVIDA |                  2787830 |                   2 |               86 |         1969-01-22 |           BRASIL |
| 8291 |          VACIVIDA |                  2788764 |                   9 |               86 |         1969-01-22 |           BRASIL |
| 8176 |          VACIVIDA |                  2064898 |                   2 |               86 |         1969-01-22 |           BRASIL |
| 8178 |          VACIVIDA |                  2038641 |                   2 |               86 |         1969-01-22 |           BRASIL |
| 8199 |          VACIVIDA |                  2025167 |                   9 |               85 |         1969-01-22 |           BRASIL |

5000 rows × 6 columns

## Exportando o Dataframe para um arquivo CSV

In [32]:

```
relatorio.to_csv('Vacina.csv')
```

## Ingestão do Relatório para o SGBD

In [33]:

```
from sqlalchemy import create_engine
```

In [34]:

```
engine = create_engine(
    'postgresql+psycopg2://postgres:root@localhost/vacinacao'
)
```

In [35]:

```
# Ingestão para o SGBD
relatorio.to_sql('vacinas', con=engine, index=False, if_exists='append')
```

![1](https://user-images.githubusercontent.com/45739569/120121382-83b7da80-c179-11eb-89a8-822f736a6cfe.PNG)

