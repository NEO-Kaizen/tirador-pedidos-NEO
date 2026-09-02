# Regras de SLA das Solicitações

**Issue:** [#32 — PRODUTO - Refinar regras de SLA das solicitações](https://github.com/NEO-Kaizen/tirador-pedidos-NEO/issues/32)

**Responsável:** Time de Produto
**Status:** Em revisão
**Arquivo:** `docs/produto/regras-sla.md`

---

## 1. Objetivo

Definir as regras de SLA das solicitações, estabelecendo os prazos de atendimento de acordo com a prioridade e as condições de início, pausa, retomada e encerramento da contagem.

Também são definidos os gatilhos visuais utilizados para indicar a situação do SLA na interface.

Os valores apresentados neste documento são uma **proposta inicial do Time de Produto** e deverão ser validados com o Cliente antes da implementação.

---

## 2. Contexto

O protótipo de alta fidelidade prevê a exibição de um contador de SLA, como:

```text
SLA: 48h restantes
```

Para que esse contador possa funcionar corretamente, é necessário definir as regras de negócio responsáveis pela contagem do tempo.

A principal preocupação é garantir que o SLA não penalize a equipe interna quando o andamento da solicitação depender do Solicitante.

---

## 3. Unidade de contagem

A proposta é utilizar **horas úteis** para a contagem do SLA.

Como referência para o MVP:

* segunda-feira a sexta-feira;
* 8 horas úteis por dia;
* finais de semana não são contabilizados.

O horário exato de funcionamento e o tratamento de feriados deverão ser validados com o Cliente.

---

## 4. Matriz de SLA

Os prazos abaixo são uma proposta inicial do Time de Produto.

| Etapa       | Baixa | Média | Alta | Crítica |
| ----------- | ----: | ----: | ---: | ------: |
| Triagem     |   40h |   24h |  16h |      8h |
| Mapeamento  |   80h |   56h |  40h |     24h |
| Homologação |   40h |   24h |  16h |      8h |

Considerando 8 horas úteis por dia:

| Etapa       |   Baixa |  Média |   Alta | Crítica |
| ----------- | ------: | -----: | -----: | ------: |
| Triagem     |  5 dias | 3 dias | 2 dias |   1 dia |
| Mapeamento  | 10 dias | 7 dias | 5 dias |  3 dias |
| Homologação |  5 dias | 3 dias | 2 dias |   1 dia |

A prioridade mais alta possui menor prazo de atendimento.

> **Observação:** Homologação foi incluída por ser uma das etapas citadas no escopo da Issue #32. Sua permanência na matriz deve ser confirmada junto ao fluxo final da solicitação.

---

## 5. Início da contagem

O SLA começa quando a solicitação entra na etapa correspondente.

| Etapa       | Início da contagem                 |
| ----------- | ---------------------------------- |
| Triagem     | Entrada na fila de triagem         |
| Mapeamento  | Entrada em `Aguardando mapeamento` |
| Homologação | Entrada em `Em homologação`        |

O prazo utilizado deve considerar a prioridade da solicitação no momento do início da etapa.

---

## 6. Pausa do SLA

O SLA deve ser pausado quando o andamento da solicitação depender de informações ou ações do Solicitante.

### Status de pausa

| Status                    | Pausa o SLA? | Motivo                                |
| ------------------------- | ------------ | ------------------------------------- |
| `Pendente de informações` | Sim          | A continuidade depende do Solicitante |

Durante a pausa:

* o contador deixa de avançar;
* o tempo já consumido é preservado;
* o período em pausa não é contabilizado no SLA.

Exemplo:

```text
SLA: 24h restantes
SLA pausado — aguardando informações
```

---

## 7. Retomada do SLA

Quando o Solicitante fornecer as informações necessárias, a contagem deve ser retomada.

O tempo utilizado antes da pausa deve ser preservado.

**O SLA não deve ser reiniciado do zero após uma pausa.**

Exemplo:

```text
SLA inicial: 24h
Tempo utilizado antes da pausa: 6h
Tempo restante: 18h

Solicitação pausada → Solicitante responde → SLA retoma com 18h restantes
```

---

## 8. Encerramento do SLA

O SLA deve ser encerrado definitivamente quando a solicitação atingir um status que finalize sua participação no fluxo.

| Status                        | Encerra o SLA? |
| ----------------------------- | -------------- |
| `Concluído`                   | Sim            |
| `Cancelado`                   | Sim            |
| `Não elegível`                | Sim            |
| `Direcionado para outra área` | Sim            |

O histórico da solicitação deve permitir consultar o prazo aplicado, o tempo consumido, os períodos de pausa e a situação do SLA no encerramento.

---

## 9. Backlog

Solicitações em `Backlog` não possuem SLA operacional ativo.

A contagem deve começar somente quando a solicitação entrar em uma etapa que possua SLA definido.

---

## 10. Gatilhos visuais

O indicador visual do SLA deve considerar o percentual do prazo já consumido.

| Indicador | Percentual do SLA consumido | Significado           |
| --------- | --------------------------: | --------------------- |
| Verde     |                    0% a 69% | Dentro do prazo       |
| Amarelo   |                   70% a 99% | Próximo do vencimento |
| Vermelho  |                100% ou mais | SLA vencido           |

Quando o SLA estiver pausado, a interface deve indicar essa situação por meio de texto, por exemplo:

```text
SLA pausado
```

---

## 11. Contador de SLA

O contador deve apresentar o tempo restante da etapa atual.

Exemplos:

```text
SLA: 48h restantes
```

```text
SLA: 5h restantes
```

Quando o prazo for ultrapassado:

```text
SLA vencido
```

Quando estiver pausado:

```text
SLA pausado
```

O contador deve acompanhar a situação atual do SLA, considerando períodos ativos e pausados.

---

## 12. Histórico

O histórico da solicitação deve permitir identificar os principais eventos relacionados ao SLA:

* início da contagem;
* pausa;
* retomada;
* alteração de prioridade, quando ocorrer;
* encerramento.

Essas informações devem permitir consultar o comportamento do SLA durante o ciclo da solicitação.

---

## 13. Fora do escopo

Não fazem parte desta especificação:

* implementação das rotinas de Banco de Dados;
* cronjobs;
* disparo automático de e-mails;
* alertas automáticos;
* contratos jurídicos ou operacionais externos de SLA.

Este documento define as regras de Produto que deverão orientar a implementação.

---

## 14. Critérios de aceite

* [x] Matriz de SLA definida para prioridades Baixa, Média, Alta e Crítica.
* [x] Prazos definidos para Triagem, Mapeamento e Homologação.
* [x] Status que pausam o SLA identificados.
* [x] `Pendente de informações` definido como status de pausa.
* [x] Regra de retomada após resposta do Solicitante definida.
* [x] Status que encerram definitivamente o SLA identificados.
* [x] Gatilhos visuais definidos para Verde, Amarelo e Vermelho.
* [x] Comportamento do contador de SLA definido.
* [x] Regras básicas de histórico documentadas.
* [ ] Proposta validada pelo Time de Produto/PO.
* [ ] Regras validadas com o Cliente.
* [ ] Viabilidade técnica confirmada.

---

## 15. Pontos para validação

Antes da implementação, devem ser validados:

| Ponto               | Proposta                                                         |
| ------------------- | ---------------------------------------------------------------- |
| Unidade de contagem | Horas úteis                                                      |
| Jornada considerada | 8h por dia útil                                                  |
| Prazos da matriz    | Conforme seção 4                                                 |
| Pausa               | `Pendente de informações`                                        |
| Retomada            | Continua de onde parou                                           |
| Backlog             | Sem SLA ativo                                                    |
| Alerta amarelo      | 70% do prazo consumido                                           |
| Alerta vermelho     | 100% do prazo consumido                                          |
| Encerramento        | `Concluído`, `Cancelado`, `Não elegível` e saída para outra área |

Os valores e regras poderão ser ajustados após a validação.

---

## 16. Referências

* Issue #32 — `PRODUTO - Refinar regras de SLA das solicitações`.
* Protótipo de alta fidelidade — seção de detalhes da demanda com contador de SLA.
* Especificação Técnica — Tirador de Pedidos do NEO.

---

## 17. Observação final

A regra mais importante desta especificação é:

> **Quando o andamento da solicitação depender do Solicitante, o SLA deve ser pausado para que o período de espera não penalize a produtividade da equipe interna.**

Os prazos apresentados neste documento são uma proposta inicial do Time de Produto e estão sujeitos à validação antes da implementação.
