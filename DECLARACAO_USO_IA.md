# Declaração de uso de IA generativa

**Disciplina:** MC886 — Introduction to Machine Learning
**Trabalho:** Assignment 1 — Linear Models
**Grupo:** Lucas Gomes Bussinger da Silva (247314), Caíque Andrade (204677), Jorge Felipe Lopes Pereira (251771)

Esta declaração atende à diretriz 4 do enunciado, que exige informar os modelos
utilizados e transcrever os prompts empregados na geração de código incorporado
à solução.

> **[PREENCHER ANTES DE SUBMETER]** Este arquivo documenta a sessão de uso de IA
> conduzida por Caíque Andrade em 13/09/2026. Se os demais integrantes usaram
> ferramentas de IA em outros momentos do trabalho (por exemplo na análise
> exploratória ou no `preprocess_data`), essas sessões devem ser acrescentadas
> na seção "Outros usos" ao final.

---

## 1. Modelos utilizados

| Ferramenta | Modelo | Identificador | Data |
|---|---|---|---|
| Claude Code (CLI da Anthropic) | Claude Opus 5 | `claude-opus-5` | 13/09/2026 |

Nenhuma outra ferramenta de IA generativa foi utilizada nesta sessão.

---

## 2. Escopo do que foi gerado com auxílio de IA

### 2.1 Código

As seguintes células foram escritas com auxílio do modelo:

| Célula | Conteúdo |
|---|---|
| 31 | **Parcial** — os dois primeiros gráficos são de autoria do grupo (commit `19a1ad9`); foram acrescentados os diagnósticos de resíduo médio por hora e perfil diário |
| 41 | `polynomial_expansion` e classe `Standardizer` |
| 42 | Split de validação temporal, varredura de graus e ablação por feature |
| 46 | `build_poly_features` e treino do modelo polinomial final |
| 48 | Gráficos comparativos linear vs polinomial |
| 56 | Classe `PoissonRegression` |
| 57 | Varredura de learning rates e curva de convergência da Poisson |
| 61, 62 | Treino do modelo Poisson final e gráficos comparativos |
| 67, 68 | Varredura e treino do modelo Poisson polinomial |
| 75, 76 | Avaliação final no conjunto de teste e gráficos de comparação |

### 2.2 Texto analítico

**Importante:** o enunciado afirma que o uso de IA para *analisar e discutir
resultados* é desencorajado. As respostas discursivas das células 33, 38, 44, 50,
54, 59, 64, 70, 73 e 78 foram **rascunhadas com auxílio do modelo** e revisadas
integralmente por mim antes da submissão. Cada uma está marcada com a tag
`[REVISAR]` no notebook.

> **[PREENCHER]** Remover as tags `[REVISAR]` conforme cada resposta for revisada,
> e ajustar a redação para refletir o entendimento do grupo.

### 2.3 Ambiente

O ambiente virtual (`.venv`) e a instalação de dependências foram configurados
com auxílio do modelo. Versões fixadas: numpy 2.3.3, pandas 2.3.2, matplotlib,
seaborn.

### 2.4 O que **não** teve auxílio de IA

- Carregamento dos dados e split treino/teste (células 5 e 7) — fornecidos no enunciado.
- Análise inicial e respostas das células 10 e 12.
- Análise exploratória das células 14, 15 e 17.
- Função `preprocess_data` (célula 19).
- Métricas e classe `LinearRegression` (célula 22).
- Funções `plot_results`, `pred_vs_true_plot` e `q_q_plot` (células 23, 29, 35).

> **[CONFERIR]** A lista acima assume que essas partes foram escritas pelo grupo
> sem auxílio de IA. Corrigir se não for o caso.

---

## 3. Transcrição dos prompts

Sessão conduzida em 13/09/2026 via Claude Code. Prompts transcritos na ordem em
que foram enviados:

1. > boa tarde, me ajude a entender o que falta implementar no @mc886_2s2026-assignment_1.ipynb

2. > qual a seção de "visualing predictions"?

3. > me de uma explicação rápida sobre os modelos polinomiais, o que devo fazer e quanto tempo você acha que isso levará

4. > tem alguma parte do trabalho que falta que você não consegue fazer?

5. > 1. Pode escrever todas as respostas como se fosse eu, pois vou revisar todas. Coloque a tag "revisar"
   > 2. Gere um arquivo, vou declara o uso no final
   > 3. Faça o necessário para resolver essas pendências: crie um venv, baixe as dependências e etc

6. > o que você já fez até agora?

7. > pode continuar de onde parou

Não houve outros prompts nesta sessão.

---

## 4. Verificação independente dos resultados

Para não depender da correção do código gerado, os seguintes pontos foram
verificados de forma independente durante a sessão:

- **`polynomial_expansion`** foi testada em um caso pequeno com resultado
  conhecido: `[[1,2],[3,4]]` no grau 2 deve produzir `[x₁, x₂, x₁², x₁x₂, x₂²]`.
  A asserção correspondente está na própria célula 41 e roda a cada execução.
- **`PoissonRegression`** foi validada contra um solver de Newton/IRLS
  implementado separadamente. Ambos convergem para a mesma
  log-verossimilhança negativa (−23616,2221) e o mesmo R² (0,6177), confirmando
  que o gradiente descendente atinge o MLE e que o desempenho inferior da
  Poisson simples é propriedade do modelo, não erro de implementação.
- **Convergência** foi verificada aumentando as iterações de 5.000 para 60.000
  sem alteração na função objetivo.

---

## 5. Outros usos

> **[PREENCHER]** Registrar aqui sessões de IA usadas por outros integrantes do
> grupo, incluindo ferramenta, modelo e prompts, caso tenham ocorrido.

---

_Última atualização: 13/09/2026_
