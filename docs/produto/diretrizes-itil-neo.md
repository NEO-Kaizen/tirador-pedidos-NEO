### Diretrizes de Governança de Serviços de TI — Alinhamento ITIL v4

#### 1. Introdução e Justificativa de Governança

O **Portal NEO** atua como o ponto único de entrada para requisições de melhorias e automações operacionais no Núcleo de Eficiência Operacional. O objetivo deste documento é consolidar as diretrizes funcionais e terminologias de mercado herdadas da biblioteca de melhores práticas **ITIL v4** (_Information Technology Infrastructure Library_), aplicando-as de forma leve ao ciclo de vida das solicitações do NEO.

Diferente de softwares de ITSM tradicionais (como o GLPI) que sobrecarregam o usuário final com taxonomias complexas, telas poluídas e burocracia excessiva, o **Tirador de Pedidos NEO** adota uma postura ágil e focada em valor. O alinhamento com o ITIL v4 serve para:

1. **Elevar a maturidade operacional** do time do NEO sem comprometer a simplicidade do MVP.
2. **Garantir conformidade e rastreabilidade** em auditorias externas de governança de TI corporativa, utilizando termos reconhecidos globalmente.
3. **Formalizar papéis operacionais e de liderança** no fluxo, permitindo que a transição de responsabilidades ocorra sem gargalos ou conflitos de custódia.

---

#### 2. Mapeamento do Fluxo do NEO vs. Práticas ITIL v4

Oo macro do Tirador de Pedidos NEO (Acesso -> Abertura -> Triagem -> Priorização -> Mapeamento -> Encerramento) está formalmente correlacionado a práticas estruturadas do ITIL v4. Esta correlação garante que cada funcionalidade da plataforma responda a um propósito de governança claro.

```mermaid
flowchart TD
    subgraph Jornada_Solicitante [Jornada do Solicitante]
        A[Abertura de Demanda] -->|Acesso Público| B[Acompanhamento]
    end

    subgraph Praticas_ITIL [Práticas ITIL v4]
        C[Gerenciamento de\nRequisições de Serviço]
        D[Service Desk\nCentralizado]
        E[Gerenciamento de\nMelhoria Contínua]
        F[Análise de Negócio\n& Diagnóstico]
        SLM[Gerenciamento de\nNível de Serviço - SLM]
    end

    subgraph Operacao_NEO [Operação Interna NEO]
        G[Triagem do Pedido] --> H[Calculadora de Score]
        H --> I[Registro de Mapeamento]
    end

    A -.->|Correlacionado a| C
    B -.->|Apoiado por| D
    G -.->|Operacionaliza| D
    H -.->|Fundamentado em| E
    I -.->|Alinhado a| F
    G -.->|Regulado por| SLM
    I -.->|Regulado por| SLM
```

##### 2.1. Abertura de Solicitação Pública $\rightarrow$ Prática: Gerenciamento de Requisições de Serviço (_Service Request Management_)

A jornada inicia-se no formulário público estruturado em blocos de dados. No ITIL v4, uma **Requisição de Serviço** é um pedido de um usuário para iniciar uma ação de serviço (neste caso, uma melhoria ou automação operacional).

- **Aplicação Prática no NEO:** A abertura pública livre elimina a necessidade de autenticação prévia (sem senhas para o MVP), agilizando o ponto de contato inicial.
- **Dados Coletados:** Estrutura-se no fornecimento de dados divididos em Blocos: Identificação (quem pede), Identificação da Demanda (o que pede), Informações Operacionais (métricas de esforço e frequência) e Informações Complementares.
- **Valor de Governança:** Garante a padronização na entrada de dados, forçando o solicitante a detalhar o processo atual, sistemas envolvidos e volumetria aproximada antes que a demanda seja analisada.

##### 2.2. Acompanhamento e Triagem na Prática: Central de Serviços (_Service Desk_)

A triagem atua como o filtro centralizado das demandas que chegam à fila do NEO. A Central de Serviços, segundo o ITIL v4, é o ponto de comunicação entre o provedor de serviços e seus usuários.

