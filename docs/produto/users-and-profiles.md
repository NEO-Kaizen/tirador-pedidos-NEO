# Usuários, Perfis e Regras de Acesso — Tirador de Pedidos do NEO

## Controle do documento

| Campo | Informação |
|---|---|
| Produto | Tirador de Pedidos do NEO |
| Documento | `docs/produto/usuarios-e-perfis.md` |
| Sprint | Sprint 1 |
| Time responsável | Produto |
| Status | Em revisão |
| Classificação | Restrito |
| Issue relacionada | #20 |
| Épico relacionado | #19 |

## 1. Objetivo do documento

<p>Este documento consolida os perfis de usuário identificados para o Tirador de Pedidos do NEO, registrando responsabilidades, necessidades, ações previstas, restrições conhecidas e pontos pendentes de definição.</p>

<p>O objetivo é apoiar os times de UI/UX, Frontend e Backend na construção dos fluxos, telas, regras de permissão e validações.</p>

## 2. Decisão importante sobre a quantidade de perfis

<p>A especificação técnica original prevê quatro perfis principais:</p>

<ol>
    <li>Solicitante.</li>
    <li>Analista/Mapeador.</li>
    <li>Administrador do NEO.</li>
    <li>Gestor/Visualizador.</li>
    <li>Admin Root.</li>
</ol>

<p>O Admin Root não está previsto em documentação tecnica, entretanto, devido a necessidades operacionais, se adicionou o Root. Ele deve ser tratado como uma role técnica/administrativa, criada por decisão técnica do time de produto. Os limites exatos desse perfil ainda precisam de validação.</p>

## 3. Resumo dos perfis

| Perfil | Tipo | Objetivo principal |
|---|---|---|
| Solicitante | Usuário final | Abrir solicitações e acompanhar o próprio pedido. |
| Analista/Mapeador | Usuário operacional | Conduzir triagem, análise, mapeamento e atualização do andamento. |
| Administrador do NEO | Usuário administrativo | Administrar fila, categorias, responsáveis, parâmetros, exportações e auditoria. |
| Gestor/Visualizador | Usuário de visualização | Consultar fila, indicadores e relatórios sem alterar registros operacionais. |
| Admin Root | Role técnica | Gerencia usuários, visualiza solicitações e delega solicitações e possui todas as atribuições anteriores. |

## 4. Solicitante

### Objetivo dentro do sistema

<p>O Solicitante é o usuário que abre uma nova solicitação a ser tratada pela NEO e acompanha o andamento da própria demanda.</p>

### Necessidades principais

<ul>
    <li>entender quais demandas podem ser cadastradas</li>
    <li>preencher o formulário de solicitação.</li>
    <li>receber um protocolo único.</li>
    <li>consultar sua solicitação posteriormente.</li>
    <li>visualizar status, pendências e próximo passo;</li>
    <li>salvar ou imprimir comprovante da solicitação.</li>
</ul>

### Ações previstas

| Ação | Situação |
|---|---|
| Acessar a tela inicial da aplicação. | Conhecido/Permitido |
| Abrir nova solicitação. | Conhecido/Permitido |
| Preencher dados do formulário. | Conhecido/Permitido |
| Receber protocolo após envio. | Conhecido/Permitido |
| Consultar solicitação por protocolo. | Conhecido/Permitido |
| Acompanhar status público. | Conhecido/Permitido |
| Visualizar pendências destinadas ao solicitante. | Conhecido/Permitido |
| Complementar informações quando permitido. | Conhecido/Permitido |
| Salvar ou imprimir comprovante. | Conhecido/Permitido |
| Visualizar fila administrativa. | Conhecido/Não permitido |
| Visualizar observações internas. | Conhecido/Não permitido |
| Alterar status. | Conhecido/Não permitido |
| Definir prioridade. | Conhecido/Não permitido |
| Atribuir responsável. | Conhecido/Não permitido |

### Restrições conhecidas

<ul>
    <li>não pode visualizar observações internas.</li>
    <li>não pode acessar a fila completa do NEO.</li>
    <li>não pode alterar registros operacionais.</li>
    <li>não haverá reconhecimento automático do usuário.</li>
    <li>os dados do solicitante serão informados manualmente no formulário.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| Em quais situações o solicitante poderá complementar informações? | Impacta tela de acompanhamento e status. | Produto. | 
| A consulta exigirá apenas protocolo e e-mail? | Impacta segurança e usabilidade. | Produto e Backend. |
| O solicitante poderá cancelar a própria solicitação? | Impacta fluxo e status. | Produto. |

## 5. Analista/Mapeador

