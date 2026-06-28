# Classificação Estelar com Curvas de Luz do TESS

Projeto final de SCC0276 (Aprendizado de Máquina, ICMC-USP). Classificação multiclasse
de curvas de luz do telescópio TESS em quatro classes: binária eclipsante, estrela
pulsante, moduladora de rotação e trânsito de exoplaneta.

## Resultados

Cinco classificadores foram comparados na mesma base de 3346 curvas, com divisão de
80% para treino e 20% para teste.

| Modelo | F1-macro | Revocação exoplaneta |
|---|---|---|
| Random Forest | 0,827 | 0,840 |
| 1D-CNN | 0,821 | 0,821 |
| SVM (RBF) | 0,806 | 0,877 |
| KNN | 0,784 | 0,764 |
| Árvore de Decisão | 0,774 | 0,830 |

O Random Forest e a 1D-CNN ficaram praticamente empatados. A maior confusão ocorre
entre pulsantes e moduladoras de rotação, que têm formas parecidas.

## Estrutura

- `notebooks/01_dados_preprocessamento.ipynb`: aquisição dos dados e pré-processamento.
- `notebooks/02_modelagem_avaliacao.ipynb`: treino e avaliação dos modelos.
- `results/`: figuras e tabelas de métricas.
- `requirements.txt`: dependências.

A pasta `data/` (catálogos, curvas e dataset processado) não é versionada por ser
grande; os notebooks a regeneram.

## Como executar

### Google Colab
1. Suba a pasta para o Google Drive em `MyDrive/stellar-classification`.
2. Abra os notebooks no Colab. A célula inicial monta o Drive e instala as bibliotecas.
3. Rode o notebook `01` (runtime CPU) e depois o `02` (runtime GPU para a CNN).

### Local
1. `pip install -r requirements.txt`
2. Rode `notebooks/01_dados_preprocessamento.ipynb` e depois `notebooks/02_modelagem_avaliacao.ipynb`.

## Dados

Baixados por script no notebook `01`:
- TESS Triple-9 (exoplanetas), via VizieR.
- TESS-EBs (binárias eclipsantes), via MAST.
- Gaia DR3 (pulsantes e moduladoras de rotação).
- Curvas de luz do TESS, via lightkurve.
