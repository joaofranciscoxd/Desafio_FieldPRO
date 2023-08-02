# Desafio_FieldPRO

# Previsão de Chuva - Análise de Dados e Modelagem

Este repositório contém o código em Python para análise de dados e modelagem de previsão de chuva com base em dados meteorológicos.

## Dados

Os dados utilizados nesta análise estão presentes nos arquivos 'Sensor_FieldPRO.csv' e 'Estacao_Convencional.csv'.

## Análise de Dados

O código realiza diversas etapas de preparação e análise dos dados:

1. Fatiamento da coluna 'Datetime – utc' em duas colunas separadas: 'data' e 'hora', e geração de uma nova coluna 'Datetime – utc' no formato de data e hora.

2. Preenchimento dos valores ausentes nas colunas 'air_humidity_100' e 'air_temperature_100' com as médias diárias correspondentes.

3. Fusão dos dados dos sensores FieldPRO e dos registros de chuvas da estação convencional, usando a coluna 'Datetime – utc' como chave.

4. Resample dos dados com base no 'piezo_charge', gerando 30 amostras entre cada par de linhas.

5. Remoção de linhas com viradas na coluna 'num_of_resets'.

6. Filtragem dos dados para manter apenas as linhas com 'Variação' maior que 0.

7. Visualização gráfica dos dados com o gráfico de linha 'Piezo Charge vs. Datetime – utc'.

8. Criação de um DataFrame de treino e teste após a remoção de colunas e outliers.

## Modelagem

O código utiliza a biblioteca PyCaret para a modelagem de previsão de chuva. As etapas de modelagem incluem:

1. Configuração do ambiente PyCaret, normalização dos dados, criação de recursos polinomiais e tratamento de outliers.

2. Comparação do desempenho de vários modelos de regressão.

3. Seleção do modelo com melhor desempenho, que neste caso é o "Extra Trees Regressor".

4. Ajuste automático dos hiperparâmetros do modelo selecionado.

5. Avaliação do desempenho do modelo ajustado usando métricas como MAE, MSE, RMSE, R², RMSLE e MAPE.

6. Realização de previsões com o modelo ajustado e armazenamento dos resultados em um arquivo 'df_predictions.xlsx'.

## Resultados

O modelo de previsão de chuva apresentou um desempenho muito bom, explicando cerca de 94.51% da variância total dos dados. As métricas de desempenho do modelo são as seguintes:

- MAE (Mean Absolute Error): 0.1531
- MSE (Mean Squared Error): 0.1363
- RMSE (Root Mean Squared Error): 0.3526
- R² (Coefficient of Determination): 0.9451
- RMSLE (Root Mean Squared Logarithmic Error): 0.1571
- MAPE (Mean Absolute Percentage Error): 0.3340

O percentual médio de erro para os casos em que a coluna "chuva" é diferente de 0 é de aproximadamente -4.16%, e para os casos em que a coluna "chuva" é igual a 0, é de 0.00%.

## Dependências

Para executar o código, as seguintes bibliotecas devem estar instaladas:

- pandas
- matplotlib
- seaborn
- scikit-learn
- pycaret
- imbalanced-learn
- openpyxl

Instale as bibliotecas utilizando o comando `pip install` antes de executar o código. Certifique-se de que os arquivos 'Sensor_FieldPRO.csv' e 'Estacao_Convencional.csv' estejam no mesmo diretório do arquivo de script Python.

---