### Objetivo dentro do sistema

<p>O Analista/Mapeador é o usuário responsável por conduzir a análise inicial das demandas, registrar informações de triagem, realizar mapeamentos e atualizar o andamento das solicitações atribuídas.</p>

### Necessidades principais

<ul>
    <li>visualizar demandas atribuídas.</li>
    <li>analisar informações recebidas.</li>
    <li>registrar observações internas.</li>
    <li>solicitar informações complementares.</li>
    <li>ajustar categoria.</li>
    <li>registrar complexidade preliminar.</li>
    <li>avaliar aderência ao escopo do NEO.</li>
    <li>registrar riscos.</li>
    <li>definir prioridade, quando aplicável.</li>
    <li>atribuir responsável, quando aplicável.</li>
    <li>registrar mapeamento.</li>
    <li>alterar status permitidos.</li>
</ul>

### Ações previstas

| Ação | Situação |
|---|---|
| Consultar demandas atribuídas. | Conhecido/Permitido |
| Revisar informações recebidas. | Conhecido/Permitido |
| Ajustar categoria. | Conhecido/Permitido |
| Registrar complexidade preliminar. | Conhecido/Permitido |
| Avaliar aderência ao escopo. | Conhecido/Permitido |
| Registrar riscos. | Conhecido/Permitido |
| Solicitar informações complementares. | Conhecido/Permitido |
| Atribuir responsável. | Conhecido/Não Permitido |
| Definir prioridade. | Conhecido/Permitido |
| Registrar observações internas. | Conhecido/Permitido |
| Indicar próximo passo. | Conhecido/Permitido |
| Alterar status permitidos. | Conhecido/Permitido |
| Registrar mapeamento. | Conhecido/Permitido |
| Registrar pendências. | Conhecido/Permitido |
| Administrar categorias. | Conhecido/Não Permitido |
| Administrar usuários. | Conhecido/Não Permitido |
| Exportar dados. | Conhecido/Permitido |
| Apagar histórico. | Conhecido/Não Permitido |

### Restrições conhecidas

<ul>
    <li>não deve administrar parâmetros globais, salvo permissão específica;</li>
    <li>não deve apagar histórico;</li>
    <li>deve respeitar as regras de auditoria;</li>
    <li>Não poderão administrar usuários;</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O analista pode ver toda a fila ou somente demandas atribuídas? | Impacta painel, permissões e UX. | Produto. |

## 6. Administrador do NEO

### Objetivo dentro do sistema

O Administrador do NEO é o perfil responsável pela administração operacional e parametrização da solução.

### Necessidades principais

<ul>
    <li>visualizar todas as solicitações.</li>
    <li>administrar a fila.</li>
    <li>administrar prioridades.</li>
    <li>administrar responsáveis.</li>
    <li>administrar categorias.</li>
    <li>administrar status.</li>
    <li>administrar parâmetros;</li>
    <li>exportar dados.</li>
    <li>consultar auditoria.</li>
    <li>gerenciar usuários e perfis básicos, quando aplicável.</li>
</ul>

### Ações previstas

| Ação | Situação |
|---|---|
| Consultar todas as demandas. | Conhecido/Permitido |
| Visualizar e filtrar a fila. | Conhecido/Permitido |
| Abrir detalhes do pedido. | Conhecido/Permitido |
| Alterar categoria. | Conhecido/Permitido |
| Definir prioridade. | Conhecido/Permitido |
| Atribuir responsável. | Conhecido/Permitido |
| Alterar status. | Conhecido/Permitido |
| Registrar pendências. | Conhecido/Permitido |
| Registrar mapeamento. | Conhecido/Permitido |
| Incluir comentários internos. | Conhecido/Permitido |
| Registrar conclusão. | Conhecido/Permitido |
| Cancelar solicitação. | Conhecido/Permitido |
| Exportar dados. | Conhecido/Permitido |
| Consultar histórico. | Conhecido/Permitido |
| Administrar categorias. | Conhecido/Permitido |
| Administrar responsáveis. | Conhecido/Permitido |
| Administrar parâmetros. | Conhecido/Permitido |
| Administrar usuários e perfis básicos. | Não Mapeado/Permitido |
| Apagar histórico pela interface comum. | Conhecido/Não permitido |

### Restrições conhecidas
<ul>
    <li>não pode apagar histórico pela interface comum.</li>
    <li>alterações relevantes devem gerar auditoria.</li>
    <li>informações restritas devem ser acessadas apenas por usuários autorizados</li>
    <li>categorias não devem ficar fixas no código.</li>
    <li>Não poderão excluir a si mesmos ou a outros administradores</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| Haverá separação clara entre Administrador do NEO e Admin Root? | Impacta permissões e segurança. | Produto e Tech Lead. |
