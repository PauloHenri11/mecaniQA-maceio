# MecâniQA — Equipe Maceió

## Contexto

O projeto tem como objetivo desenvolver o módulo de análise e previsão da MecâniQA, utilizando dados históricos de Trocas de Óleo e Manutenções de Motor.

A proposta é compreender o comportamento temporal da demanda por manutenções, realizar o tratamento e análise dos dados e desenvolver modelos de previsão utilizando técnicas de Machine Learning.

## OAT 1 — Análise e Preparação dos Dados

Nesta etapa, realizamos a análise inicial do conjunto de dados, identificamos valores ausentes e exploramos o comportamento temporal da demanda.

Também desenvolvemos um pipeline inicial de Machine Learning, respeitando a divisão cronológica dos dados entre treinamento e teste.

## OAT 2 — Baselines e Engenharia de Atributos

Implementamos dois modelos de referência: Naive e Média Móvel de 7 dias.

A avaliação utilizou validação temporal com TimeSeriesSplit e as métricas MAE, RMSE e MAPE.

| Modelo | MAE | RMSE | MAPE |
|---|---|---|---|
| Naive | 6,65 | 8,92 | 32,64% |
| Média Móvel | 7,36 | 8,09 | 37,22% |

O Naive apresentou o melhor desempenho geral, com menores valores de MAE e MAPE, enquanto a Média Móvel obteve menor RMSE.

Também foram desenvolvidos atributos temporais, incluindo Lag 1, Lag 7 e Rolling Window de 7 dias, utilizando apenas informações anteriores ao período previsto.

## OAT 3 — Modelos de Regressão e Otimização

Nesta etapa, implementamos Random Forest e Gradient Boosting para previsão da demanda por trocas de óleo.

Utilizamos GridSearchCV e RandomizedSearchCV com TimeSeriesSplit para buscar configurações de hiperparâmetros, respeitando a ordem temporal dos dados.

Também comparamos o tempo de execução e a precisão das duas estratégias de busca.

### Comparação Final dos Modelos

Os três modelos foram avaliados sobre os mesmos 143 registros de teste.

| Modelo | MAE | RMSE | MAPE |
|---|---|---|---|
| Baseline Naive | 6,49 | 8,91 | 26,95% |
| Random Forest Inicial | 3,12 | 4,23 | 14,19% |
| Random Forest Tunado | 3,16 | 4,22 | 14,21% |

O Random Forest Inicial apresentou o melhor desempenho geral, reduzindo aproximadamente 52% do MAE e 47% do MAPE em relação ao Naive.

O modelo tunado obteve RMSE ligeiramente menor, mas não apresentou ganhos significativos em relação ao modelo inicial.

### Conclusão

Os resultados demonstraram que a utilização de modelos de Machine Learning melhorou significativamente a previsão da demanda em comparação com o baseline tradicional.

A otimização dos hiperparâmetros não garantiu uma melhoria adicional, destacando a importância de avaliar os modelos por meio de métricas e validação temporal.

## Equipe

**Time Maceió**

- Paulo Henrique
- Kauã Henrique
- João Henrique
- Cailane