- **Aplicação Prática no NEO:** O painel público de acompanhamento por chave dupla de validação (Protocolo + E-mail) fornece visibilidade em tempo real ao Solicitante sobre pendências abertas, data prevista de mapeamento e status, mantendo dados confidenciais (comentários internos e score de prioridade) protegidos e privados.
- **Módulo Administrativo:** A Fila Centralizada consolida as demandas e permite ao Analista realizar buscas rápidas e avaliações de elegibilidade.

##### 2.3. Mapeamento de Processos na Prática: Análise de Negócio (_Business Analysis_)

No ITIL v4, a prática de Análise de Negócio foca na identificação e definição de soluções para problemas de negócios de maneira a maximizar o valor entregue às partes interessadas.

- **Aplicação Prática no NEO:** Representado pelo fluxo de **Registro de Mapeamento**. Como o sistema atua como um repositório declarativo, o analista realiza as reuniões externamente (Teams/Outlook) e registra os dados de diagnósticos e alinhamentos na plataforma, utilizando templates dinâmicos de e-mail integrados à área de transferência para otimizar o tempo operacional de comunicação.

##### 2.4. Priorização de Demandas na Prática: Gerenciamento de Melhoria Contínua (_Continual Improvement_) e Gerenciamento de Portfólio

O ITIL v4 posiciona a Melhoria Contínua como uma prática vital para manter os serviços eficientes. O repositório de demandas do NEO atua conceitualmente como o **Registro de Melhoria Contínua (CIR - Continual Improvement Register)** corporativo, centralizando todas as propostas de otimização de fluxos de trabalho da organização.

- **Aplicação Prática no NEO:** A **Calculadora de Score por Média Ponderada** quantifica objetivamente a relevância de cada demanda com base em critérios de negócio estruturados, fornecendo prioridades automáticas e auditáveis.

---

#### 3. Gestão de Melhoria Contínua: Critérios e Calculadora de Score

Pue a triagem não dependa de percepções puramente subjetivas da equipe técnica, a calculadora de score operacionaliza o alinhamento estratégico e a análise de valor preconizados pelo ITIL v4. O score de 10 a 50 pontos classifica as solicitações automaticamente em faixas fixas de classificação (Baixa, Média, Alta ou Crítica).

A tabela abaixo correlaciona os **10 critérios de negócio da calculadora do NEO** com os pilares conceituais do ITIL v4 para demonstrar como o algoritmo reflete a geração de valor operacional.

| Critério de Negócio do NEO  | Pontuação (1 a 5) | Peso Padrão | Pilar Conceitual ITIL v4    | Justificativa de Alinhamento de Governança                                                                                |
| --------------------------- | ----------------- | ----------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Alinhamento Estratégico** | 1 a 5             | 1           | Co-criação de Valor         | Avalia se a automação ou melhoria apoia diretamente os objetivos estratégicos anuais da corporação.                       |
| **Impacto Operacional**     | 1 a 5             | 1           | Eficiência e Utilidade      | Mede a abrangência e relevância das melhorias propostas na rotina produtiva diária dos colaboradores.                     |
| **Impacto no Cliente**      | 1 a 5             | 1           | Foco no Valor (End-User)    | Verifica o nível de benefício final ou percepção de valor gerado para o cliente externo da Toyota/NEO.                    |
| **Volumetria**              | 1 a 5             | 1           | Otimização e Automação      | Quantifica a escala de repetição do processo analisado (número de transações ou registros processados/mês).               |
| **Esforço Manual**          | 1 a 5             | 1           | Eliminação de Desperdício   | Avalia a carga horária de trabalho manual rotineiro que atualmente é despendida pela equipe do solicitante.               |
| **Urgência**                | 1 a 5             | 1           | Gestão de Portfólio e Tempo | Determina a janela de oportunidade ou necessidade temporal de atendimento antes de afetar as operações.                   |
| **Prazo Regulatório**       | 1 a 5             | 1           | Riscos e Conformidade       | Pondera se a ausência da melhoria gera multas, inconformidades contratuais ou riscos regulatórios.                        |
| **Risco Operacional**       | 1 a 5             | 1           | Gestão de Riscos            | Mede a probabilidade de ocorrência de erros graves, fraudes ou retrabalhos caso o processo permaneça como está.           |
| **Áreas Impactadas**        | 1 a 5             | 1           | Integração Organizacional   | Avalia a quantidade de departamentos ou filiais diferentes que se beneficiarão diretamente da entrega.                    |
| **Complexidade Estimada**   | 1 a 5             | 1           | Custos e Viabilidade        | Funciona como o moderador técnico. Um processo extremamente complexo exige mais esforço e reduz o retorno de curto prazo. |

