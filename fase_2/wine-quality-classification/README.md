# Classificação da Qualidade de Vinhos com Machine Learning

## Objetivo

Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de prever a qualidade de vinhos tintos utilizando apenas características físico-químicas obtidas durante o processo produtivo.

A proposta busca avaliar se variáveis laboratoriais podem auxiliar ou complementar a avaliação tradicional realizada por especialistas.

---

## Dataset

Foi utilizado o dataset Wine Quality (Red Wine), contendo:

* 1.143 amostras de vinho tinto
* 11 características físico-químicas
* Nota de qualidade atribuída por especialistas

A variável alvo foi transformada em uma classificação binária:

* 0 → Qualidade Baixa/Média (nota < 7)
* 1 → Alta Qualidade (nota ≥ 7)

---

## Tecnologias Utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* Jupyter Notebook

---

## Estrutura do Projeto

```text
wine-quality-classification/

├── data/
│   ├── raw/
│   │   └── WineQT.csv
│   └── processed/
│       └── wine_quality_processed.csv
│
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_evaluation.ipynb
│
├── results/
│   ├── confusion_matrix_rf.png
│   ├── feature_importance_rf.png
│   └── model_comparison.csv
│
└── README.md
```

---

## Etapas do Projeto

### 1. Análise Exploratória dos Dados (EDA)

* Verificação da qualidade dos dados
* Análise estatística descritiva
* Distribuição das variáveis
* Identificação de outliers
* Matriz de correlação

Principais insights:

* Álcool apresentou correlação positiva com a qualidade
* Acidez volátil apresentou correlação negativa
* Sulfatos e ácido cítrico também demonstraram influência relevante

---

### 2. Pré-processamento

* Criação da variável alvo (`quality_label`)
* Separação entre variáveis independentes e variável alvo
* Divisão dos dados em treino e teste
* Padronização utilizando StandardScaler

---

### 3. Modelagem

Foram avaliados dois algoritmos:

#### Logistic Regression

Modelo utilizado como baseline para comparação.

#### Random Forest

Modelo baseado em múltiplas árvores de decisão, selecionado como modelo final devido ao melhor desempenho.

---

### 4. Avaliação

As métricas utilizadas foram:

* Accuracy
* Precision
* Recall
* F1-Score
* Matriz de Confusão

Comparação dos modelos:

| Métrica            | Logistic Regression | Random Forest |
| ------------------ | ------------------: | ------------: |
| Accuracy           |               86,9% |         91,7% |
| Precision Classe 1 |                 55% |           76% |
| Recall Classe 1    |                 34% |           59% |
| F1-Score Classe 1  |                 42% |           67% |

---

## Resultados

O modelo Random Forest apresentou o melhor desempenho:

* Accuracy: 91,7%
* Precision: 76%
* Recall: 59%
* F1-Score: 67%

Além disso, as variáveis mais relevantes para a previsão da qualidade do vinho foram:

1. Teor alcoólico
2. Acidez volátil
3. Ácido cítrico
4. Sulfatos

---

## Conclusão

Os resultados demonstram que características físico-químicas são capazes de prever a qualidade dos vinhos com alto grau de precisão.

O modelo Random Forest apresentou desempenho superior ao modelo Logistic Regression e mostrou potencial para apoiar decisões relacionadas ao controle de qualidade, reduzindo a dependência exclusiva de avaliações sensoriais realizadas por especialistas.

---

## Integrantes

* Danilo Cangussu
* Isabella Lima
* Kevyn Rabelo
