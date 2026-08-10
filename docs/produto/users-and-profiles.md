<style>
    p, ul, ol {
        text-align: justify;
    }
</style>

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
    
    Além desses, o time registrou a necessidade de um quinto perfil técnico:

<li>Admin Root.</li>
</ol>

<p>O Admin Root deve ser tratado como uma role técnica/administrativa, criada por decisão técnica do time. Os limites exatos desse perfil ainda precisam de validação.</p>

## 3. Resumo dos perfis

| Perfil | Tipo | Objetivo principal |
|---|---|---|
| Solicitante | Usuário final | Abrir solicitações e acompanhar o próprio pedido. |
| Analista/Mapeador | Usuário operacional | Conduzir triagem, análise, mapeamento e atualização do andamento. |
| Administrador do NEO | Usuário administrativo | Administrar fila, categorias, responsáveis, parâmetros, exportações e auditoria. |
| Gestor/Visualizador | Usuário de visualização | Consultar fila, indicadores e relatórios sem alterar registros operacionais. |
| Admin Root | Role técnica | Gerencia usuários, visualiza solicitações e delega solicitações. |

## 4. Solicitante

### Objetivo dentro do sistema

<p>O Solicitante é o usuário que abre uma nova solicitação para o NEO e acompanha o andamento da própria demanda.</p>

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
| Acessar a tela inicial da aplicação. | Conhecido |
| Abrir nova solicitação. | Conhecido |
| Preencher dados do formulário. | Conhecido |
| Receber protocolo após envio. | Conhecido |
| Consultar solicitação por protocolo. | Conhecido |
| Acompanhar status público. | Conhecido |
| Visualizar pendências destinadas ao solicitante. | Conhecido |
| Complementar informações quando permitido. | Conhecido, mas depende de definição |
| Salvar ou imprimir comprovante. | Conhecido |
| Visualizar fila administrativa. | Não permitido |
| Visualizar observações internas. | Não permitido |
| Alterar status. | Não permitido |
| Definir prioridade. | Não permitido |
| Atribuir responsável. | Não permitido |

### Restrições conhecidas

<ul>
    <li>não pode visualizar observações internas.</li>
    <li>não pode acessar a fila completa do NEO.</li>
    <li>não pode alterar registros operacionais.</li>
    <li>não deve acessar solicitações de outros usuários sem permissão.</li>
    <li>não haverá reconhecimento automático do usuário.</li>
    <li>os dados do solicitante serão informados manualmente no formulário.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O solicitante poderá editar a solicitação após o envio? | Impacta formulário, fluxo e banco. | Produto. |
| Em quais situações o solicitante poderá complementar informações? | Impacta tela de acompanhamento e status. | Produto. | (remover?)
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
| Consultar demandas atribuídas. | Conhecido |
| Revisar informações recebidas. | Conhecido |
| Ajustar categoria. | Conhecido |
| Registrar complexidade preliminar. | Conhecido |
| Avaliar aderência ao escopo. | Conhecido |
| Registrar riscos. | Conhecido |
| Solicitar informações complementares. | Conhecido |
| Atribuir responsável. | Conhecido |
| Definir prioridade. | Conhecido |
| Registrar observações internas. | Conhecido |
| Indicar próximo passo. | Conhecido |
| Alterar status permitidos. | Conhecido |
| Registrar mapeamento. | Conhecido |
| Registrar pendências. | Conhecido |
| Administrar categorias. | Não previsto |
| Administrar usuários. | Não previsto |
| Exportar dados. | Pendente |
| Apagar histórico. | Não permitido |

### Restrições conhecidas

<ul>
    <li>não deve administrar parâmetros globais, salvo permissão específica;</li>
    <li>não deve apagar histórico;</li>
    <li>deve respeitar as regras de auditoria;</li>
    <li>observações internas não devem ser exibidas ao solicitante.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O analista pode ver toda a fila ou somente demandas atribuídas? | Impacta painel, permissões e UX. | Produto. |
