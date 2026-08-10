# Visão, Problema e Escopo do Produto — Tirador de Pedidos do NEO

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | Tirador de Pedidos do NEO |
| Documento | `docs/produto/visao-e-escopo.md` |
| Sprint | Sprint 1 |
| Time responsável | Produto |
| Status | Em revisão? |
| Classificação | Restrito |
| Issue relacionada | ? |
| Épico relacionado | ? |

---

## 1. Visão do produto

O Tirador de Pedidos do NEO é uma aplicação web destinada a centralizar o recebimento, a organização, a triagem, a priorização e o acompanhamento de solicitações encaminhadas ao NEO — Núcleo de Eficiência Operacional.

A solução deve funcionar como ponto único de entrada para demandas destinadas ao NEO, reduzindo controles paralelos, planilhas descentralizadas e solicitações recebidas por diferentes canais.

---

## 2. Problema identificado

Atualmente, o recebimento de demandas pelo NEO pode ocorrer de forma descentralizada, com registros em diferentes canais e controles paralelos. Isso gera dificuldade para:

- visualizar todas as solicitações em um único lugar;
- priorizar demandas com critério claro;
- saber quem é o responsável por cada demanda;
- acompanhar o status de cada pedido;
- registrar pendências e próximas ações;
- manter histórico das alterações;
- gerar indicadores e exportações para análise.

A ausência de um fluxo padronizado compromete a rastreabilidade, a transparência e a capacidade de gestão operacional do NEO.

---

## 3. Objetivo da solução

O objetivo da primeira versão do Tirador de Pedidos do NEO é disponibilizar uma solução web funcional, simples, rastreável e de fácil implantação, que permita:

- registrar novas solicitações;
- gerar protocolo único;
- armazenar os dados da demanda;
- inserir automaticamente a solicitação na fila do NEO;
- classificar e priorizar demandas;
- atribuir manualmente um responsável;
- registrar manualmente o mapeamento;
- acompanhar status, pendências e próximos passos;
- manter histórico de movimentações;
- fornecer visão consolidada do backlog;
- exportar dados para análise e construção de indicadores.

---

## 4. Proposta de valor

| Valor entregue | Resultado esperado |
|---|---|
| Padronização | Recebimento de demandas com campos e regras comuns. |
| Centralização | Fila única para acompanhamento operacional. |
| Rastreabilidade | Histórico de mudanças e responsáveis. |
| Gestão | Visão de status, prioridades, pendências e responsáveis. |
| Transparência | Consulta do andamento pelo solicitante. |
| Dados estruturados | Base para indicadores e análises. |
| Evolução | Arquitetura preparada para integrações futuras. |

---

## 5. Usuários iniciais

Em visão macro, o produto deve atender aos seguintes usuários:

| Usuário | Papel principal |
|---|---|
| Solicitante | Abre solicitação e acompanha o próprio pedido. |
| Analista/Mapeador | Conduz triagem, análise, mapeamento e atualização do andamento. |
| Administrador do NEO | Administra fila, parâmetros, categorias, responsáveis, exportações e auditoria. |
| Gestor/Visualizador | Consulta fila, indicadores e relatórios, sem alterar registros operacionais. |
| Admin Root | Perfil técnico adicional definido pelo time para administração técnica, suporte ou configuração inicial. |

> Observação: a especificação técnica original prevê quatro perfis principais. O quinto perfil, Admin Root, foi incluído por decisão técnica do time e precisa ter limites claramente validados.

---

## 6. Fluxo macro do produto

O fluxo principal conhecido é:

```text
Acesso à aplicação
→ Preenchimento da solicitação
→ Geração do protocolo
→ Entrada na fila
→ Triagem
→ Priorização
→ Atribuição de responsável
→ Registro do mapeamento
→ Acompanhamento
→ Encerramento