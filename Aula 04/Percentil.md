# Percentis — Material Didático


# Percentis — Entendendo a posição de um valor em um conjunto de dados

**Curso:** Machine Learning / Estatística para Ciência de Dados  
**Professora:** Karize Viecelli  
**Nível:** Iniciante ao Intermediário

---
---
# Objetivos da Aula

Ao final deste material, o aluno será capaz de:

- Compreender o que é um percentil.
- Interpretar percentis em diferentes contextos.
- Diferenciar percentis, quartis e mediana.
- Calcular percentis utilizando Python.
- Aplicar percentis na análise exploratória de dados (EDA).
- Utilizar percentis para identificar outliers.
- Entender como percentis são utilizados em Machine Learning.

---

# 1. Imagine uma corrida...

Imagine uma maratona com **100 corredores**.

Você terminou em **15º lugar**.

Isso significa que:

- 14 pessoas chegaram antes.
- 85 chegaram depois.

Você está aproximadamente no **Percentil 85**.

Ou seja:

> Você foi melhor que aproximadamente 85% dos participantes.

É exatamente isso que um percentil representa.

**Percentil = posição relativa de um valor dentro de um conjunto de dados.**

---

# Outra analogia

Imagine uma turma com 40 alunos.

Após uma prova, as notas foram organizadas da menor para a maior.

Aluno | Nota
------|------
1º | 1,5
2º | 2,0
...
20º | 6,5
...
40º | 10,0

Se sua nota ficou exatamente no meio da turma...

Você está no:

**Percentil 50**

Metade dos alunos teve nota menor.

Metade teve nota maior.

---

# Definição

Um percentil divide um conjunto de dados em **100 partes iguais**.

Cada percentil indica a porcentagem de valores abaixo dele.

Por exemplo:

Percentil | Significado
-----------|------------------------------
P10 | 10% dos dados estão abaixo
P25 | 25% estão abaixo
P50 | metade dos dados
P75 | 75% estão abaixo
P90 | 90% estão abaixo
P95 | somente 5% estão acima
P99 | apenas 1% está acima

---

# Como interpretar?

Suponha o salário de funcionários.

Salários:

```
1800
2000
2200
2500
2600
2800
3000
3500
4500
8000
```

Agora calculamos:

P25 = 2250

Significa:

25% recebem menos que R$2250.

---

P50 = 2700

Significa:

50% recebem menos que R$2700.

Esse é também a **mediana**.

---

P90 = 4850

Significa:

90% recebem menos que R$4850.

Somente os 10% mais bem pagos estão acima.

---

# Visualizando

```
0%                                             100%

|------------------------------------------------|

P10      P25        P50        P75          P90
 |---------|----------|----------|------------|

```

---

# Percentis NÃO dividem os dados igualmente

Eles dividem a **posição**, não os valores.

Exemplo:

```
1
2
3
4
5
6
7
8
100
```

O Percentil 90 ficará próximo de 100.

Isso mostra que os dados podem estar muito espalhados.

---

# Percentis x Quartis

Quartis são apenas percentis especiais.

Quartil | Percentil
---------|------------
Q1 | P25
Q2 | P50
Q3 | P75

Ou seja:

- Primeiro Quartil = Percentil 25
- Segundo Quartil = Percentil 50
- Terceiro Quartil = Percentil 75

---

# Percentis x Mediana

A mediana é simplesmente:

**Percentil 50**

Ela divide os dados em duas partes iguais.

---

# Como calcular em Python

Lista:

```python
import numpy as np

idades = [18,19,20,21,22,23,24,25,30,40]
```

Percentil 25

```python
np.percentile(idades,25)
```

Resultado

```
20.25
```

---

Percentil 50

```python
np.percentile(idades,50)
```

Resultado

```
22.5
```

---

Percentil 90

```python
np.percentile(idades,90)
```

Resultado

```
31
```

---

# Calculando vários percentis

```python
np.percentile(
    idades,
    [10,25,50,75,90]
)
```

Resultado

```
array([
18.9,
20.25,
22.5,
24.75,
31
])
```

---

# Utilizando Pandas

```python
import pandas as pd

df = pd.DataFrame({
    "idade":[18,19,20,21,22,23,24,25,30,40]
})
```

```python
df["idade"].quantile(0.25)
```

Observe:

Percentil | Quantile
-----------|-----------
25% | 0.25
50% | 0.50
75% | 0.75

---

# Percentis em gráficos

Imagine um BoxPlot.

```
          _________
         |         |
---------|---------|---------
        Q1   Mediana   Q3
```

Os limites da caixa são:

- Percentil 25
- Percentil 75

A linha central:

Percentil 50

