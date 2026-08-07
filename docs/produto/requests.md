# Requisitos Funcionais

| Identificador | Nome | Prioridade | Descrição |
| :---: | :---: | :---: | :---: |
| [RF01](#rf01-formulario-de-solicitação) | Formulario de Solicitação | Essencial | O sistema deve poder realizar o cadastro de solicitações por meio de um formulário. Esse formulário possui: *Identificação do solicitante, Identificação da demanda , Informações operacionais, Informações complementares.* |
| RF02 | Protocolação de Solicitações | Essencial | Após o cadastro, o sistema deve: *Validar os dados, Gerar o número do protocolo dessa solicitação, salva-lá, Registrar data e hora de abertura, insirar o pedido(solicitação protocolada) na fila do NEO e apresentar a confirmação*  |
| [RF03](#rf03-fila-centralizada-de-pedidos) | Fila Centralizada de Pedidos | Essencial | Os pedidos devem ser gerenciados/visualizados por meio de uma fila central organizada por: *Protocolo, Data de entrada, Nome do processo, Área solicitante, Categoria, Prioridade, Criticidade, Status, Responsável, Previsão de mapeamento, Última atualização, Indicadores visuais*|
| [RF04](#rf04-triagem-do-pedido) | Triagem do Pedido | Essencial | Durante o ciclo de vida do pedido(triagem), **o responsável deve poder**: *Revisar as informações recebidas, Ajustar a categoria, Registrar a complexidade preliminar, Avaliar aderência ao escopo do NEO, Registrar riscos, Solicitar informações complementares, Atribuir um responsável, Definir a prioridade, Registrar observações internas, Indicar o próximo passo, Alterar o status*. **O Pedido Pode ter os seguintes resultados**: *Elegível para avaliação, Pendente de informações, Fora do escopo, Direcionada para outra área, Duplicada, Cancelada, Backlog*|
| [RF05](#rf05-priorização-de-demanda) | Priorização de Demanda | Essencial | Os pedidos devem possuir um sistema de priorização baseado em critério definidos pelo NEO. Cada critério recebe uma nota de 1 a 5 (pesos configuráveis ou definidos manualmente). As faixas são: *baixa, média, alta e crítica*. **Ajustes manuais devem exigir o registro do motivo** |
|[RF06](#rf06-atribuição-de-responsável-ao-pedido)| Atribuição de Responsável ao Pedido| Essencial | O sistema deverá permitir selecionar o responsável, visualizar sua carga de demandas, substituir a atribuição e manter o histórico |
|[RF07](#rf07-registro-de-mapeamento)|Registro de Mapeamento| Essencial| O sistema deve permitir o controle manual da agenda de mapeamento (reuniões estratégicas para o solucionamento do pedido)|
|RF08| Template de comunicados | Importante | O Sistema deve disponibilizar templates prontos para o envio de comunicações referentes aos pedidos. As comunicões são: *Confirmação de recebimento, Solicitação de informação complementar, Confirmação de agendamento,   Comunicação de não elegibilidade, Direcionamento para outra área, Atualização de status, Encerramento da demanda*|
|[RF09](#rf09-acompanhamento-pelo-solicitante)|Acompanhamento pelo Solicitante|Essencial|O solicitante deverá conseguir consultar sua solicitação por meio do número do protocolo e do e-mail informado no cadastro, ou por outro código identificador do pedido (protocolo)|
|[RF10](#rf10-perfis-de-acesso)|Perfis de Acesso|Essencial| O sistema deve separar níveis de acessos de acordo com os seguintes perfis: Solcitante, Analista/Mapeador. Administrador do NEO, Gestor /Visualizador  |
|[RF11](#rf11-painel-administrativo)|Painel Administrativo|Essencial|O sistema deve possui um painel administrativo que permita consulta e controle da fila, controle sobre os pedidos, exportação de dados, entre outros|
|[RF12](#rf12-histórico-e-auditoria)|Histórico e Auditoria|Essencial|Todas as ações relevantes deverão gerar registro de histórico contendo protocolo, tipo da ação, usuário responsável, data e horário, valor anterior, novo valor, observação e origem da alteração.|
|[RF13](#rf13-dashboard-de-visão-geral)|Dashboard de Visão Geral| Essencial | A solução deverá apresentar um painel resumido com informações obtidas diretamente dos registros cadastrados e filtro por período|
|[RF14](#rf14-exportação-de-dados)| Exportação de Dados | Essencial | O sistema deverá permitir exportar a fila e os principais dados da solicitação em Excel ou CSV, respeitando os filtros aplicados na tela | 
# Especificação das RFs

## RF01 Formulario de Solicitação

### Preocupações de UI/UX
É ideal que o sistema tenha uma foram de reaproveitar as informações do solicitante, para evitar o repetição do usuário

### Campos do Formulário
Identificação do solicitante:
- Nome do solicitante.
- E-mail corporativo.
- Área solicitante.
- Departamento.
- Gestor responsável.
- Contato adicional, quando aplicável


### Identificação da demanda
- Nome do processo.
- Título resumido da solicitação.
- Tipo de solicitação.
- Categoria da demanda. 
    - Automação: Solicitações de automação de atividades operacionais.
    - Melhoria de processo: Revisão, simplificação ou padronização de fluxo.
    - Indicador: Criação ou evolução de métrica operacional.
    - Dashboard ou relatório: Construção de visualização ou relatório gerencial.
    - Análise de dados: Tratamento, cruzamento ou exploração de dados.
    - Padronização: Definição de modelos, controles ou procedimentos.
    - Revisão de processo: Diagnóstico de processo existente.
    - Apoio técnico: Avaliação ou suporte dentro do escopo do NEO.
    - Estudo de viabilidade: Análise preliminar de aderência, esforço e benefício.
    - Outros: Solicitação ainda não coberta pelas categorias anteriores.
- Descrição da necessidade.
- Problema ou oportunidade identificada.
- Resultado esperado.
- Justificativa da solicitação

#### Categorias 
As categorias não deverão ficar fixas diretamente no código. O administrador deverá conseguir cadastrar,
ativar ou desativar categorias.

### Informações operacionais
- Descrição resumida do processo atual.
- Principais etapas do processo.
- Sistemas utilizados.
- Frequência de execução.
- Volumetria aproximada.
- Quantidade de pessoas envolvidas.
- Tempo médio de execução.
- Esforço mensal estimado.
- Existência de controles manuais.
- Principais riscos.
- Impacto no cliente.
- Impacto operacional.
- Prazo desejado.
- Criticidade percebida pelo solicitante.

### Informações complementares
- Existência de documentação do processo.
- Existência de solução semelhante.
- Dependência de outras áreas.
- Tratamento de informações restritas.
- Observações adicionais.
- Anexos, caso a funcionalidade seja viável no ambiente de implantação.

## RF03 Fila Centralizada de Pedidos
A equipe do NEO deverá conseguir ordenar e filtrar a fila por protocolo, período, área, categoria,
prioridade, status, responsável, criticidade, pendência, ausência de responsável e prazo
### Categorias
- Protocolo: Identificação única da solicitação.
- Data de entrada: Controle de antiguidade e SLA.
- Nome do processo:  Identificação objetiva da demanda.
- Área solicitante: Agrupamento e análise por origem.
- Categoria: Classificação funcional.
- Prioridade: Ordenação e direcionamento.
- Criticidade: Sinalização operacional.
- Status: Etapa atual do fluxo.
    1. Solicitação enviada
    2. Aguardando triagem
    3. Em triagem
    4. Pendente de informações
    5. Aguardando mapeamento
    6. Mapeamento agendado
    7. Em mapeamento
    8. Em análise de viabilidade
    9. Elegível
    10. Não elegível
    11. Priorizado
    12. Backlog
    13. Direcionado para outra área
    14. Em desenvolvimento
    15. Em homologação
    16. Concluído
    17. Cancelado  
- Responsável: Pessoa atribuída para condução.
- Previsão de mapeamento: Data planejada ou registrada.
- Última atualização: Controle de movimentação.
- Indicadores visuais: Atraso, pendência e ausência de responsável.

#### Status
Não será obrigatório utilizar todos os status desde a publicação inicial. Cada alteração deverá registrar
status anterior, novo status, data e horário, usuário responsável e justificativa, quando aplicável.

## RF04 Triagem do Pedido
Quando a demanda não for elegível, o registro de justificativa deverá ser obrigatório.
### Ciclo de Vida do Pedido
Criação do Pedido --> Ação do Responsável --> Nova ação ou Conclusão --> Justificativa (obrigatória apenas quando a demanda não é elegível)

### Ações do Responsável

- Revisar as informações recebidas.
- Ajustar a categoria.
- Registrar a complexidade preliminar.
- Avaliar aderência ao escopo do NEO.
- Registrar riscos.
- Solicitar informações complementares.
- Atribuir um responsável.
- Definir a prioridade.
- Registrar observações internas.
- Indicar o próximo passo.
- Alterar o status.

### Resultados
- Elegível para avaliação: Prosseguir para mapeamento, viabilidade ou priorização.
- Pendente de informações: Registrar pendência e aguardar complementação.
- Fora do escopo: Registrar justificativa e orientar o solicitante.
- Direcionada para outra área: Registrar área de destino e justificativa.
- Duplicada: Vincular ou referenciar a demanda principal.
- Cancelada: Registrar motivo do cancelamento.
- Backlog: Manter para priorização futura.

## RF05 Priorização de Demanda
### Perguntas em aberto
1. Cálculo da faixa é baseado nas notas? Quais são os pesos?
1. Ajuste manual é **apenas** sobre a faixa? Ou pode ajustar as notas?
1. Ajuste manual pode ser sobre os pesos? Ou estes pesos são configuravéis a nivel de dev apenas?

### Respostas por hora


### Critérios
- Impacto operacional
- Risco operacional
- Urgência
- Volumetria
- Esforço manual
- Impacto no cliente
- Prazo regulatório
- Áreas impactadas
- Alinhamento estratégico
- Complexidade estimada

## RF06 Atribuição de Responsável ao Pedido

### Ponto de Atenção
Não deverá haver busca automática de usuários no diretório corporativo. A estrutura deverá facilitar essa
integração em uma evolução futura.

### Responsável
O formato do Responsável deve ser:

- Nome: Nome completo.
- E-mail: Informação de contato; sem consulta automática.
- Função: Papel desempenhado no fluxo.
- Especialidades: Temas ou competências de atendimento.
- Categorias atendidas: Categorias para as quais poderá ser selecionado.
- Status: Ativo ou inativo.
- Capacidade de atendimento: Referência de capacidade para visualização.
- Observações: Informações administrativas adicionais

## RF07 Registro de Mapeamento
### Ponto de atenção
Como a primeira versão não realizará consulta automática de agenda, o agendamento deverá ser
controlado manualmente. 

O sistema não deverá criar a reunião nem enviar convites. O objetivo será manter o registro centralizado
e permitir a visualização da próxima atividade relacionada à demanda.

### Registro do Mapeamento
Após combinar o horário pelos canais atuais, a equipe deverá registrar:
- Responsável pelo mapeamento.
- Data.
- Horário.
- Duração prevista.
- Modalidade.
- Link da reunião, quando existente.
- Local, quando presencial.
- Participantes previstos.
- Observações.
- Status da confirmação.

### Preferência de Horários
O formulário poderá permitir que o solicitante informe até três opções de disponibilidade para o primeiro
contato. Essas opções funcionarão apenas como referência; o sistema não deverá validar a agenda dos
participantes.

#### Perguntas em aberto
1. Se a comunicação será feita 'pelos canais atuais', onde que entraria esse formulário de preferência
2. Como é o fluxo de registro de preferências? Quem decide o horário final?

## RF09 Acompanhamento pelo Solicitante

### Ponto de atenção
Observações classificadas como internas não deverão ser exibidas ao solicitante.

### Informações a serem exibidas
- Protocolo: Sempre visível.
- Nome da demanda: Exibição resumida.
- Data de abertura: Data registrada no envio.
- Status: Status público atual.
- Responsável: Exibir **quando permitido**.
- Mapeamento: Previsão ou data registrada.
- Pendências: Somente pendências destinadas ao solicitante.
- Última atualização: Data da movimentação mais recente.
- Próximo passo: Orientação objetiva.
- Conclusão da análise: Resultado e justificativa, quando aplicável


## RF10 Perfis de Acesso

### Perfis
 
|Perfil | Permissões principais |
| :---: | :---: |
|Solicitante | Cadastrar solicitação, consultar protocolo, acompanhar status, visualizar pendências e complementar informações quando permitido. |
|Analista / Mapeador | Consultar demandas atribuídas, registrar análises, alterar status permitidos, registrar mapeamento, observações e pendências. |
|Administrador do NEO | Visualizar todas as solicitações, administrar fila, prioridades, responsáveis, categorias, status, parâmetros, exportações e auditoria. |
|Gestor / Visualizador | Consultar fila e indicadores e exportar relatórios, sem alterar registros operacionais. |

#### Autenticação
A forma de autenticação deverá utilizar a alternativa mais simples aprovada para o ambiente interno. O
reconhecimento automático do usuário e a integração com o diretório corporativo não fazem parte do
escopo inicial.

## RF11 Painel Administrativo

### Ponto de Atenção
A tela de detalhes deverá separar claramente os dados do solicitante, dados da demanda, prioridade,
responsável, mapeamento, pendências, observações internas e histórico.

### Ações Previstas (Administrador)
- Consultar todas as demandas.
- Visualizar e filtrar a fila.
- Abrir os detalhes do pedido.
- Alterar categoria.
- Definir prioridade.
- Atribuir responsável.
- Alterar status.
- Registrar pendências.
- Registrar o mapeamento.
- Incluir comentários internos.
- Registrar conclusão.
- Cancelar uma solicitação.
- Exportar os dados.
- Consultar o histórico.
### Ações Previstas (Gestor)
- Consultar todas as demandas.
- Visualizar e filtrar a fila.
- Abrir os detalhes do pedido.
- Exportar os dados.
- Consultar o histórico.

### Ações Previstas (Analista/Mapeador)
- Consultar demandas Atribuídas.
    - Visualizar e filtrar a fila.
    - Abrir os detalhes do pedido.
    - Alterar status (limitado).
    - Registrar pendências.
    - Registrar o mapeamento.
    - Incluir comentários internos (observações).
- **Verificar se pode**:
    - Registrar conclusão.
    - Consultar o histórico.

### Ações Previstas (Solicitante)
- Cadastrar Solicitação
- Consultar via protocolo.
    - Abrir os detalhes do pedido.
        - Acompanhar Status
    - Visualizar Pendências
    - Complementar informações quando solicitado

## RF12 Histórico e Auditoria
### Ponto de atenção
Os registros de histórico não deverão ser apagados pela interface comum.

### Eventos Mínimos de Auditoria
- Criação da solicitação
- Alteração de status
- Alteração de prioridade
- Atribuição de responsável
- Substituição do responsável
- Registro ou alteração do mapeamento
- Inclusão de pendência
- Conclusão
- Cancelamento

## RF13 Dashboard de Visão Geral

### Ponto de atenção para primeira versão
Nesta primeira versão, não será necessária uma camada analítica avançada. O objetivo será fornecer
visão operacional básica e permitir exportação para outras ferramentas.

### Informações a serem visualizadas:
- Total de solicitações registradas.
- Solicitações por status.
- Solicitações por categoria.
- Solicitações por área.
- Solicitações por prioridade.
- Demandas por responsável.
- Demandas sem responsável.
- Demandas pendentes.
- Demandas fora do prazo.
- Demandas concluídas.
- Demandas elegíveis e não elegíveis.
- Tempo entre abertura e triagem.
- Tempo entre abertura e registro do mapeamento.

## RF14 Exportação de Dados

### Campos Mínimos de Exportação

- Protocolo 
- Data de abertura 
- Área 
- Processo 
- Categoria 
- Status 
- Prioridade 
- Responsável 
- Data de mapeamento 
- Data da última atualização 
- Resultado da triagem 
- Data de conclusão 

### Perguntas em Aberto

-  Quais são as opções de exportação? 
    - Filtros por perído? Responsável?
