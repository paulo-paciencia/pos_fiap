# Conclusões da Análise Exploratória dos Dados (EDA)

## 1. Resultado geral do NPS

A base analisada possui 2.500 registros. Após a aplicação da classificação do NPS, foram identificados:

- **74,04% de detratores** (1.851 clientes);
- **17,92% de passivos** (448 clientes);
- **8,04% de promotores** (201 clientes).

O **NPS geral foi de -66 pontos**, indicando uma participação de detratores muito superior à de promotores na base analisada.

## 2. Principais fatores associados ao NPS

As análises por faixas e as correlações mostraram que os fatores operacionais com maior associação ao NPS foram:

- **Atraso na entrega:** apresentou a maior associação operacional com o NPS. Quanto maior o atraso, menor tende a ser a nota.
- **Quantidade de reclamações:** apresentou relação negativa relevante e progressiva com o NPS.
- **Contatos com o atendimento:** clientes com maior número de contatos tendem a apresentar NPS mais baixo. Entretanto, essa variável possui forte relação com a quantidade de reclamações.
- **Tempo de resolução:** apresentou associação negativa mais fraca e sem um ponto de ruptura claro.

O `csat_internal_score` apresentou associação positiva com o NPS e foi mantido como indicador complementar de satisfação. Entretanto, sua forma e momento de cálculo não estão documentados na base.

## 3. Pontos de ruptura e níveis críticos

### Atraso na entrega

A deterioração da satisfação começa já no primeiro dia de atraso. Não foi identificado um único ponto de ruptura, mas atrasos de **três dias ou mais** se mostraram um nível operacional crítico, associado a NPS médio significativamente mais baixo.

### Reclamações

A maior queda relevante ocorreu entre a primeira e a segunda reclamação. Dessa forma, a **segunda reclamação** foi identificada como um possível ponto de ruptura. A partir de três reclamações, o NPS médio já se encontra abaixo de 5.

### Contatos com atendimento

A redução do NPS começa desde o primeiro contato e permanece progressiva. O terceiro contato pode ser tratado como um nível de atenção operacional, pois está associado a uma satisfação consideravelmente mais baixa.

### Tempo de resolução

O NPS diminui gradualmente à medida que aumenta o tempo de resolução, porém não foi identificado um limite específico que caracterize uma ruptura clara.

## 4. Perfil do cliente

As análises de região e faixa etária não mostraram diferenças suficientemente fortes para serem priorizadas como fatores explicativos do NPS.

Os resultados indicam que, nesta base, as características da experiência operacional possuem maior associação com a satisfação do que as características demográficas avaliadas.

## 5. Principais interpretações de negócio

O **tempo total de entrega apresentou associação praticamente nula com o NPS**, enquanto o atraso em relação ao prazo apresentou uma das maiores associações negativas.

Esse resultado sugere que o cumprimento do prazo esperado é mais relevante para a satisfação do cliente do que a duração absoluta da entrega.

Também foi identificada forte relação entre reclamações e contatos com atendimento. Por isso, o número de contatos deve ser interpretado principalmente como um sinal de recorrência ou continuidade de problemas na jornada, e não como uma causa isolada da insatisfação.

## 6. Recomendações iniciais

Com base nos resultados da EDA, as principais frentes de atenção são:

1. **Priorizar o cumprimento dos prazos de entrega**, atuando preventivamente sobre pedidos com risco de atraso.
2. **Criar alertas para clientes que registrarem uma segunda reclamação**, evitando a recorrência do problema.
3. **Priorizar clientes com múltiplos contatos com atendimento**, principalmente a partir do terceiro contato.
4. **Monitorar o tempo de resolução**, mesmo não tendo sido identificado um ponto de ruptura específico.
5. Utilizar os indicadores operacionais em conjunto para identificar jornadas com maior risco de insatisfação.

## 7. Limitações relevantes

A análise identificou uma relação determinística entre `repeat_purchase_30d` e o NPS: todos os clientes com NPS inferior a 8 foram classificados como não recompra, enquanto todos os clientes com NPS igual ou superior a 8 foram classificados como recompra. Por esse motivo, essa variável não foi utilizada como fator explicativo.

O `csat_internal_score` apresentou associação relevante com o NPS, porém não existem informações suficientes sobre sua construção ou momento de cálculo. Seu uso em uma eventual modelagem preditiva deve ser avaliado com cautela.

Por fim, as relações identificadas nesta EDA representam **associações estatísticas e padrões descritivos**, não evidências de causalidade.