##### Fórmula de Estabilidade ITIL

A fórmula matemática implementada garante conformidade mesmo que o Administrador altere os pesos dos critérios dinamicamente no painel de configurações:
$$\text{Score Final} = \left( \frac{\sum_{i=1}^{10} (\text{Nota}_i \times \text{Peso}_i)}{\sum_{i=1}^{10} \text{Peso}_i} \right) \times 10$$
Essa normalização matemática mantém a pontuação estritamente na faixa de **10.0 a 50.0**, assegurando que auditorias possam confiar nas faixas de classificação históricas, independentemente de mudanças conjunturais na parametrização de importância de cada critério.

---

#### 4. Matriz RACI de Responsabilidades (Alinhamento ITIL)

Para eliminar conflitos de responsabilidade e estabelecer uma linha clara de prestação de contas, a matriz **RACI** (_Responsible, Accountable, Consulted, Informed_) abaixo define o papel de cada perfil operacional do NEO em cada etapa crítica do ciclo de vida.

- **R - Responsible (Executor):** Quem executa diretamente a tarefa.
- **A - Accountable (Responsável Final/Aprovador):** Quem responde pela decisão e possui autoridade final de aprovação (somente uma pessoa por atividade).
- **C - Consulted (Consultado):** Quem fornece informações, pareceres ou insumos vitais para a execução da tarefa.
- **I - Informed (Informado):** Quem precisa ser atualizado sobre os resultados ou status da atividade.

##### Matriz de Papéis do NEO

| Etapa Operacional / Atividade                   | Solicitante        | Analista / Mapeador | Administrador do NEO | Gestor / Visualizador | Admin Root (Técnico) |
| ----------------------------------------------- | ------------------ | ------------------- | -------------------- | --------------------- | -------------------- |
| **Abertura de nova solicitação**                | **A** / **R**      | I                   | I                    | I                     | I                    |
| **Triagem e análise de elegibilidade**          | I                  | **R**               | **A**                | I                     | I                    |
| **Avaliação e cálculo do Score de Prioridade**  | I                  | **R**               | **A**                | I                     | I                    |
| **Definição/Atribuição de Responsável Técnico** | I                  | I                   | **A** / **R**        | I                     | I                    |
| **Agendamento e registro do Mapeamento**        | C                  | **R**               | **A**                | I                     | I                    |
| **Alteração de Status das Demandas**            | I                  | **R** (com limites) | **A** (irrestrito)   | I                     | I                    |
| **Edição de Categorias e Parâmetros globais**   | I                  | I                   | **A** / **R**        | I                     | I                    |
| **Criação de Contas de Usuários**               | I                  | I                   | **R**                | I                     | **A**                |
| **Visualização de KPIs e Relatórios**           | I (apenas próprio) | **R** (atribuídas)  | **R** (total)        | **R** (total)         | I                    |
| **Consulta de Histórico de Auditoria**          | I (apenas próprio) | **C**               | **A** / **R**        | I                     | I                    |

---

#### 5. Gestão de Nível de Serviço: Regras e Acordos de SLA (Alinhamento ITIL SLM)

A prática de **Gerenciamento de Nível de Serviço (_Service Level Management - SLM_)** do ITIL v4 visa definir, monitorar e gerenciar metas realistas e focadas em valor para o atendimento dos usuários. No Tirador de Pedidos NEO, essa prática é operacionalizada de forma ágil através de regras claras baseadas em **horas úteis** e no status de colaboração do solicitante.

