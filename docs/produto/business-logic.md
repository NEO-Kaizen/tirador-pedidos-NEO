# Regras de Negócio — Tirador de Pedidos NEO

Este documento reúne e detalha as Regras de Negócio (RNs) que regem os comportamentos funcionais, restrições, fórmulas matemáticas e fluxos de decisão do sistema.

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | Tirador de Pedidos NEO |
| Documento | `docs/produto/business-logic.md` |
| Sprint | Sprint 1 (Consolidação) |
| Status | Pronto para Integração |

---

## 1. Regras de Acesso e Interface do Solicitante

### RN-001 — Acesso Público Irrestrito
- **Regra:** A tela inicial do portal público de abertura de solicitações deve ser acessível a qualquer pessoa através da rede corporativa, sem exigência de autenticação por usuário e senha.
- **Condição:** Sempre aplicável.
- **Comportamento esperado:** Abertura direta do formulário.
- **Origem:** Especificação de requisitos e alinhamento com P.O.
- **Status:** Confirmada.

### RN-002 — Validação de Domínio de E-mail
- **Regra:** O formulário de abertura de solicitações deve validar o campo de e-mail corporativo do solicitante, rejeitando domínios de e-mails públicos ou não autorizados.
- **Condição:** No momento do preenchimento e clique em "Enviar".
- **Comportamento esperado:** Aceitar apenas domínios corporativos parametrizados (ex: `@RESTRITO.com` ou `@RESTRITO.com`). Exibir alerta na tela em caso de falha.
- **Origem:** Especificação de requisitos.
- **Status:** Não Confirmado.

### RN-003 — Inexistência de Caching em Tela (Local Storage)
- **Regra:** O sistema não deve fazer uso de `Local Storage` ou qualquer mecanismo de cache local no navegador para salvar provisoriamente o rascunho de preenchimento do formulário.
- **Condição:** Preenchimento do formulário de abertura.
- **Comportamento esperado:** Caso o navegador seja fechado ou a conexão caia antes do envio completo, os dados digitados serão perdidos.
- **Origem:** Decisão de produto baseada em riscos de TI e diversidade de navegadores.
- **Status:** Confirmada.

### RN-004 — Armazenamento de Texto Longo
- **Regra:** Os campos longos preenchidos pelo solicitante (Descrição da Necessidade, Justificativa e Descrição do Processo Atual) não devem possuir limites de caracteres estritos de interface.
- **Condição:** Envio e armazenamento no banco de dados.
- **Comportamento esperado:** O banco de dados PostgreSQL salvará os campos como tipo `TEXT`, sem truncar ou quebrar o conteúdo detalhado pelo usuário.
- **Origem:** Alinhamento com P.O. para garantir liberdade de escrita de processos na ponta.
- **Status:** Confirmada.

---

## 2. Regras de Consulta Pública e Privacidade

### RN-005 — Validação de Chave Dupla para Acompanhamento
- **Regra:** O solicitante só pode acessar o andamento de sua solicitação na área pública se fornecer a combinação idêntica e correta do número do protocolo e e-mail cadastrados na abertura.
- **Condição:** Busca de protocolo na área pública.
- **Comportamento esperado:** Se o par de dados não for correspondente, retornar mensagem genérica de erro ("Protocolo ou e-mail não encontrados"). Bloquear acessos por tentativa e erro de números sequenciais de protocolo.
- **Origem:** Considerações de cibersegurança e alinhamento de privacidade de dados.
- **Status:** Não Confirmado.

### RN-006 — Autenticação Administrativa Segura (JWT)
- **Regra:** Toda e qualquer sessão administrativa ou técnica interna do sistema deve ser protegida por credenciais armazenadas de forma segura (uso de algoritmo de hashing de senha no banco de dados) e gerenciamento de estado via JSON Web Tokens (JWT).
- **Condição:** Acesso ao painel administrativo.
- **Comportamento esperado:** Bloquear acessos não autenticados a endpoints e páginas internas. Senhas em texto limpo não devem ser armazenadas sob nenhuma hipótese.
- **Origem:** Decisão de produto alinhada com as recomendações de cibersegurança do coordenador.
- **Status:** Confirmada.

### RN-007 — Filtro de Exibição de Dados Públicos
- **Regra:** Informações de comentários internos de analistas, scores de prioridade, notas atribuídas aos critérios e campos privados da triagem nunca devem ser carregados ou exibidos ao Solicitante no painel de acompanhamento.
- **Condição:** Renderização do Painel Público de Acompanhamento.
- **Comportamento esperado:** Exibir apenas: protocolo, nome resumo, status, responsável, data de mapeamento (se houver), pendências destinadas ao solicitante e resultado final do encerramento.
- **Origem:** Garantia de isolamento e privacidade operacional do time técnico do NEO.
- **Status:** Confirmada.

---

## 3. Regras da Fila Centralizada e Triagem

### RN-008 — Pesquisa Unificada de Fila de Trabalho
- **Regra:** A barra de busca da Fila Centralizada Administrativa deve filtrar os resultados localizando ocorrências correspondentes aos campos de E-mail do Solicitante ou Número de Protocolo de forma independente.
- **Condição:** Digitação na pesquisa interna.
- **Comportamento esperado:** Filtrar a tabela de forma dinâmica se o texto inserido fizer correspondência parcial ou total com um dos dois campos estabelecidos.
- **Origem:** Alinhamento com P.O.
- **Status:** Confirmada.

