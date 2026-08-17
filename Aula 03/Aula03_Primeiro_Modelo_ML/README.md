# Aula 03 — Construindo o Primeiro Modelo de Machine Learning

**© @karizeviecelli - 2026**

Link Colab
https://colab.research.google.com/drive/1t16lSfboeMP883QyvGiyorjt-Nu-e9Nz?usp=sharing

## Objetivo da aula

Nesta aula você utilizará o dataset tratado para construir, treinar, testar, avaliar, visualizar e salvar um modelo de classificação.

## Algoritmo

`DecisionTreeClassifier` — Árvore de Decisão.

## Arquivos principais

- `Aula03_Colab.ipynb`: notebook guiado.
- `datasets/alunos_tratado.csv`: dataset principal.
- `datasets/alunos_novos.csv`: novos registros para previsão.
- `datasets/alunos_teste.csv`: dados para avaliação externa.
- `modelos/modelo_aprovacao.pkl`: modelo treinado de exemplo.
- `imagens/arvore_decisao_exemplo.png`: visualização da árvore.
- `imagens/importancia_features.png`: gráfico de importância.
- `exercicios.md`: atividades.
- `desafio.md`: missão final.
- `gabarito.md`: solução comentada.
- `checklist.md`: conferência da entrega.
- `guia_professor.md`: roteiro da aula.

## Fluxo da aula

```text
Dataset tratado
      ↓
Features e Target
      ↓
Treino e teste
      ↓
Treinamento
      ↓
Previsões
      ↓
Acurácia
      ↓
Visualização
      ↓
Salvar modelo
```

## Features utilizadas

- `Idade`
- `Nota`
- `Frequencia`

## Target

- `Aprovado`

## Resultado do modelo de exemplo

Acurácia obtida na divisão com `random_state=42`: **100.00%**

## Como usar no Google Colab

1. Abra `Aula03_Colab.ipynb`.
2. Faça upload de `alunos_tratado.csv`.
3. Execute as células em ordem.
4. Faça os laboratórios.
5. Use `alunos_novos.csv` para realizar previsões.
6. Salve seu próprio arquivo `.pkl`.

## Atenção

O resultado pode mudar quando você altera:

- `test_size`;
- `random_state`;
- profundidade da árvore;
- conjunto de features.
