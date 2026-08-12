# Pendências e Decisões de Produto — Tirador de Produtos NEO

Este documento lista as dúvidas funcionais, hipóteses não confirmadas e discussões em aberto que foram identificadas e isoladas durante o mapeamento de requisitos. 

Estes itens **não constituem regras de negócio confirmadas** para o MVP e devem ser tratados como pendências de produto a serem refinadas em Sprints futuras.

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | Tirador de Produtos NEO |
| Documento | `docs/produto/pending.md` |
| Sprint | Sprint 1 (Consolidação) |
| Status | Em Aberto / A Validar |

---

## 1. Pendências Operacionais de Fluxo

### PEND-001 — Permissões de Visualização e Exportação de Dados do Perfil Gestor
- **Dúvida:** O perfil de Gestor/Visualizador poderá exportar dados de auditoria detalhados e relatórios contendo informações classificadas como confidenciais ou sensíveis da empresa?
- **Impacto:** Segurança da informação e visibilidade de dados.
- **Responsável por decidir:** Produto e Tech Lead.
- **Ações sugeridas:** Definir uma matriz complementar de classificação de dados para mascaramento ou restrição de e-mails/logs para perfis não-operacionais.
- **Status:** Pendente.

### PEND-002 — Edição de Solicitações Concluídas
- **Dúvida:** O administrador ou analista poderá reabrir ou alterar dados sensíveis de uma solicitação após o status ser alterado para **Concluído** ou **Cancelado**?
- **Impacto:** Integridade da fila e confiabilidade do histórico de auditoria.
- **Responsável por decidir:** Produto e Scrum Master.
- **Ações sugeridas:** Bloquear a edição de dados descritivos após a conclusão, permitindo apenas a inserção de logs justificando a reabertura excepcional.
- **Status:** Pendente.

### PEND-003 — Cancelamento Ativo pelo Solicitante
- **Dúvida:** O Solicitante terá permissão para cancelar ativamente a própria solicitação através da tela de acompanhamento público, utilizando sua validação por e-mail e protocolo?
- **Impacto:** Fluxo de vida do pedido e retrabalho da equipe de triagem.
- **Responsável por decidir:** Produto.
- **Ações sugeridas:** Permitir apenas que o solicitante "solicite o cancelamento" por mensagem, deixando a ação efetiva de alteração de status restrita à equipe interna.
- **Status:** Pendente.

### PEND-004 — Acesso de Observações Internas pelo Perfil Gestor
- **Dúvida:** O Gestor de relatórios (Visualizador) deve ter acesso à leitura dos comentários internos e notas particulares feitos pelos analistas no processo de triagem ou somente aos dados públicos da demanda?
- **Impacto:** Privacidade técnica e governança operacional.
- **Responsável por decidir:** Produto.
- **Status:** Pendente.