Isso impede que a equipe técnica seja indevidamente penalizada quando o andamento de uma solicitação depender de uma ação ou resposta do usuário.

##### 5.1. Unidade de Contagem Operacional

Para garantir um alinhamento realista com a capacidade de entrega e o horário comercial da empresa, a contagem de SLA adota o seguinte padrão para o MVP:

- **Unidade de Medida:** Horas úteis (segunda-feira a sexta-feira).
- **Jornada de Trabalho:** 8 horas úteis por dia útil.
- **Exclusões:** Finais de semana e feriados nacionais não entram no cômputo da contagem.

##### 5.2. Matriz de SLA do NEO por Etapa e Prioridade

O prazo de SLA é inversamente proporcional à prioridade atribuída à demanda (calculada de forma automatizada na Seção 3 através da Calculadora de Score). Quanto mais alta a prioridade, menor o prazo de atendimento.

A matriz de SLA proposta engloba três etapas fundamentais do ciclo de vida:

| Etapa Operacional | Baixa (Score 10-19) | Média (Score 20-29) | Alta (Score 30-39) | Crítica (Score 40-50) |
| :---------------- | :------------------ | :------------------ | :----------------- | :-------------------- |
| **Triagem**       | 40h úteis (5 dias)  | 24h úteis (3 dias)  | 16h úteis (2 dias) | 8h úteis (1 dia)      |
| **Mapeamento**    | 80h úteis (10 dias) | 56h úteis (7 dias)  | 40h úteis (5 dias) | 24h úteis (3 dias)    |
| **Homologação**   | 40h úteis (5 dias)  | 24h úteis (3 dias)  | 16h úteis (2 dias) | 8h úteis (1 dia)      |

_Nota: Prazos expressos considerando uma jornada padrão de 8 horas úteis por dia._

##### 5.3. Ciclo de Vida da Contagem (Início, Pausa, Retomada e Encerramento)

O comportamento do contador de SLA varia dinamicamente ao longo das transições de status da solicitação, evitando gargalos de conformidade e garantindo a co-criação de valor:

1. **Início da Contagem:** O SLA é iniciado automaticamente quando a solicitação ingressa na respectiva etapa operacional:
   - **Triagem:** Iniciado ao entrar no status **Aguardando triagem** (Status 2).
   - **Mapeamento:** Iniciado ao entrar no status **Aguardando mapeamento** (Status 5).
   - **Homologação:** Iniciado ao entrar no status **Em homologação** (Status 15).
   - _O prazo de atendimento aplicado considerará a prioridade da solicitação no exato momento de entrada na etapa._
2. **Pausa do SLA (Co-criação e Colaboração):** O SLA é pausado de imediato quando o progresso técnico depender exclusivamente de informações adicionais ou ações por parte do Solicitante.
   - **Status de Pausa:** **Pendente de informações** (Status 4).
   - **Regra de Pausa:** Durante o período de pausa, o contador visual deixa de avançar e o tempo acumulado até então é integralmente preservado. O período de espera do usuário não é contabilizado no SLA, protegendo a métrica de produtividade interna da equipe do NEO.
3. **Retomada do SLA:** Quando o Solicitante interage com a plataforma fornecendo as informações solicitadas, a contagem do SLA é retomada.
   - **Regra de Retomada:** A contagem continua exatamente do ponto onde parou. **O SLA nunca é reiniciado do zero após uma pausa**. (Exemplo: se uma solicitação com SLA de 24h consumiu 6h úteis antes de ser pausada, ela retomará com exatamente 18h restantes).
4. **Ausência de SLA no Backlog:** Solicitações no status **Backlog** (Status 12) não possuem SLA operacional ativo. A contagem de SLA só começa quando a solicitação for ativamente puxada para uma etapa que possua SLA definido.
5. **Encerramento do SLA:** O SLA é finalizado e encerrado definitivamente quando a solicitação atinge qualquer um dos seguintes status finais:
   - **Concluído** (Status 16)
   - **Cancelado** (Status 17)
   - **Não elegível** (Status 10)
   - **Direcionado para outra área** (Status 13)

