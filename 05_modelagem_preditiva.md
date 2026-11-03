# Modelagem preditiva

## 1. Objetivo

Foi desenvolvida uma prova de conceito para identificar clientes com risco de se tornarem detratores e apoiar a priorização de ações preventivas durante a jornada.

O modelo complementa os alertas operacionais identificados na EDA. A proposta não é apenas antecipar a nota do cliente, mas combinar sinais de risco para apoiar a atuação das áreas responsáveis pela experiência.

## 2. Variável alvo

O problema foi tratado como classificação binária:

- `1` = Detrator (`nps_score <= 6`);
- `0` = Não detrator (`nps_score > 6`).

## 3. Variáveis utilizadas

Foram utilizadas características do cliente, pedido, logística e atendimento que podem representar sinais da jornada.

Foram excluídos identificadores, o próprio NPS e suas variáveis derivadas. `repeat_purchase_30d` foi excluída devido à relação determinística identificada com o NPS. `csat_internal_score` também foi retirado do modelo principal, pois não há informação suficiente sobre sua construção e momento de disponibilidade.

## 4. Treino e teste

A base foi dividida em:

- 80% para treinamento;
- 20% para teste.

A separação foi estratificada pela variável alvo para preservar a proporção das classes.

## 5. Modelos avaliados

Foram comparados dois modelos:

- Regressão Logística;
- Random Forest.

A Regressão Logística foi escolhida como modelo principal por apresentar desempenho equivalente ou superior nas principais métricas, além de maior simplicidade e interpretabilidade para aplicação de negócio.

## 6. Resultado principal

A Regressão Logística apresentou:

- acurácia: **84%**;
- precision dos detratores: **87%**;
- recall dos detratores: **93%**;
- F1-score dos detratores: **90%**;
- ROC-AUC: **0,876**.

No conjunto de teste, o modelo identificou corretamente **345 dos 370 detratores**, deixando de identificar 25 casos.

A Random Forest apresentou desempenho semelhante, com recall de 94% para detratores e ROC-AUC de 0,864, sem ganho suficiente para justificar a maior complexidade nesta prova de conceito.

## 7. Aplicação prática

A proposta é utilizar o modelo como uma segunda camada de priorização:

1. indicadores operacionais geram sinais de alerta;
2. o modelo combina os sinais disponíveis;
3. cada cliente recebe uma probabilidade de se tornar detrator;
4. clientes com maior risco podem ser priorizados para atuação preventiva.

Exemplos de ações incluem priorização de entregas problemáticas, tratamento de reclamações recorrentes, escalonamento de atendimento e contato proativo.

## 8. Limitação

A base não possui a sequência temporal detalhada dos eventos da jornada. Algumas variáveis representam o resultado completo do processo.

Por isso, o modelo deve ser interpretado como uma prova de conceito. Em uma aplicação real, o risco deveria ser recalculado ao longo da jornada utilizando somente informações disponíveis no momento da previsão.
