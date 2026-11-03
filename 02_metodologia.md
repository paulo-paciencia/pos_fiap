# Metodologia

## 1. Abordagem adotada

O projeto foi conduzido com base no CRISP-DM, utilizando suas etapas como referência para organizar o entendimento do problema, a exploração dos dados e a preparação das próximas fases do trabalho.

Nesta primeira fase, o foco esteve principalmente em:

1. entendimento do negócio;
2. entendimento dos dados;
3. preparação dos dados necessária para a análise;
4. análise exploratória (EDA);
5. identificação dos principais fatores associados ao NPS.

A modelagem preditiva será tratada separadamente, após a consolidação dos resultados exploratórios.

## 2. Entendimento dos dados

A análise começou pela avaliação da estrutura da base, incluindo:

- quantidade de registros e variáveis;
- tipos de dados;
- valores ausentes;
- registros duplicados;
- quantidade de valores distintos;
- estatísticas descritivas iniciais.

Essa etapa teve como objetivo validar a qualidade e a consistência geral da base antes de iniciar análises mais detalhadas.

## 3. Exploração inicial do NPS

Antes de aplicar a classificação tradicional entre detratores, passivos e promotores, o `nps_score` foi analisado em sua forma original.

Foram avaliados:

- escala e granularidade das notas;
- média, mediana e dispersão;
- frequência das notas;
- formato da distribuição;
- assimetria;
- comportamento dos extremos.

Essa escolha permitiu compreender primeiro o comportamento dos dados sem impor categorias previamente definidas.

## 4. Faixas exploratórias

Para facilitar a comparação dos indicadores ao longo da escala, foi criada a variável `nps_faixa`, agrupando notas próximas.

As faixas foram utilizadas apenas como recurso exploratório. O objetivo foi observar como características de cliente, pedido, logística, atendimento e satisfação se comportavam à medida que o NPS aumentava.

Região e idade foram analisadas separadamente para verificar possíveis diferenças de perfil, mas não apresentaram evidências suficientes para serem priorizadas como fatores explicativos.

## 5. Análise de correlação

Foram utilizadas as correlações de Pearson e Spearman para avaliar a associação entre o NPS e as variáveis numéricas.

A correlação de Spearman foi utilizada como principal referência por permitir identificar relações monotônicas sem exigir uma relação perfeitamente linear. Pearson foi mantida como comparação complementar.

Variáveis de identificação e classificações criadas durante a análise foram excluídas dos cálculos.

A variável `repeat_purchase_30d` também foi retirada da análise explicativa após ser identificada uma relação determinística com o NPS.

## 6. Investigação dos pontos de ruptura

Depois da análise de correlação, foram aprofundados os indicadores operacionais com maior associação ao NPS:

- atraso na entrega;
- quantidade de reclamações;
- contatos com atendimento;
- tempo de resolução.

Para cada indicador foram avaliados:

- quantidade de clientes por nível;
- NPS médio e mediano;
- variação do NPS entre níveis consecutivos;
- representatividade dos grupos;
- comportamento de outros indicadores relacionados.

Os pontos identificados foram tratados como referências exploratórias e operacionais, e não como limites causais.

## 7. Relação entre indicadores operacionais

Foi utilizada uma matriz de correlação de Spearman entre os principais indicadores operacionais para avaliar possíveis sobreposições.

Essa análise permitiu diferenciar fatores com comportamento próprio de variáveis que representam aspectos relacionados da mesma jornada, como reclamações e contatos com atendimento.

## 8. Classificação final do NPS

Após a análise contínua e exploratória, foi criada a classificação de NPS utilizada na visão final do negócio:

- Detrator: notas até 6;
- Passivo: notas acima de 6 e até 8;
- Promotor: notas acima de 8.

A adaptação foi necessária porque a base possui notas decimais.

A classificação final foi utilizada para calcular o NPS geral e consolidar os resultados em uma visão mais próxima da aplicação gerencial da metodologia.

## 9. Organização dos resultados

Os dados originais foram preservados na pasta `data/raw`, enquanto a versão enriquecida com classificações derivadas foi armazenada em `data/processed`.

Os gráficos e tabelas produzidos pela EDA foram separados em `outputs`, mantendo os notebooks como registro reproduzível de todo o processo analítico.
