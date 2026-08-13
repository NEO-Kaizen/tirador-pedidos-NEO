# Ciclo de Vida e Fluxos Funcionais — Tirador de Pedidos do NEO

Este documento apresenta a visão macro dos fluxos funcionais e do ciclo de vida das solicitações enviadas ao **Tirador de Pedidos do NEO** (Núcleo de Eficiência Operacional). Ele estabelece a organização dos processos que gerenciam a entrada de demandas, sua triagem, priorização, agendamento de reuniões e encerramento.

## 1. Visão Macro do Ciclo de Vida da Demanda

O Tirador de Pedidos atua como ponto único de entrada para solicitações operacionais direcionadas ao NEO. O fluxo transita desde a recepção dos dados públicos até as etapas administrativas internas, mantendo o histórico de auditoria imutável.

---

## 2. Matriz de Atores e Responsabilidades

Com base no mapeamento de casos de uso do sistema, as responsabilidades de cada perfil estão definidas abaixo:

| Atividade / Funcionalidade           | Solicitante | Analista | Administrador | Gestor |
| :----------------------------------- | :---------: | :------: | :-----------: | :----: |
| **Cadastrar Solicitação**            |    **A**    |    C     |       C       |   I    |
| **Consultar Protocolo**              |    **A**    |    C     |       C       |   I    |
| **Acompanhar Status Público**        |    **A**    |    C     |       C       |   I    |
| **Visualizar/Sanar Pendências**      |    **A**    |    C     |       C       |   I    |
| **Consultar Fila Centralizada**      |      -      |  **A**   |     **A**     |   I    |
| **Executar Triagem & Elegibilidade** |      -      |  **A**   |     **A**     |   -    |
| **Cálculo de Priorização & Score**   |      -      |  **A**   |     **A**     |   -    |
| **Atribuir Responsável Técnico**     |      -      |    -     |     **A**     |   -    |
| **Registrar Mapeamento Manual**      |      I      |  **A**   |     **A**     |   -    |
| **Gerenciar Parâmetros do Sistema**  |      -      |    -     |     **A**     |   -    |
| **Exportar Dados e Logs**            |      -      |    -     |     **A**     | **A**  |
| **Visualizar Histórico & Auditoria** |      -      |    -     |     **A**     |   I    |

_Legenda: **A** = Responsável por executar (Accountable/Responsible) | **C** = Consultado (Consulted) | **I** = Informado (Informed)._

---

## 3. Matriz de Status da Solicitação

O sistema utiliza um fluxo padronizado contendo **17 status** para garantir rastreabilidade contínua. A tabela abaixo indica a visibilidade pública para o solicitante e as transições esperadas:

| Ordem  | Status Técnico              | Próximo Passo Esperado                          | Origem da Mudança                                |
| :----: | :-------------------------- | :---------------------------------------------- | :----------------------------------------------- |
| **1**  | Solicitação enviada         | Aguardando início da triagem técnica            | Automático via envio do formulário               |
| **2**  | Aguardando triagem          | Aguardando alocação de analista de triagem      | Transição pelo sistema                           |
| **3**  | Em triagem                  | Analista revisando informações enviadas         | Manual pelo Analista/Admin                       |
| **4**  | Pendente de informações     | Solicitante deve responder pendência em tela    | Manual pelo Analista/Admin                       |
| **5**  | Aguardando mapeamento       | Analista entrará em contato para agendar        | Manual pelo Analista após elegibilidade          |
| **6**  | Mapeamento agendado         | Reunião de mapeamento agendada com solicitante  | Manual pelo Analista após acerto de agenda       |
| **7**  | Em mapeamento               | Reunião e análise de processos em andamento     | Manual pelo Analista                             |
| **8**  | Em análise de viabilidade   | Avaliação de escopo e esforço de entrega        | Manual pelo Analista                             |
| **9**  | Elegível                    | Demanda validada e qualificada para priorização | Manual pelo Analista/Admin                       |
| **10** | Não elegível                | Demanda encerrada (com justificativa de recusa) | Manual pelo Analista (Justificativa obrigatória) |
| **11** | Priorizado                  | Alocado no backlog priorizado do NEO            | Manual pelo Admin (pós-priorização)              |
| **12** | Backlog                     | Demanda no banco de ideias para execução futura | Manual pelo Admin                                |
| **13** | Direcionado para outra área | Direcionado para a área competente externa      | Manual pelo Analista (Justificativa obrigatória) |
| **14** | Em desenvolvimento          | Construção da solução técnica em progresso      | Manual pelo Analista/Admin                       |
| **15** | Em homologação              | Solicitante testando a solução entregue         | Manual pelo Analista/Admin                       |
| **16** | Concluído                   | Solução implantada e homologada com sucesso     | Manual pelo Analista/Admin                       |
| **17** | Cancelado                   | Solicitação cancelada pelo usuário ou equipe    | Manual pelo Analista/Admin                       |

---

## 5. Indice de Documentos de Fluxo

Para acessar o detalhamento funcional individual de cada jornada de uso, consulte os documentos a seguir:

1.  **[Criação de Solicitação](./criacao-de-solicitacao.md):** Fluxo de preenchimento, validação e abertura de demandas pelo Solicitante.
2.  **[Consulta de Solicitação](./consulta-de-solicitacao.md):** Fluxo que permite ao solicitante acompanhar o andamento da sua demanda.
3.  **[Logins e Perfis](./login-e-perfis.md):** Fluxo que estabelece o mecanismo de controle de segurança, autenticação e autorização de acesso
4.  **[Triagem e Priorizacao](./triagem-e-priorizacao.md):** Fluxo utilizado pela equipe interna para avaliar, classificar, dimensionar a prioridade de atendimento e alocar recursos para cada solicitação recebida.
5.  **[Registro de Mapeamento](./registro-de-mapeamento.md):** Fluxo administrativo interno que realiza a gestão, o agendamento e o controle manual das reuniões técnicas.
6.  **[Gerenciamento de Configuracoes](./gerenciamento-de-configuracoes.md):** Fluxo de navegação do painel de Configurações e Parâmetros.
