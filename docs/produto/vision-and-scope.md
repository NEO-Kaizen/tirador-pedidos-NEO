# Visão, Problema e Escopo do Produto — Tirador de Pedidos do NEO

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | Tirador de Pedidos do NEO |
| Documento | `docs/produto/vision-and-scope.md` |
| Sprint | Sprint 1 |
| Time responsável | Produto |
| Status | Em revisão |
| Classificação | Restrito |
| Issue relacionada | #18, #21 |
| Épico relacionado | #19 |

## 1. Visão do produto

<p>O Tirador de Pedidos do NEO é uma aplicação web destinada a centralizar o recebimento, a organização, a triagem, a priorização e o acompanhamento de solicitações encaminhadas ao NEO — Núcleo de Eficiência Operacional.

A solução deve funcionar como ponto único de entrada para demandas destinadas ao NEO, reduzindo controles paralelos, planilhas descentralizadas e solicitações recebidas por diferentes canais.
</p>

## 2. Problema identificado

<p>Atualmente, o recebimento de demandas pelo NEO pode ocorrer de forma descentralizada, com registros em diferentes canais e controles paralelos. Isso gera dificuldade para:</p>

<ul>
    <li>visualizar todas as solicitações em um único lugar.</li>
    <li>priorizar demandas com critério claro.</li>
    <li>saber quem é o responsável por cada demanda.</li>
    <li>acompanhar o status de cada pedido.</li>
    <li>registrar pendências e próximas ações.</li>
    <li>manter histórico das alterações.</li>
    <li>gerar indicadores e exportações para análise.</li>
</ul>

<p>A ausência de um fluxo padronizado compromete a rastreabilidade, a transparência e a capacidade de gestão operacional do NEO.</p>

## 3. Objetivo da solução

<p>O objetivo da primeira versão do Tirador de Pedidos do NEO é disponibilizar uma solução web funcional, simples, rastreável e de fácil implantação, que permita:</p>

<ul>
    <li>registrar novas solicitações.</li>
    <li>gerar protocolo único.</li>
    <li>armazenar os dados da demanda.</li>
    <li>inserir automaticamente a solicitação na fila do NEO.</li>
    <li>classificar e priorizar demandas.</li>
    <li>atribuir manualmente um responsável.</li>
    <li>registrar manualmente o mapeamento.</li>
    <li>acompanhar status, pendências e próximos passos.</li>
    <li>manter histórico de movimentações.</li>
    <li>fornecer visão consolidada do backlog.</li>
    <li>exportar dados para análise e construção de indicadores.</li>
</ul>

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

## 5. Usuários iniciais

Em visão macro, o produto deve atender aos seguintes usuários:

| Usuário | Papel principal |
|---|---|
| Solicitante | Abre solicitação e acompanha o próprio pedido. |
| Analista/Mapeador | Conduz triagem, análise, mapeamento e atualização do andamento. |
| Administrador do NEO | Administra fila, parâmetros, categorias, responsáveis, exportações e auditoria. |
| Gestor/Visualizador | Consulta fila, indicadores e relatórios, sem alterar registros operacionais. |
| Admin Root | Perfil técnico adicional definido pelo time para administração técnica, suporte ou configuração inicial. |

**<p>Observação: a especificação técnica original prevê quatro perfis principais. O quinto perfil, Admin Root, foi incluído por decisão técnica do time e precisa ter limites claramente validados.</p>**

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
```

## 7.Referências

<ul>
    <li>Link do prototipo no figma:</li>
    https://www.figma.com/design/Z4Vhez5HFfolIv3uaMMyyF/NEO---Kaizen?node-id=1-2&p=f
</ul>