| O Administrador poderá editar dados após conclusão? | Impacta auditoria e regras de negócio. | Produto. |

## 7. Gestor/Visualizador

### Objetivo dentro do sistema

O Gestor/Visualizador é o perfil que acompanha indicadores, relatórios e a fila, sem alterar registros operacionais.

### Necessidades principais

<ul>
    <li>consultar fila.</li>
    <li>visualizar indicadores.</li>
    <li>exportar relatórios.</li>
    <li>acompanhar status geral das demandas.</li>
    <li>ter visão gerencial sem operar o fluxo.</li>
</ul>

### Ações previstas

| Ação | Situação |
|---|---|
| Consultar fila. | Conhecido/Permitido |
| Consultar indicadores. | Conhecido/Permitido |
| Exportar relatórios. | Conhecido/Permitido |
| Abrir solicitações para visualização. | Conhecido/Permitido |
| Alterar status. | Não permitido |
| Definir prioridade. | Conhecido/Não permitido |
| Atribuir responsável. | Conhecido/Não permitido |
| Registrar pendências. | Conhecido/Não permitido |
| Registrar mapeamento. | Conhecido/Não permitido |
| Administrar parâmetros. | Conhecido/Não permitido |
| Apagar histórico. | Conhecido/Não permitido |

### Restrições conhecidas

<ul>
    <li>não pode alterar registros operacionais.</li>
    <li>não pode administrar parâmetros.</li>
    <li>não pode registrar pendências ou mapeamento.</li>
    <li>não deve executar ações administrativas.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O Gestor/Visualizador pode ver detalhes completos da solicitação? | Impacta tela de visualização. | Produto. |
| O Gestor/Visualizador pode ver observações internas? | Impacta privacidade e permissões. | Produto. |
| O Gestor pode exportar informações restritas? | Impacta segurança. | Produto e Backend. |

## 8. Admin Root

### Objetivo dentro do sistema

O Admin Root é uma role técnica adicional proposta pelo time. Ele não é um perfil funcional previsto originalmente na especificação, mas foi identificado para apoiar necessidades técnicas, administrativas ou de implantação. Já que não deve haver dados de autenticação no sistema, o primeiro usuário cadastrado que devera realizar o registro dos demais usuários.

### Situação atual

Este perfil ainda precisa de validação formal. O documento registra a existência da necessidade, mas não inventa permissões não definidas.

### Possíveis responsabilidades

<p>As responsabilidades abaixo são hipóteses iniciais e precisam de validação:</p>

<ul>
    <li>O sistema terá um usuário Root configurado previamente no banco de dados.</li>
    <li>O usuário Root será responsável por cadastrar os demais usuários do sistema.</li>
    <li>apoiar configuração inicial do sistema.</li>
    <li>apoiar criação ou recuperação de usuários.</li>
    <li>apoiar correções excepcionais.</li>
    <li>apoiar troubleshooting técnico.</li>
    <li>acessar configurações técnicas.</li>
    <li>auditar ações administrativas críticas.</li>
</ul>

### Ações previstas

| Ação | Situação |
|---|---|
| Consultar todas as demandas. | Não Mapeado/Permitido |
| Visualizar e filtrar a fila. | Não Mapeado/Permitido |
| Abrir detalhes do pedido. | Não Mapeado/Permitido |
| Alterar categoria. | Não Mapeado/Permitido |
| Definir prioridade. | Não Mapeado/Permitido |
| Atribuir responsável. | Não Mapeado/Permitido |
| Alterar status. | Não Mapeado/Permitido |
| Registrar pendências. | Não Mapeado/Permitido |
| Registrar mapeamento. | Não Mapeado/Permitido |
| Incluir comentários internos. | Não Mapeado/Permitido |
| Registrar conclusão. | Não Mapeado/Permitido |
| Cancelar solicitação. | Não Mapeado/Permitido |
| Exportar dados. | Não Mapeado/Permitido |
| Consultar histórico. | Não Mapeado/Permitido |
| Administrar categorias. | Não Mapeado/Permitido |
| Administrar responsáveis. | Não Mapeado/Permitido |
| Administrar parâmetros. | Não Mapeado/Permitido |
| Administrar usuários e perfis básicos. | Não Mapeado/Permitido |
| Apagar histórico pela interface comum. | Não Mapeado/Não permitido |

### Restrições recomendadas

