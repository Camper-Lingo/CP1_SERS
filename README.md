# Análise de Consumo de Energia e Fator de Potência

## 📌 Sobre a atividade

Esta atividade teve como objetivo realizar uma análise exploratória de dados relacionados ao **consumo de energia elétrica** e ao **fator de potência**, utilizando Python e a biblioteca Pandas.

A análise foi realizada a partir de um conjunto de dados contendo informações sobre consumo, fator de potência e categorias de carga.

## 🎯 Objetivos

Durante a atividade, foram realizadas as seguintes análises:

* Identificação do maior consumo registrado;
* Cálculo de um limiar correspondente a **75% do consumo máximo**;
* Seleção dos registros que ultrapassam esse limite;
* Cálculo da quantidade e do percentual desses registros em relação à amostra;
* Identificação dos registros pertencentes à categoria **Maximum Load**;
* Análise dos valores de fator de potência;
* Definição de um limite para representar fatores de potência mais baixos;
* Criação de um novo conjunto de dados combinando **consumo elevado** e **fator de potência baixo**;
* Interpretação dos resultados e identificação de registros que podem exigir maior atenção da equipe de energia.

## 🛠️ Tecnologias utilizadas

* **Python**
* **Pandas**
* **Jupyter Notebook / Google Colab**

## 📊 Principais critérios utilizados

### Consumo elevado

Foi calculado o maior valor de consumo da amostra e definido um limite correspondente a 75% desse valor:

```python
maior_consumo = df1['Consumo_kWh'].max()
limiar_75 = 0.75 * maior_consumo
```

Em seguida, foram selecionados apenas os registros acima desse limite:

```python
df_consumo_alto = df1[df1['Consumo_kWh'] > limiar_75]
```

### Fator de potência

Foi utilizado o atributo de fator de potência em atraso (`FP_Atraso`). Após observar seus valores, foi definido um limite de **0,90** para representar valores mais baixos.

```python
limite_fp = 0.90
```

Os registros que apresentam simultaneamente consumo elevado e fator de potência abaixo do limite foram selecionados:

```python
df_atencao = df1[
    (df1['Consumo_kWh'] > limiar_75) &
    (df1['FP_Atraso'] < limite_fp)
]
```

## 🔎 Análise dos resultados

Os registros com consumo acima de 75% do máximo representam os casos de maior consumo dentro da amostra analisada.

Ao adicionar o fator de potência como segundo critério, o conjunto de registros se torna mais restritivo. Dessa forma, são selecionados apenas os casos que apresentam **alto consumo e baixo fator de potência simultaneamente**.

Esses registros podem merecer maior atenção da equipe de energia porque combinam uma demanda elevada com um fator de potência menos favorável, podendo indicar uma utilização menos eficiente da energia elétrica e a necessidade de uma investigação mais detalhada.

## 📁 Estrutura da atividade

```text
├── dados/
│   └── dataset.csv
├── atividade.ipynb
└── README.md
```

## 📚 Conclusão

A atividade permitiu aplicar conceitos de **análise e filtragem de dados com Pandas**, utilizando critérios estatísticos e operacionais para identificar situações de maior interesse no consumo de energia.

A combinação de diferentes indicadores, como consumo e fator de potência, possibilita uma análise mais específica e pode auxiliar na identificação de situações que merecem investigação e acompanhamento.
