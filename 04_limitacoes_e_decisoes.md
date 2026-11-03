# Limitações e decisões analíticas

Este documento registra os principais cuidados metodológicos identificados durante a análise e as decisões adotadas para evitar interpretações incorretas dos resultados.

## 1. Recompra em 30 dias

A variável `repeat_purchase_30d` apresentou uma relação determinística com o `nps_score`:

- clientes com NPS inferior a 8 possuem `repeat_purchase_30d = 0`;
- clientes com NPS igual ou superior a 8 possuem `repeat_purchase_30d = 1`.

Não foram encontradas exceções a essa regra na base analisada. Por esse motivo, a variável não foi utilizada para explicar o NPS e deverá ser excluída de uma eventual modelagem preditiva da satisfação, evitando vazamento de informação.

Também não é possível utilizar esta base para avaliar de forma independente se clientes mais satisfeitos apresentam maior probabilidade de recompra.

## 2. CSAT interno

O `csat_internal_score` apresentou associação positiva relevante com o NPS, porém a documentação fornecida informa apenas que se trata de um score interno de satisfação.

Não existem informações sobre sua fórmula, variáveis utilizadas ou momento de cálculo. Por isso:

- o CSAT foi mantido na análise exploratória como indicador complementar de satisfação;
- a associação com o NPS não foi interpretada como causalidade;
- seu uso em eventual modelo preditivo deverá ser avaliado com cautela, principalmente para evitar vazamento de informação.

## 3. Associação não representa causalidade

As correlações e comparações realizadas durante a EDA identificam associações entre variáveis, mas não demonstram relações de causa e efeito.

Por exemplo, atrasos maiores estão associados a NPS mais baixo, mas a análise realizada não permite afirmar isoladamente que o atraso seja a causa direta da nota atribuída pelo cliente.

Da mesma forma, o número de contatos com atendimento deve ser interpretado com cautela, pois apresentou forte associação com a quantidade de reclamações e pode representar a recorrência de problemas na jornada.

## 4. Pontos de ruptura

Os pontos de ruptura identificados representam referências exploratórias para o negócio, e não limites causais ou universais.

Foram considerados o comportamento do NPS, a variação entre níveis consecutivos e a quantidade de observações disponível em cada grupo. Resultados baseados em grupos com poucas observações foram tratados com cautela.

## 5. Classificação do NPS

A base possui notas decimais entre 0 e 10, enquanto a metodologia tradicional do NPS utiliza as categorias detratores, passivos e promotores a partir da escala de recomendação.

Para preservar essa lógica na base disponível, foram adotados os seguintes limites:

- `0 ≤ NPS ≤ 6`: Detrator;
- `6 < NPS ≤ 8`: Passivo;
- `8 < NPS ≤ 10`: Promotor.

A classificação foi aplicada somente após a exploração da variável em sua forma contínua, permitindo primeiro compreender a distribuição e o comportamento das notas.

## 6. Limitações dos dados

A análise está limitada às variáveis disponibilizadas no conjunto de dados. Não estão disponíveis informações detalhadas sobre o processo de geração da base, definição de alguns indicadores ou sequência temporal completa da jornada do cliente.

Essas limitações devem ser consideradas na interpretação dos resultados e, principalmente, antes da utilização das variáveis em modelos preditivos ou decisões operacionais automatizadas.