##### 5.4. Gatilhos Visuais e Indicadores de Monitoramento na Interface

Alinhado com o princípio ITIL de manter os fluxos simples, práticos e visuais (_Keep it simple and practical_), o Portal NEO adota um monitoramento em tempo real por percentual de tempo consumido e status de pausa:

- **🟢 Verde (Dentro do Prazo):** De **0% a 69%** do prazo do SLA consumido. Indica que o atendimento está progredindo normalmente.
- **🟡 Amarelo (Próximo do Vencimento):** De **70% a 99%** do prazo do SLA consumido. Serve de alerta visual para o mapeador/administrador priorizar a ação técnica.
- **🔴 Vermelho (SLA Vencido):** **100% ou mais** do prazo do SLA consumido. Indica atraso operacional na entrega da etapa.
- **⏸️ Status de Pausa:** Quando o SLA está pausado, a contagem horária congela e a interface exibe de forma clara: `SLA pausado`.

##### 5.5. Registro Histórico de SLA para Auditoria

Para fins de auditoria de conformidade, melhoria contínua (_Continual Improvement_) e análise de capacidade de atendimento, todos os marcos temporais de SLA de cada solicitação devem ser persistidos no banco de dados. O histórico de auditoria registrará:

- Data e hora exatas do início da contagem por etapa;
- Log de pausas (timestamp de entrada em "Pendente de informações") e justificativas;
- Log de retomadas (timestamp de retorno);
- Alterações de prioridade no meio do ciclo e seu impacto no recálculo do prazo restante;
- Timestamp exato de encerramento do SLA.

---

#### 6. Nomenclatura e Status de Ciclo de Vida (17 Status) para Auditoria e Conformidade

A matriz de status do NEO possui **17 status funcionais** que garantem a micro-rastreabilidade de cada demanda do MVP. Para garantir a governança e permitir auditorias de TI externas sem poluir o acompanhamento visual do Solicitante, os status internos do NEO são correlacionados ao **Ciclo de Vida de Ciclo Único de ITIL v4**.

A tabela abaixo descreve essa equivalência de nomenclatura corporativa e integra as regras de controle de SLA de cada etapa.