---

# Aplicação em Machine Learning

Percentis aparecem frequentemente na preparação dos dados.

Exemplos:

✔ Detectar outliers

✔ Criar faixas

✔ Normalizar dados

✔ Analisar distribuição

✔ Definir limites

---

# Detectando Outliers

Imagine:

```
10
12
13
15
15
16
17
18
19
250
```

O valor 250 parece estranho.

Podemos usar:

- Percentil 25
- Percentil 75

Depois calcular:

```
IQR = P75 - P25
```

Então:

```
Limite inferior

P25 − 1.5 × IQR

Limite superior

P75 + 1.5 × IQR
```

Tudo que estiver fora desses limites é considerado um possível outlier.

---

# Exemplo

```python
dados = [10,12,13,15,15,16,17,18,19,250]

Q1 = np.percentile(dados,25)
Q3 = np.percentile(dados,75)

IQR = Q3-Q1

inferior = Q1 - 1.5*IQR
superior = Q3 + 1.5*IQR
```

Depois:

```python
for valor in dados:

    if valor < inferior or valor > superior:
        print(valor,"é outlier")
```

Resultado

```
250 é outlier
```

---

# Percentis em vestibulares

É comum ouvir:

"O aluno está no percentil 98."

Significa:

Ele teve desempenho melhor que 98% dos candidatos.

---

# Percentis na Medicina

Exemplo:

Uma criança está no percentil 90 de altura.

Isso significa:

Ela é mais alta que 90% das crianças da mesma idade.

---

# Percentis no mercado financeiro

Investidores usam percentis para descobrir:

- ações muito caras
- ações muito baratas
- empresas fora do padrão

---

# Percentis em IA

Imagine um banco com milhões de clientes.

Pode-se calcular:

- Percentil da renda
- Percentil de compras
- Percentil de atraso
- Percentil de risco

Essas informações ajudam modelos de Machine Learning.

---

# Erros comuns

❌ Achar que Percentil 90 significa nota 9.

Não tem relação.

É posição.

---

❌ Confundir percentagem com percentil.

20%

é uma porcentagem.

Percentil 20

é uma posição.

---

❌ Achar que P50 é média.

Não.

É mediana.

---

# Resumo

Percentil | Significado
-----------|-------------------------------
P10 | 10% abaixo
P25 | Primeiro quartil
P50 | Mediana
P75 | Terceiro quartil
P90 | 90% abaixo
P95 | Apenas 5% acima
P99 | Apenas 1% acima

---

# Exercícios

## Exercício 1

Explique com suas palavras o que representa o Percentil 75.

---

## Exercício 2

Qual a diferença entre:

- média
- mediana
- percentil

---

## Exercício 3

Utilizando Python:

```python
idades = [
18,19,20,20,21,21,22,23,
24,24,25,27,30,32,35
]
```

Calcule:

- P25
- P50
- P75
- P90

---
 
## Exercício 4

Explique por que o Percentil 50 também é chamado de mediana.

---

## Exercício 5

Qual dos seguintes exemplos representa corretamente um percentil?

a) Um aluno tirou nota 9,5 e isso significa que está no Percentil 95.

b) Uma criança está no Percentil 80 de altura, ou seja, é mais alta do que aproximadamente 80% das crianças da mesma idade.

c) Percentil é a mesma coisa que porcentagem.

d) Percentil sempre representa a média dos dados.

---

# Gabarito

## Exercício 1

O Percentil 75 indica que aproximadamente 75% dos valores estão abaixo desse ponto e 25% estão acima.

---

## Exercício 2

- Média: soma dos valores dividida pela quantidade.
- Mediana: valor central do conjunto ordenado.
- Percentil: posição relativa de um valor em relação aos demais.

---

## Exercício 3

```python
import numpy as np

idades = [
18,19,20,20,21,21,22,23,
24,24,25,27,30,32,35
]

print(np.percentile(idades,[25,50,75,90]))
```

---

## Exercício 4

Porque divide os dados em duas metades: 50% abaixo e 50% acima.

---

## Exercício 5

Resposta correta:

**b)** Uma criança está no Percentil 80 de altura, ou seja, é mais alta do que aproximadamente 80% das crianças da mesma idade.

---

# Conclusão

Os percentis são uma ferramenta essencial para interpretar dados de forma mais robusta do que apenas utilizando médias. Eles permitem compreender a posição de um indivíduo ou de uma observação dentro de um conjunto de dados, sendo amplamente utilizados em estatística, educação, saúde, finanças e Machine Learning. Dominar esse conceito é um passo importante para realizar análises exploratórias mais precisas e construir modelos de aprendizado de máquina mais confiáveis.
````