<ul>
    <li>não deve ser usado para operação diária comum;</li>
    <li>ações devem ser auditadas;</li>
    <li>deve ser usado apenas por pessoas autorizadas;</li>
    <li>não deve permitir exclusão de histórico pela interface comum;</li>
    <li>deve haver registro claro de quando o Admin Root for utilizado.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O Admin Root será uma role da aplicação ou apenas acesso técnico de infraestrutura? | Impacta backend, segurança e banco. | Backend e Tech Lead. |
| Haverá log especial para ações de Admin Root? | Impacta auditoria. | Backend. |
| Quantas pessoas poderão ter Admin Root? | Impacta governança. | Produto e Tech Lead. |

## 9. Matriz resumida de permissões

Legenda:

| Símbolo | Significado |
|---|---|
| S | Permitido, conforme especificação conhecida. |
| N | Não permitido. |
| C | Conforme atribuição ou permissão específica. |
| P | Pendente de definição. |

| Ação | Solicitante | Analista/Mapeador | Administrador do NEO | Gestor/Visualizador | Admin Root |
|---|---:|---:|---:|---:|---:|
| Abrir nova solicitação | S | S | S | S | S |
| Consultar próprio protocolo | S | S | S | S | S |
| Visualizar fila completa | N | C | S | S | S |
| Visualizar demandas atribuídas | N | S | S | S | S |
| Registrar triagem | N | S | S | N | S |
| Ajustar categoria | N | S | S | N | S |
| Definir prioridade | N | S | S | N | S |
| Atribuir responsável | N | S | S | N | S |
| Alterar status | N | C | S | N | S |
| Registrar pendências | N | S | S | N | s |
| Registrar mapeamento | N | S | S | N | S |
| Ver observações internas | N | S | S | S | S |
| Consultar histórico | N | C | S | S | S |
| Exportar dados | N | S | S | S | S |
| Administrar categorias | N | N | S | N | S |
| Administrar responsáveis | N | N | S | N | S |
| Administrar parâmetros | N | N | S | N | S |
| Administrar usuários | N | N | S | N | S |
| Apagar histórico pela interface comum | N | N | N | N | N |

## 10. Regras gerais de acesso conhecidas

<ul>
    <li>A aplicação deverá usar mecanismo simples de autenticação aprovado para o ambiente interno.</li>
    <li>Não haverá reconhecimento automático do usuário conectado.</li>
    <li>Não haverá integração com diretório corporativo nesta versão.</li>
    <li>Os dados do solicitante deverão ser informados manualmente no formulário.</li>
    <li>O e-mail do solicitante funcionará como dado de referência e contato.</li>
    <li>Não haverá envio automático de mensagens.</li>
    <li>Informações restritas devem ser acessadas apenas por usuários autorizados.</li>
    <li>Ações relevantes devem gerar auditoria.</li>
    <li>O histórico não deve ser apagado pela interface comum.</li>
</ul>

## 11. Pontos abertos

<p>Os pontos abaixo precisam de decisão antes da implementação completa das permissões:</p>

<ol>
    <li>O Admin Root será realmente implementado como role da aplicação?</li>
    <li>Quais serão as permissões exatas do Admin Root?</li>
    <li>O Admin Root poderá executar ações administrativas comuns?</li>
    <li>O Gestor/Visualizador poderá visualizar observações internas?</li>
    <li>O Analista/Mapeador poderá exportar dados?</li>
    <li>O Administrador do NEO poderá gerenciar usuários?</li>
    <li>A consulta do solicitante usará apenas protocolo e e-mail?</li>
    <li>Haverá diferença entre usuário administrativo ativo e inativo?</li>
    <li>Como será feita a recuperação de acesso nesta primeira versão?</li>
    <li>Quais ações do Admin Root exigirão auditoria especial?</li>
</ol>

## 12. Referências

<ul>
    <li>NEO — Especificação Técnica — Tirador de Pedidos do NEO, versão 0.1.</li>
    <li>Seção 20 — Perfis de acesso.</li>
    <li>Seção 7 — Acesso à aplicação.</li>
    <li>Seção 19 — Painel administrativo.</li>
    <li>Seção 21 — Histórico e auditoria.</li>
    <li>Materiais produzidos na Sprint 1.</li>
    <li>Registros de reunião e decisões do time.</li>
</ul>

## 13. Observações

<p>Este documento não deve criar regras de permissão apenas para completar lacunas.

Quando uma informação não estiver definida, ela deve permanecer como pendência até validação formal.

O Admin Root deve ser tratado com cuidado, pois envolve acesso administrativo amplo e risco de segurança. Suas permissões precisam ser validadas por Produto, Backend e Tech Lead.</p>