| O analista pode atribuir responsável a si mesmo? | Impacta fluxo de triagem. | Produto. |
| Quais status podem ser alterados pelo analista? | Impacta máquina de status. | Produto e Backend. |
| O analista poderá exportar dados? | Impacta permissões e segurança. | Produto. |

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
| Consultar todas as demandas. | Conhecido |
| Visualizar e filtrar a fila. | Conhecido |
| Abrir detalhes do pedido. | Conhecido |
| Alterar categoria. | Conhecido |
| Definir prioridade. | Conhecido |
| Atribuir responsável. | Conhecido |
| Alterar status. | Conhecido |
| Registrar pendências. | Conhecido |
| Registrar mapeamento. | Conhecido |
| Incluir comentários internos. | Conhecido |
| Registrar conclusão. | Conhecido |
| Cancelar solicitação. | Conhecido |
| Exportar dados. | Conhecido |
| Consultar histórico. | Conhecido |
| Administrar categorias. | Conhecido |
| Administrar responsáveis. | Conhecido |
| Administrar parâmetros. | Conhecido |
| Administrar usuários e perfis básicos. | Pendente |
| Apagar histórico pela interface comum. | Não permitido |

### Restrições conhecidas
<ul>
    <li>não pode apagar histórico pela interface comum.</li>
    <li>alterações relevantes devem gerar auditoria.</li>
    <li>informações restritas devem ser acessadas apenas por usuários autorizados</li>
    <li>categorias não devem ficar fixas no código.</li>
</ul>

### Pendências

| Pendência | Impacto | Responsável por decidir |
|---|---|---|
| O Administrador do NEO poderá criar e gerenciar usuários? | Impacta módulo de usuários e perfis. | Produto e Backend. |
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
| Consultar fila. | Conhecido |
| Consultar indicadores. | Conhecido |
| Exportar relatórios. | Conhecido |
| Abrir solicitações para visualização. | Pendente |
| Alterar status. | Não permitido |
| Definir prioridade. | Não permitido |
| Atribuir responsável. | Não permitido |
| Registrar pendências. | Não permitido |
| Registrar mapeamento. | Não permitido |
| Administrar parâmetros. | Não permitido |
| Apagar histórico. | Não permitido |

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

O Admin Root é uma role técnica adicional proposta pelo time. Ele não é um perfil funcional previsto originalmente na especificação, mas foi identificado para apoiar necessidades técnicas, administrativas ou de implantação.

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
| Administrar usuários. | Pendente |
| Administrar roles. | Pendente |
| Administrar parâmetros técnicos. | Pendente |
| Acessar logs técnicos. | Pendente |
| Realizar correções excepcionais. | Pendente |
| Executar ações operacionais comuns. | Não recomendado |
| Apagar histórico pela interface comum. | Não permitido |

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
| O Admin Root poderá administrar usuários e perfis? | Impacta matriz de permissões. | Produto e Backend. |
| O Admin Root poderá acessar todas as solicitações? | Impacta privacidade e segurança. | Produto e Backend. |
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
| Abrir nova solicitação | S | P | P | N | N |
| Consultar próprio protocolo | S | P | S | N | P |
| Visualizar fila completa | N | C | S | S | P |
| Visualizar demandas atribuídas | N | S | S | P | P |
| Registrar triagem | N | S | S | N | P |
| Ajustar categoria | N | S | S | N | P |
| Definir prioridade | N | S | S | N | P |
| Atribuir responsável | N | S | S | N | P |
| Alterar status | N | C | S | N | P |
| Registrar pendências | N | S | S | N | P |
| Registrar mapeamento | N | S | S | N | P |
| Ver observações internas | N | S | S | P | P |
| Consultar histórico | N | C | S | P | P |
| Exportar dados | N | P | S | S | P |
| Administrar categorias | N | N | S | N | P |
| Administrar responsáveis | N | N | S | N | P |
| Administrar parâmetros | N | N | S | N | P |
| Administrar usuários | N | N | P | N | P |
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