### RN-009 — Calculadora de Score por Média Ponderada Normalizada
- **Regra:** O Score de Prioridade de uma demanda deve ser calculado aplicando-se a média ponderada das notas atribuídas aos 10 critérios de negócio, multiplicando-se o resultado final por 10 para normalização na escala decimal de 10 a 50 pontos.
- **Condição:** Execução da calculadora de priorização na triagem.
- **Fórmula:**
  $$\text{Score Final} = \left( \frac{\sum_{i=1}^{10} (\text{Nota}_i \times \text{Peso}_i)}{\sum_{i=1}^{10} \text{Peso}_i} \right) \times 10$$
- **Comportamento esperado:** O score resultante estará matematicamente fixado no intervalo entre 10.0 (mínimo) e 50.0 (máximo), independente de flutuações e alterações de pesos configuradas.
- **Origem:** Decisão matemática acordada para garantir a estabilidade das faixas de risco.
- **Status:** Confirmada.

### RN-010 — Faixas Fixas de Classificação de Prioridade
- **Regra:** O Score Final obtido através da média ponderada normalizada classifica a solicitação automaticamente em uma das seguintes categorias de prioridade de atendimento:
  - **Prioridade Baixa:** de 10.0 a 20.0 pontos.
  - **Prioridade Média:** de 20.1 a 30.0 pontos.
  - **Prioridade Alta:** de 30.1 a 40.0 pontos.
  - **Prioridade Crítica:** de 40.1 a 50.0 pontos.
- **Condição:** Cálculo do Score Final.
- **Status:** Confirmada.

### RN-011 — Parametrização Inicial de Pesos
- **Regra:** Todos os 10 critérios de priorização devem ser inicializados no banco de dados com **peso padrão igual a 1** (equivalendo à soma simples). O Administrador do sistema pode alterar o peso de cada critério na tela de configurações a qualquer momento.
- **Condição:** Configurações do sistema.
- **Comportamento esperado:** A alteração de um peso aplica-se automaticamente aos novos cálculos executados pela calculadora, afetando a média ponderada sem quebrar as faixas de score.
- **Origem:** Proposta de flexibilidade de arquitetura de produto aprovada pelo P.O.
- **Status:** Confirmada.

---

## 4. Regras de Atribuição e Status

### RN-012 — Gatilho de Status na Triagem de Elegíveis
- **Regra:** No momento em que uma demanda em triagem for aprovada como elegível pelo analista e o Administrador definir e salvar o responsável técnico pelo mapeamento, o sistema deve alterar automaticamente o status da solicitação de **"Em triagem"** para **"Aguardando mapeamento"**.
- **Condição:** Salvamento do responsável na triagem com elegibilidade aprovada.
- **Status:** Confirmada.

### RN-013 — Manutenção de Custódia e Inativação Sem Bloqueios (Softlocks)
- **Regra:** Caso um analista cadastrado seja desativado (Inativo) no painel de configurações de usuários, as demandas associadas a ele na fila administrativa permanecem intocadas, mantendo o histórico de atribuição.
- **Condição:** Desativação de usuário administrativo.
- **Comportamento esperado:** O sistema impede novos logins do usuário inativado. Na fila administrativa, o Administrador poderá, a qualquer momento e sem travas automatizadas, substituir o responsável técnico das demandas inativas por analistas ativos.
- **Origem:** Alinhamento de Produto focado em simplificação técnica para o MVP.
- **Status:** Confirmada.

---

## 5. Regras de Mapeamento de Reuniões

### RN-014 — Registro Manual e Independente de Mapeamento
- **Regra:** As reuniões de mapeamento, diagnósticos e alinhamentos de processo ocorrem por fora da plataforma (Teams/Outlook corporativos). O sistema atua apenas como repositório declarativo desses agendamentos.
- **Condição:** Registro de reuniões.
- **Comportamento esperado:** O sistema armazena os dados descritivos (data, link, local) sem realizar consultas de agenda do Office 365, e fornece templates de e-mail preenchidos para cópia rápida via área de transferência (*clipboard*).
- **Status:** Confirmada.

---

## 6. Regras de Inicialização de Sistema

### RN-015 — Bootstrapping e Seed de Fábrica do Super-Admin
- **Regra:** A aplicação não deve possuir telas públicas para criação ou autocadastro do primeiro administrador. O banco de dados inicial deve conter um registro de super-administrador padrão ativo através de carga inicial de banco de dados (*database seed*).
- **Condição:** Inicialização limpa da aplicação.
- **Comportamento esperado:** O técnico de implantação realiza o primeiro login utilizando o e-mail e senha padrão criados pelo seed e, a partir de seu painel restrito, cria as contas oficiais dos demais usuários operacionais.
- **Origem:** Preocupação de cibersegurança e facilitação de implantação por migrations.
- **Status:** Confirmada.

---

## 7. Regras de Histórico e Auditoria

### RN-016 — Geração Obrigatória de Logs de Auditoria
- **Regra:** Qualquer alteração efetuada nos registros de demandas ou configurações de parâmetros administrativos do sistema disparará a geração automática de um log imutável de auditoria no banco de dados.
- **Condição:** Execução de um dos 9 gatilhos de auditoria mapeados.
- **Schema Mínimo do Registro:**
  - *ID do Registro* (PK)
  - *Protocolo da demanda afetada* (null em caso de alteração global de parâmetros)
  - *Tipo da Ação* (Criação, Alteração de Status, Alteração de Prioridade, Atribuição, Substituição, Registro de Mapeamento, Inclusão de Pendência, Conclusão ou Cancelamento)
  - *Usuário executor* (ID/E-mail do analista ativo na sessão)
  - *Data e Hora* (Timestamp do sistema)
  - *Valor Anterior* (Cadeia de texto ou JSON representando estado prévio)
  - *Novo Valor* (Cadeia de texto ou JSON representando estado pós-ação)
  - *Observação* (Comentário associado à ação)
  - *Origem da Alteração* (Interface onde ocorreu a alteração)
- **Status:** Confirmada.