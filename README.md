# Tech Challenge - NPS Preditivo

Projeto de análise de dados voltado à identificação dos fatores associados à satisfação dos clientes de um e-commerce e à avaliação de uma prova de conceito para antecipar o risco de clientes se tornarem detratores.

## Estrutura do repositório

```text
1.data/
├── 1.raw/          # Base original, preservada sem alterações
└── 2.processed/    # Base preparada e enriquecida para análise

2.notebooks/
├── 1_data_understanding.ipynb  # Estrutura e qualidade dos dados
├── 2_eda.ipynb                 # Análise exploratória e conclusões
└── 3_modeling.ipynb            # Prova de conceito preditiva

4.docs/
├── 01_business_understanding.md
├── 02_metodologia.md
├── 03_conclusoes_eda.md
├── 04_limitacoes_e_decisoes.md
└── 05_modelagem_preditiva.md

5.outputs/
├── 1.figures/      # Gráficos gerados pela análise
├── 2.tables/       # Tabelas e resultados exportados
└── 3.reports/      # Materiais finais de apresentação/relatório
```

## Como acompanhar o projeto

A ordem recomendada é:

1. Leia `4.docs/01_business_understanding.md` para entender o problema e os objetivos.
2. Execute `2.notebooks/1_data_understanding.ipynb` para validar a estrutura da base.
3. Execute `2.notebooks/2_eda.ipynb` para reproduzir a análise exploratória, correlações e pontos de ruptura.
4. Consulte `4.docs/03_conclusoes_eda.md` e `04_limitacoes_e_decisoes.md` para as principais conclusões e cuidados de interpretação.
5. Execute `2.notebooks/3_modeling.ipynb` para reproduzir a prova de conceito preditiva.
6. Consulte `4.docs/05_modelagem_preditiva.md` para o resumo do modelo e sua proposta de aplicação.

## Principais resultados

A análise identificou atraso na entrega e recorrência de reclamações como os principais sinais operacionais associados a notas mais baixas de NPS. Contatos recorrentes com atendimento também funcionam como sinal de uma jornada problemática.

A prova de conceito utiliza classificação binária para identificar risco de detrator. A Regressão Logística foi selecionada como modelo principal, com recall de 93% para detratores e ROC-AUC de 0,876 no conjunto de teste.

## Reprodutibilidade

Os notebooks devem ser executados na ordem indicada, a partir da pasta `2.notebooks`. A base original permanece em `1.data/1.raw`, enquanto arquivos derivados são gravados em `1.data/2.processed` e os resultados em `5.outputs`.

## Observações importantes

- `repeat_purchase_30d` não é utilizada como variável explicativa ou preditora devido à relação determinística identificada com o NPS.
- `csat_internal_score` é utilizado apenas como indicador complementar na EDA e foi excluído do modelo principal por falta de documentação sobre sua construção e momento de cálculo.
- Os resultados representam associações e uma prova de conceito. A base não permite demonstrar causalidade nem reproduzir completamente uma previsão em tempo real durante a jornada.
