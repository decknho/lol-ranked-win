# 🎮 League of Legends — Previsão de Vitórias

Projeto de Ciência de Dados e Machine Learning desenvolvido para analisar partidas ranqueadas de League of Legends e prever a vitória da equipe Blue.

O projeto explora como a preparação dos dados, a engenharia de atributos e a comparação entre modelos de classificação podem contribuir para a previsão de resultados.

## 🎯 Objetivo do Projeto

Desenvolver e comparar modelos de Machine Learning capazes de prever se a equipe Blue venceria uma partida (`blueWins`), identificando padrões relevantes nas estatísticas das equipes.

Além disso, investigar se representar as diferenças entre as equipes proporciona melhores resultados do que manter as informações de cada equipe separadamente.

## 🛠️ Tecnologias e Ferramentas

- **Python** — desenvolvimento e análise de dados.
- **Pandas e NumPy** — manipulação e preparação dos dados.
- **Scikit-learn** — pré-processamento, avaliação dos modelos, validação cruzada e otimização de hiperparâmetros.
- **XGBoost** — desenvolvimento de modelos de classificação.
- **Random Forest** — classificação utilizando conjuntos de árvores de decisão.
- **Matplotlib e Seaborn** — visualização de dados.
- **Jupyter Notebook** — desenvolvimento e documentação das análises.

## 🔬 Metodologia

O projeto foi desenvolvido seguindo as principais etapas de um fluxo de trabalho de Machine Learning.

### 1. Preparação dos dados

Análise inicial da base, identificação de variáveis redundantes e remoção de informações que representavam essencialmente os mesmos atributos.

### 2. Engenharia de atributos

Foram avaliadas duas representações dos dados:

- **`lol_diff`** — utiliza as diferenças entre as equipes, permitindo analisar diretamente as vantagens acumuladas.
- **`lol_no_diff`** — mantém as estatísticas de cada equipe separadamente.

### 3. Desenvolvimento dos modelos

Foram utilizados dois algoritmos de classificação:

- **Random Forest**
- **XGBoost**

Inicialmente, os modelos foram avaliados com suas configurações base.

### 4. Otimização dos hiperparâmetros

Foi utilizado `GridSearchCV` com validação cruzada de 5 folds para testar diferentes configurações e buscar melhores resultados.

### 5. Avaliação dos resultados

A avaliação considerou as métricas Accuracy, Precision, Recall, F1-score e ROC-AUC, além de matrizes de confusão, análise dos erros, calibração das probabilidades e importância das variáveis.

## 📊 Resultados

A comparação dos modelos demonstrou desempenho semelhante entre os algoritmos, com uma pequena vantagem para a representação baseada nas diferenças entre as equipes.

| Modelo | Representação | ROC-AUC |
|---|---|---:|
| XGBoost otimizado | `lol_diff` | **0,815** |
| Random Forest | `lol_diff` | 0,814 |
| XGBoost | `lol_no_diff` | 0,810 |
| Random Forest | `lol_no_diff` | 0,810 |

O **XGBoost otimizado com a representação `lol_diff`** foi selecionado como a configuração de melhor desempenho, apresentando ROC-AUC de 0,815.

Entretanto, a diferença em relação ao Random Forest foi mínima, indicando que ambos os modelos conseguiram identificar padrões relevantes nos dados.

**Importante:** ROC-AUC mede a capacidade do modelo de distinguir as classes ao longo de diferentes limites de decisão. Um valor de 0,815 não significa que o modelo acertou 81,5% das partidas.

## 🔎 Importância das Variáveis

A análise da importância das variáveis destacou características relacionadas ao ouro acumulado, à experiência e às eliminações das equipes.

### Representação `lol_diff`

Entre as variáveis de maior relevância, destacaram-se:

- `totalGoldDiff`
- `totalExperienceDiff`
- `killDiff`

### Representação `lol_no_diff`

Também apresentaram relevância variáveis como:

- `blueTotalGold`
- `redTotalGold`
- `blueTotalExperience`
- `redTotalExperience`

Os resultados sugerem que as diferenças de desempenho entre as equipes são informações úteis para estimar o resultado de uma partida.

A importância das variáveis indica sua contribuição para as previsões do modelo, não necessariamente uma relação de causa e efeito.

## 💡 Principais Aprendizados

- A engenharia de atributos pode influenciar o desempenho dos modelos.
- A representação baseada nas diferenças entre as equipes apresentou os melhores resultados neste experimento.
- XGBoost e Random Forest demonstraram desempenho bastante semelhante.
- A análise de diferentes métricas permite compreender melhor os pontos fortes e as limitações dos modelos.
- A preparação dos dados e a interpretação dos resultados são etapas fundamentais em projetos de Ciência de Dados.

## 📁 Estrutura do Repositório

```text
lol-ranked-win/
├── LICENSE
├── README.md
├── data.csv
└── main.ipynb
```

- `data.csv`: base de dados utilizada no projeto.
- `main.ipynb`: notebook com as análises, experimentos, treinamento e avaliação dos modelos.
- `README.md`: documentação do projeto.

## 🚀 Como Executar

Clone o repositório:

```bash
git clone https://github.com/decknho/lol-ranked-win.git
cd lol-ranked-win
```

Instale as bibliotecas utilizadas:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
```

Inicie o Jupyter Notebook:

```bash
jupyter notebook main.ipynb
```

Verifique se o arquivo `data.csv` está no caminho esperado pelo notebook antes de executar as células.

## 🏁 Conclusão

O projeto permitiu desenvolver um fluxo de trabalho de Machine Learning, desde a preparação dos dados e a engenharia de atributos até a otimização e avaliação dos modelos.

Os experimentos demonstraram que a representação baseada nas diferenças entre as equipes foi uma abordagem eficiente para esse problema. O XGBoost otimizado apresentou o melhor resultado numérico, com ROC-AUC de 0,815, embora o desempenho tenha sido praticamente igual ao do Random Forest.

O trabalho reforça a importância de testar diferentes representações dos dados, comparar modelos e interpretar as métricas de avaliação com cuidado.

---

**Autor:** [@decknho](https://github.com/decknho)
