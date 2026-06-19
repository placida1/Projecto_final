# Projecto Final - Analise de Dados de Testes Laboratoriais

## Visao Geral
Este projeto analisa dados de testes laboratoriais para explorar o comportamento do valor de Ct (valor_ct) e a sua relacao com categorias clinicas e laboratoriais, como tipo de patogeno, estado do resultado, laboratorio e qualidade da amostra.

Fluxo de trabalho:
- importacao e inspecao dos dados
- limpeza e organizacao
- estatisticas descritivas
- analise de frequencias de variaveis categoricas
- testes estatisticos inferenciais
- geracao e exportacao de graficos

## Estrutura do Projecto

```text
data/
  processed/
    lab_limpo.csv
    lab_limpo1.csv
  raw/
figs/
  barplot_resultado_patogeno.png
  boxplot_valor_ct.png
  histogram_valor_ct.png
notebooks/
tables/
  valores_descriptivos_valor_ct.csv
  table3_frequency_all.csv
  table3_frequency_resultado.csv
  table3_frequency_patogeno.csv
  table3_frequency_laboratorio.csv
  table3_frequency_qualidade_amostra.csv
  table9_statistical_tests.csv
```

## Conjunto de Dados
Ficheiro principal analisado:
- data/processed/lab_limpo1.csv

Variaveis principais:
- id_amostra: identificador da amostra
- id_paciente: identificador do paciente
- patogeno: categoria do patogeno (ex.: COVID-19, Influenza)
- valor_ct: valor numerico de Ct
- resultado: resultado do teste (Positivo/Negativo)
- data_teste: data do teste
- laboratorio: laboratorio onde o teste foi processado
- qualidade_amostra: qualidade da amostra

## Configuracao do Ambiente

A partir da raiz do projeto:

```bash
/opt/homebrew/bin/python3 -m venv .venv
source .venv/bin/activate
pip install pandas numpy scipy matplotlib seaborn
```

No VS Code, selecione o interpretador .venv:
- Paleta de Comandos -> Python: Select Interpreter -> .venv

## Inicio Rapido

### 1. Executar a analise na consola interativa do Python ou em caderno
Carregar os dados:

```python
import pandas as pd
df = pd.read_csv("data/processed/lab_limpo1.csv")
```

### 2. Criar tabelas de frequencia (Tabela 3)
Os ficheiros de saida sao guardados em tables/.

### 3. Criar resumo de testes estatisticos (Tabela 9)
Ficheiro gerado:
- tables/table9_statistical_tests.csv

### 4. Gerar graficos
Graficos exportados atualmente:
- figs/boxplot_valor_ct.png
- figs/barplot_resultado_patogeno.png
- figs/histogram_valor_ct.png

## Resumo dos Resultados Atuais
Com base em tables/table9_statistical_tests.csv:

- Shapiro-Wilk para valor_ct: p = 0.0563 (aproximadamente normal para alpha = 0.05)
- Mann-Whitney (valor_ct por patogeno): p = 0.2122 (sem diferenca significativa)
- Mann-Whitney (valor_ct por resultado): p < 0.0001 apos arredondamento no output (diferenca significativa)
- Qui-quadrado (resultado vs patogeno): p = 0.9101 (sem associacao)
- Qui-quadrado (resultado vs laboratorio): p = 1.0000 (sem associacao)
- Qui-quadrado (resultado vs qualidade_amostra): p = 0.0902 (sem associacao para 0.05)

## Notas de Reprodutibilidade
- Execute sempre dentro de .venv para evitar problemas de importacao de pacotes.
- Guarde os outputs gerados em tables/ e figs/ para manter os resultados organizados.
- Se o prompt do Python mostrar ..., feche o bloco com Enter ou cancele com Ctrl+C.

## Autora
Placida Maholela
