# Sistema de Monitoramento da Missão Espacial Orion-X

Sistema desenvolvido em **Python** para simular o monitoramento e a análise de dados de uma missão espacial fictícia.

O projeto utiliza dados de sensores da missão **Orion-X** para identificar situações de risco, gerar análises automáticas, consultar informações externas através de uma API e produzir um relatório final em Excel.

## Sobre o projeto

Durante uma missão espacial, diferentes informações precisam ser monitoradas constantemente, como temperatura, energia disponível, nível de oxigênio, radiação e qualidade da comunicação.

Pensando nesse cenário, o **Sistema de Monitoramento da Missão Espacial Orion-X** foi desenvolvido para simular o processamento dessas informações utilizando Python e técnicas de análise de dados.

A aplicação lê uma base de dados em Excel, processa os registros utilizando **Pandas**, classifica automaticamente o nível de risco de cada registro e gera um novo arquivo Excel contendo análises, alertas e resumos da missão.

## Objetivos

O projeto tem como objetivo aplicar conceitos de programação e análise de dados em um cenário inspirado na indústria espacial.

Entre os principais recursos desenvolvidos estão:

* utilização de **tuplas, dicionários e laços de repetição**;
* leitura e manipulação de arquivos Excel;
* análise de dados utilizando **Pandas**;
* criação automática de indicadores;
* aplicação de filtros condicionais;
* classificação de níveis de risco;
* geração automática de alertas;
* integração com uma **API Web**;
* tratamento de erros com `try/except`;
* leitura e tratamento de dados em JSON;
* geração automática de um relatório final em Excel.

---

## Dados monitorados

A base da missão contém informações simuladas coletadas durante a operação da Orion-X.

Entre as principais variáveis monitoradas estão:

| Dado            | Descrição                                     |
| --------------- | --------------------------------------------- |
|  Temperatura | Temperatura interna registrada pelos sensores |
|  Energia      | Percentual de energia disponível              |
|  Oxigênio     | Nível de oxigênio disponível                  |
|  Radiação     | Nível de radiação detectado                   |
|  Comunicação  | Qualidade da comunicação da nave              |
|  Status      | Estado operacional da nave                    |
|  Localização  | Latitude, longitude e altitude                |

A base utilizada possui **20 registros de monitoramento**.

---

## Classificação de risco

Cada registro da missão é analisado automaticamente e recebe uma classificação:

### Normal

Os parâmetros monitorados encontram-se dentro das condições consideradas seguras.

### Atenção

Um ou mais indicadores estão fora da faixa ideal e precisam ser acompanhados.

### Crítico

Um ou mais parâmetros atingiram valores considerados perigosos e podem exigir intervenção.

A classificação considera os valores de:

* temperatura;
* energia;
* oxigênio;
* radiação;
* comunicação.

---

## Análise automática

Além da classificação de risco, o sistema gera automaticamente uma descrição dos problemas encontrados em cada registro.

Exemplo:

```text
Alerta: temperatura elevada, energia baixa.
```

Caso nenhum problema seja identificado:

```text
Parametros dentro da faixa segura.
```

Dessa forma, o relatório apresenta não apenas os valores dos sensores, mas também uma interpretação automática da situação.

---

## Índice de estabilidade

O sistema também calcula um **índice de estabilidade** para cada registro.

O indicador combina informações de:

```text
Energia
Oxigênio
Comunicação
Radiação
Temperatura
```

O cálculo utilizado considera diferentes pesos para cada variável:

```python
indice_estabilidade = (
    (energia_pct * 0.30)
    + (oxigenio_pct * 0.30)
    + (comunicacao_pct * 0.25)
    - (radiacao_msv * 10)
    - (temperatura_c * 0.15)
)
```

Quanto maior o índice, melhor a estabilidade geral do registro monitorado.

---

## Integração com API

O projeto utiliza a biblioteca **Requests** para consumir dados da API pública **Open-Meteo**.

A consulta utiliza como referência as coordenadas do **Centro Espacial Kennedy**, na Flórida.

São coletadas informações como:

* temperatura externa;
* velocidade do vento;
* direção do vento;
* horário da coleta.

Os dados recebidos em formato **JSON** são tratados pelo programa e adicionados ao relatório final.

A comunicação com a API também utiliza tratamento de erros com `try/except`, evitando que uma falha de conexão interrompa todo o processamento.

---

## Análise com Pandas

A biblioteca **Pandas** é utilizada durante todo o processamento da base.

Entre os recursos utilizados estão:

```python
df.head()
df.tail()
df.info()
df.describe()
```

Também são aplicados filtros para separar automaticamente registros classificados como críticos ou em atenção.

Durante o processamento, o sistema cria novas colunas:

```text
classificacao_risco
analise_automatica
energia_consumida_pct
indice_estabilidade
```

---

## Relatório final

Após o processamento, o sistema gera automaticamente o arquivo:

```text
relatorio_final_orion_x.xlsx
```

O relatório possui as seguintes abas:

| Aba                    | Conteúdo                                   |
| ---------------------- | ------------------------------------------ |
| `Dados_Analisados`     | Base completa após o processamento         |
| `Resumo_Estatistico`   | Estatísticas dos dados numéricos           |
| `Resumo_Classificacao` | Quantidade de registros por nível de risco |
| `Alertas_Criticos`     | Registros classificados como críticos      |
| `Alertas_Atencao`      | Registros que precisam de atenção          |
| `Dados_API`            | Informações obtidas através da API         |
| `Resumo_Geral`         | Indicadores consolidados da missão         |

---

## Estrutura do projeto

```text
orion-x-monitoramento/
│
├── GS2_py.ipynb
│
├── base_missao_orion_x.xlsx
│
├── relatorio_final_orion_x.xlsx
│
├── GS_python.pdf
│
└── README.md
```

### Arquivos

**`GS2_py.ipynb`**

Notebook contendo o código responsável pelo processamento e análise dos dados.

**`base_missao_orion_x.xlsx`**

Base fictícia contendo os registros e dados dos sensores da missão.

**`relatorio_final_orion_x.xlsx`**

Relatório gerado após a execução do sistema.

**`GS_python.pdf`**

Documentação acadêmica do projeto, contendo objetivos, explicações do código e descrição das funcionalidades.

---

## Tecnologias utilizadas

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python\&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-purple?logo=pandas)
![Excel](https://img.shields.io/badge/Excel-OpenPyXL-green?logo=microsoftexcel)
![API](https://img.shields.io/badge/API-Open--Meteo-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

Principais tecnologias:

* Python
* Pandas
* Requests
* OpenPyXL
* Jupyter Notebook
* Microsoft Excel
* API Open-Meteo
* JSON

---

## Como executar o projeto

### 1. Clone o repositório

```bash
git clone URL-DO-SEU-REPOSITORIO
```

Entre na pasta:

```bash
cd orion-x-monitoramento
```

### 2. Instale as dependências

```bash
pip install pandas openpyxl requests
```

### 3. Verifique a base de dados

Certifique-se de que o arquivo:

```text
base_missao_orion_x.xlsx
```

esteja disponível no mesmo ambiente de execução do notebook.

### 4. Execute o notebook

Abra:

```text
GS2_py.ipynb
```

utilizando **Jupyter Notebook**, **JupyterLab** ou **Google Colab** e execute as células do projeto.

Após o processamento, será gerado o arquivo:

```text
relatorio_final_orion_x.xlsx
```

---

## Fluxo da aplicação

```text
Base de dados Excel
        ↓
Leitura com Pandas
        ↓
Análise dos registros
        ↓
Classificação de risco
        ↓
Geração de alertas
        ↓
Cálculo do índice de estabilidade
        ↓
Consulta à API Open-Meteo
        ↓
Consolidação das informações
        ↓
Geração do relatório Excel
```

---

## Conceitos aplicados

O desenvolvimento do projeto permitiu aplicar diferentes conceitos de Python e análise de dados, incluindo:

* estruturas de dados;
* tuplas;
* dicionários;
* loops;
* funções;
* condicionais;
* manipulação de DataFrames;
* filtros com Pandas;
* análise estatística;
* leitura e escrita de arquivos Excel;
* consumo de APIs REST;
* manipulação de JSON;
* tratamento de exceções;
* automação de relatórios.

---

## Possíveis melhorias futuras

Como evolução do projeto, poderiam ser implementados:

* dashboard interativo para visualização dos sensores;
* gráficos de temperatura, energia, oxigênio e radiação;
* monitoramento contínuo dos registros;
* banco de dados para armazenamento histórico;
* sistema de notificações para situações críticas;
* interface gráfica ou aplicação Web;
* novos indicadores para previsão de situações de risco.

---

## Autor

**Matheus Costa Cutrim**

RM: 568087
Turma: CCPR

Projeto desenvolvido para a disciplina de Python como parte da **Global Solution – 2º Semestre**.

---

## Licença

Este projeto foi desenvolvido para fins acadêmicos e educacionais.