| Status no NEO                       | Categoria / Estado ITIL v4 Equivalente            | Descrição Operacional e Gatilhos de Mudança                                                        | Visibilidade do Solicitante | Comportamento do SLA                                                     |
| ----------------------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------ |
| **1. Solicitação enviada**          | _Submitted_ (Submetida)                           | Demanda persistida no banco pelo solicitante. Aguarda geração física de protocolo.                 | Sim                         | **Sem contagem ativa** (Aguardando processamento inicial)                |
| **2. Aguardando triagem**           | _Queued_ (Em Fila de Entrada)                     | Inserida de forma automática na Fila Centralizada à espera de triagem.                             | Sim                         | **Início da contagem de SLA da Triagem** (SLA ativo conforme prioridade) |
| **3. Em triagem**                   | _Under Assessment_ (Sob Avaliação)                | Analista abre os detalhes para iniciar a avaliação. O sistema dispara esse status.                 | Sim                         | **Contagem ativa** de SLA da Triagem                                     |
| **4. Pendente de informações**      | _Pending User_ (Pendente com Usuário)             | Analista identifica falta de dados cruciais e envia notificação de pendência em tela.              | Sim                         | **Pausa do SLA** (O contador congela e preserva o tempo decorrido)       |
| **5. Aguardando mapeamento**        | _Approved for Diagnostics_ (Diagnóstico Pendente) | Demanda aprovada na triagem. O Administrador define o técnico responsável.                         | Sim                         | **Início da contagem de SLA do Mapeamento** (SLA ativo)                  |
| **6. Mapeamento agendado**          | _Diagnostics Scheduled_ (Diagnóstico Agendado)    | Reunião de mapeamento de processos agendada formalmente fora da plataforma.                        | Sim                         | **Contagem ativa** de SLA do Mapeamento                                  |
| **7. Em mapeamento**                | _In Diagnostics_ (Diagnóstico em Execução)        | Reunião ou sessões de análise de processo estão ocorrendo na data agendada.                        | Sim                         | **Contagem ativa** de SLA do Mapeamento                                  |
| **8. Em análise de viabilidade**    | _Under Feasibility Study_ (Estudo de Viabilidade) | Equipe técnica do NEO avalia se o processo mapeado é passível de automação.                        | Sim                         | **Contagem ativa** de SLA do Mapeamento                                  |
| **9. Elegível**                     | _Qualified_ (Qualificada)                         | Demanda atende a todos os critérios operacionais e de escopo do NEO.                               | Sim                         | **Encerra o SLA do Mapeamento** (Aguardando priorização)                 |
| **10. Não elegível**                | _Ineligible_ (Não Qualificada)                    | Demanda rejeitada por estar fora do escopo ou sem viabilidade técnico-operacional.                 | Sim                         | **Encerra o SLA definitivamente**                                        |
| **11. Priorizado**                  | _Prioritized in CIR_ (Oportunidade Priorizada)    | Score calculado coloca a solicitação em nível destacado para execução prioritária.                 | Sim                         | **Sem contagem ativa** (Demandas priorizadas em carteira)                |
| **12. Backlog**                     | _Backlog_ (Backlog Técnico)                       | Aprovada, porém retida no banco para aguardar alocação futura de capacidade técnica.               | Sim                         | **Sem SLA ativo** (Contagem suspensa no backlog)                         |
| **13. Direcionado para outra área** | _Transferred_ (Transferida)                       | Identificada como necessidade viável, mas que deve ser executada por outra célula ou time técnico. | Sim                         | **Encerra o SLA definitivamente**                                        |
| **14. Em desenvolvimento**          | _Implementation_ (Em Execução de Solução)         | O desenvolvimento da automação ou melhoria foi iniciado (Scripts, fluxos, robôs RPA).              | Sim                         | **Sem contagem ativa** (Etapa de desenvolvimento técnico no MVP)         |
| **15. Em homologação**              | _Testing & Validation_ (Em Homologação)           | A solução está em fase de testes conjuntos e validação do usuário final na ponta.                  | Sim                         | **Início da contagem de SLA da Homologação** (SLA ativo)                 |
| **16. Concluído**                   | _Resolved & Closed_ (Concluída / Encerrada)       | Entrega finalizada de forma bem-sucedida, com resultados validados e documentados.                 | Sim                         | **Encerra o SLA definitivamente**                                        |
| **17. Cancelado**                   | _Canceled_ (Cancelada)                            | Demanda cancelada internamente por duplicidade, descontinuidade do processo ou desistência.        | Sim                         | **Encerra o SLA definitivamente**                                        |

---

#### 7. Avaliação de Práticas ITIL Descartadas ou Simplificadas (Foco no MVP)

Para evitar que o Portal NEO herde as burocracias rígidas das ferramentas tradicionais de ITSM de mercado, várias práticas da biblioteca ITIL v4 foram intencionalmente **descartadas ou adaptadas com simplificação profunda** para o MVP. Essa modelagem garante conformidade sem onerar o time técnico e a interface do usuário.

#### Diretriz de Produto: "Herde a robustez do vocabulário do ITIL sem herdar a poluição de tela e complexidade do GLPI."

##### 7.1. Habilitação de Mudanças (_Change Enablement_) - **Descartada / Simplificada**

- **A Prática Original:** Exige que qualquer alteração de sistema passe por um comitê formal de aprovação de mudanças (CAB - _Change Advisory Board_), testes exaustivos registrados, rollback estruturado e aprovações multifásicas.
- **Justificativa de Descarte para o NEO:** As demandas cadastradas no NEO são melhorias e automações operacionais em rotinas departamentais (ex: RPA ou scripts de simplificação). Submetê-las a um CAB corporativo engessaria a agilidade do núcleo. O controle de liberação fica restrito à etapa simples de **Homologação** (Status 15) executada diretamente entre o Analista e o Solicitante, mantendo o processo dinâmico.

