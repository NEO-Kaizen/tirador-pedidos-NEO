# Requisitos Funcionais — RESTRITO

Este documento lista e detalha os Requisitos Funcionais (RFs) mapeados e consolidados para o sistema. Eles descrevem o que a aplicação deve fazer e permitir que seus atores executem.

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | RESTRITO |
| Documento | `docs/produto/requisitos-funcionais.md` |
| Sprint | Sprint 1 (Consolidação) |
| Status | Pronto para Integração |

---

## 1. Módulo do Solicitante (Área Pública)

### RF-001 — Abertura de Solicitação Pública
- **Descrição:** O sistema deve disponibilizar um formulário de livre acesso para registro de novas solicitações operacionais, estruturado em blocos de dados.
- **Ator:** Solicitante.
- **Resultado esperado:** Solicitação gravada no banco de dados, geração de protocolo de identificação e apresentação da tela de confirmação.
- **Regras relacionadas:** `RN-001`, `RN-002`, `RN-003`, `RN-004`.
- **Status:** Confirmado.

### RF-002 — Consulta Pública de Andamento
- **Descrição:** O sistema deve permitir que o solicitante acompanhe a evolução do status, pendências e próximos passos da sua solicitação através de uma busca cruzada.
- **Ator:** Solicitante.
- **Resultado esperado:** Carregamento das informações públicas da demanda quando as credenciais fornecidas coincidirem.
- **Regras relacionadas:** `RN-005`, `RN-007`.
- **Status:** Confirmado.

---

## 2. Módulo de Segurança e Acesso

### RF-003 — Autenticação de Usuários Administrativos
- **Descrição:** O sistema deve exigir login e senha local para conceder acesso às telas de triagem, mapeamento e configurações aos perfis administrativos.
- **Ator:** Analista, Administrador, Gestor.
- **Resultado esperado:** Geração de sessão segura e redirecionamento de acordo com o perfil.
- **Regras relacionadas:** `RN-006`.
- **Status:** Confirmado.

---

## 3. Módulo de Operação e Triagem (Fila Centralizada)

### RF-004 — Exibição e Filtragem da Fila Administrativa
- **Descrição:** O sistema deve apresentar a Fila Centralizada de Pedidos, permitindo ordenação, visualização e filtragem rápida por e-mail ou protocolo.
- **Ator:** Analista, Administrador, Gestor.
- **Resultado esperado:** Exibição dinâmica dos registros da fila.
- **Regras relacionadas:** `RN-008`, `RN-013`.
- **Status:** Confirmado.

### RF-005 — Avaliação de Score e Priorização
- **Descrição:** O sistema deve fornecer uma calculadora em tela contendo 10 critérios para que o analista avalie a demanda de 1 a 5 e calcule o nível de risco/prioridade.
- **Ator:** Analista, Administrador.
- **Resultado esperado:** Geração automática do score ponderado e classificação na faixa de prioridade correspondente.
- **Regras relacionadas:** `RN-009`, `RN-010`, `RN-011`.
- **Status:** Confirmado.

### RF-006 — Atribuição de Responsável Técnico
- **Descrição:** O sistema deve permitir que o Administrador atribua ou altere manualmente o analista responsável pela condução do mapeamento da solicitação.
- **Ator:** Administrador.
- **Resultado esperado:** Atualização do analista responsável no registro e gatilho de mudança de status da demanda.
- **Regras relacionadas:** `RN-012`, `RN-013`.
- **Status:** Confirmado.

---

## 4. Módulo de Mapeamento de Processos

### RF-007 — Registro de Atividades de Mapeamento
- **Descrição:** O sistema deve disponibilizar formulário interno para o registro declarativo de dados de reuniões, links, datas e participantes de reuniões de diagnóstico.
- **Ator:** Analista, Administrador.
- **Resultado esperado:** Dados de agendamento gravados nos detalhes da demanda e disponibilização de templates de texto para cópia.
- **Regras relacionadas:** `RN-014`.
- **Status:** Confirmado.

---

## 5. Módulo de Administração de Parâmetros

### RF-008 — Gerenciamento de Configurações do Sistema
- **Descrição:** O sistema deve disponibilizar um painel administrativo exclusivo para gerenciamento dinâmico de usuários (criar, editar e inativar), categorias de solicitações e alteração dos pesos da calculadora de priorização.
- **Ator:** Administrador.
- **Resultado esperado:** Gravação e persistência das novas regras de negócio sem necessidade de alteração de código-fonte.
- **Regras relacionadas:** `RN-011`, `RN-013`, `RN-015`.
- **Status:** Confirmado.

### RF-009 — Consulta do Histórico de Auditoria
- **Descrição:** O sistema deve manter uma área para consulta de logs imutáveis que registraram as modificações operacionais mais importantes ocorridas nas solicitações e configurações.
- **Ator:** Administrador, Gestor (Apenas leitura).
- **Resultado esperado:** Exibição sequencial e rastreável de todas as ações de log.
- **Regras relacionadas:** `RN-016`.
- **Status:** Confirmado.