##### 7.2. Gerenciamento de Ativos e de Configuração (_Service Asset and Configuration Management - SACM_) - **Descartada**

- **A Prática Original:** Requer o registro e mapeamento de todos os itens de configuração (CI) físicos e lógicos (hardware, licenças de software, servidores) em um banco de dados denciamento de configuração (CMDB).
- **Justificativa de Descarte para o NEO:** O escopo do NEO é focado em eficiência de processos de negócios e fluxos de automação de tarefas, não em inventário ou controle de hardware. Acoplar um banco de dados CMDB geraria complexidade técnica desnecessária no modelo de dados do banco PostgreSQL, exigindo o mapeamento de ativos que já são gerenciados por outras instâncias tradicionais da empresa.

##### 7.3. Gerenciamento de Incidentes de Processo (_Incident Management_) - **Tratamento Simplificado**

- **A Prática Original:** Dedicada a restaurar a operação normal do serviço de TI o mais rápido possível após uma falha ou queda inesperada de sistema.
- **Justificativa de Descarte/Simplificação para o NEO:** O Tirador de Pedidos NEO **não é um sistema de suporte de infraestrutura ou suporte de TI geral** (como "problemas com internet" ou "troca de mouse"). Se uma automação existente apresentar problemas (um incidente), o solicitante pode reportar a necessidade como uma nova solicitação na categoria **Apoio Técnico**, **Revisão de Processo** ou **Outros**. Desta forma, o NEO treats o incidente conceitualmente sob o mesmo fluxo simplificado de requisição de serviço, centralizando e otimizando a fila operacional sem precisar de um módulo técnico separado para incidentes.

##### 7.4. Gerenciamento de Nível de Serviço (_Service Level Management - SLM_) - **Operacionalizado via Regras de SLA Flexíveis**

- **A Prática Original:** Estabelece contratos rígidos de nível de serviço (SLA), com acordos formais tripartites de tempos de resposta, penalidades financeiras e painéis complexos de monitoramento de metas em tempo real.
- **Aplicação Prática no NEO:** Em vez de adotar SLAs contratuais punitivos típicos de terceirizadas que engessam a TI tradicional, o Portal NEO adota o modelo de **SLA de Horas Úteis com Pausa Dinâmica** detalhado na Seção 5. Esse modelo une o controle operacional necessário com a flexibilidade da co-criação de valor (pausa no status de pendência com o solicitante). Isso elimina a rigidez prejudicial de ITSM corporativo enquanto mantém as metas operacionais transparentes e monitoradas por meio de gatilhos visuais.

---

#### 8. Rastreabilidade e Auditoria Imutável

O maior trunfo de governança do Tirador de Pedidos NEO é a imutabilidade do seu histórico de transações. Alinhado com as recomendações de segurança e auditorias corporativas, qualquer transição nos status operacionais, alterações de pesos ou atribuições gera um log de auditoria automático.
Este log protege a integridade das decisões tomadas na calculadora de score e na alocação de recursos:

- **Imutabilidade:** O histórico de auditoria não possui telas ou funcionalidades para exclusão através da interface comum.
- **Schema Estruturado:** Registra de forma indelével o protocolo, tipo de ação, usuário executor, timestamp exato, valores anteriores, novos valores e observações/justificativas associadas.
- **Controle de Eventos de SLA:** Registra de maneira auditável todos os marcos temporais e ações que impactaram os tempos de SLA (início de contagem por etapa, pausas pelo status "Pendente de informações", retomadas e a situação exata do SLA no encerramento da demanda).
- **Valor de Auditoria:** Garante conformidade com órgãos externos e governança de TI interna ao comprovar matematicamente o porquê de uma melhoria ter sido priorizada ou rejeitada, bem como o tempo útil de atendimento efetivo.

---

##### Considerações Finais

O alinhamento conceitual contido neste documento garante que o Tirador de Pedidos NEO possua robustez técnica de grandes soluções corporativas sob um chassi ágil e simplificado de MVP.
