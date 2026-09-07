# Especificação de Produto & Engenharia — Sistema de Gestão de Demandas (Intake)

Documento técnico e funcional de referência para os times de **Produto, Frontend, Backend, Segurança e QA**, unificando requisitos de negócio, arquitetura de dados, padrões de validação sincronizada (UI/DB), segurança criptográfica de consulta, esteira de triagem, detecção de similaridade, central unificada de configurações e proposta de branding.

---

## 1. Formulário de Solicitação de Demanda

### 1.1 Bloco 1: Identificação do Solicitante
* **Nome do Solicitante:** Texto. **Obrigatório**.
* **E-mail Corporativo:** Texto com validação de formato corporativo (`xxxxxx@xxxx.xxx`). **Obrigatório**.
* **Área Solicitante:** Texto. **Obrigatório**.
* **Departamento (Comportamento Dinâmico):**
  * **Regra de Renderização:** **Select OU Campo Aberto**.
    * Se o Administrador tiver cadastrado a lista de departamentos na página de configurações, a interface renderiza automaticamente um componente `<Select>` com os departamentos ativos.
    * Caso não existam departamentos cadastrados no sistema, a interface exibe um campo de texto livre aberto para preenchimento manual.
  * **Regra de Obrigatoriedade:** **Padrão: Opcional** (o administrador pode alternar a obrigatoriedade para obrigatório na página de configurações).
* **Gestor Responsável:** Texto. **Obrigatório**.
* **Contato Adicional:** Texto / Telefone / E-mail alternativo. **Opcional**.

### 1.2 Bloco 2: Identificação da Demanda
* **Nome do Processo:** Texto. **Obrigatório**.
* **Título Resumido da Solicitação:** Texto conciso. **Obrigatório**.
* **Tipo de Solicitação:** Enquadramento macro do serviço (ex.: Automação, Melhoria, Manutenção). **Obrigatório**.
* **Categoria da Demanda:** Select funcional com 10 opções base + suporte a novas categorias gerenciadas na página de configurações. **Obrigatório**.
  1. *Automação* — Solicitações de automação de atividades operacionais.
  2. *Melhoria de processo* — Revisão, simplificação ou padronização de fluxo.
  3. *Indicador* — Criação ou evolução de métrica operacional.
  4. *Dashboard ou relatório* — Construção de visualização ou relatório gerencial.
  5. *Análise de dados* — Tratamento, cruzamento ou exploração de dados.
  6. *Padronização* — Definição de modelos, controles ou procedimentos.
  7. *Revisão de processo* — Diagnóstico de processo existente.
  8. *Apoio técnico* — Avaliação ou suporte dentro do escopo do NEO.
  9. *Estudo de viabilidade* — Análise preliminar de aderência, esforço e benefício.
  10. *Outros* — Solicitação ainda não coberta pelas categorias anteriores.
* **Descrição da Necessidade:** Textarea detalhado. **Obrigatório**.
* **Problema ou Oportunidade Identificada:** Textarea. **Obrigatório**.
* **Resultado Esperado:** Textarea (o que se espera alcançar objetivamente). **Obrigatório**.
* **Justificativa da Solicitação:** Textarea (motivo de negócio / por que fazer). **Obrigatório**.

> **Nota:** Justificativa e Resultado Esperado são **dois campos independentes** no formulário de abertura. Na conclusão posterior da triagem/mapeamento interno existe o campo consolidado de `Conclusão da Análise` técnica.

### 1.3 Detecção de Demandas Semelhantes / Possíveis Duplicidades (Alerta Não Impeditivo)
* **Mecanismo de Checagem:** Durante o preenchimento do formulário (ao digitar campos-chave como *Nome do Processo*, *Título Resumido* e *Descrição*), o sistema executa uma análise de similaridade textual em segundo plano contra demandas previamente cadastradas (da mesma área/departamento).
* **Alerta Visual na Interface:** Se for detectada alta correspondência com um chamado anterior, a UI exibe um banner/card informativo destacando:
  > ⚠️ *"Aviso: Identificamos uma solicitação semelhante já cadastrada para este processo (Demanda: [Título / Código de Rastreio]). Verifique se o seu pedido já não está em andamento."*
* **Caráter Não Bloqueante (Soft Warning):** O alerta possui finalidade exclusivamente **orientativa e consultiva**. Ele **NÃO impede** o envio do formulário, permitindo que o solicitante conclua o cadastro caso se trate de uma demanda diferente ou complementar.

### 1.4 Bloco 3: Informações Operacionais (14 Campos Completos)
1. **Descrição Resumida do Processo Atual:** Textarea. **Obrigatório**.
2. **Principais Etapas do Processo:** Textarea em tópicos/passo a passo. **Obrigatório**.
3. **Sistemas Utilizados:** Texto descritivo (softwares, ERPs, planilhas). **Obrigatório**.
4. **Frequência de Execução:** Select/Texto (ex.: Diária, Semanal, Mensal, Por Demanda). **Obrigatório**.
5. **Volumetria Aproximada:** Texto/Numérico (itens/transações processadas). **Obrigatório**.
6. **Quantidade de Pessoas Envolvidas:** Numérico (headcount alocado). **Obrigatório**.
7. **Tempo Médio de Execução:** Texto/Horas (tempo por ciclo). **Obrigatório**.
8. **Esforço Mensal Estimado:** Numérico/Horas totais por mês. **Obrigatório**.
9. **Existência de Controles Manuais:** Sim / Não (+ detalhamento). **Obrigatório**.
10. **Principais Riscos:** Textarea (riscos de erro, compliance, operacionais). **Obrigatório**.
11. **Impacto no Cliente:** Textarea (reflexo no cliente interno/externo). **Obrigatório**.
12. **Impacto Operacional:** Select fixo: `Baixo`, `Médio`, `Alto`, `Crítico`. **Obrigatório**.
13. **Prazo Desejado:** Data limite ideal para implantação. **Obrigatório**.
14. **Criticidade Percebida pelo Solicitante:** Select (`Baixa`, `Média`, `Alta`, `Crítica`). **Obrigatório**.

### 1.5 Bloco 4: Informações Complementares & Anexos
> **Regra Geral:** Todo o bloco complementar é **100% opcional**, devendo a interface sinalizar explicitamente que seu preenchimento é facultativo.

* **Existência de Documentação do Processo:** Sim / Não (+ Detalhes/Links). **Opcional**.
* **Existência de Solução Semelhante:** Sim / Não (+ Detalhes). **Opcional**.
* **Dependência de Outras Áreas:** Sim / Não (+ Quais áreas). **Opcional**.
* **Tratamento de Informações Restritas:** Sim / Não (+ Detalhes de LGPD/Sigilo). **Opcional**.
* **Observações Adicionais:** Textarea livre. **Opcional**.
* **Anexos:** Upload de arquivos (PDF, DOCX, XLSX, PNG, JPG; limite máx. 10 MB por arquivo). **Opcional**.

---

## 2. Perguntas & Respostas Oficiais de Produto (FAQ)

| Pergunta | Resposta Oficial de Produto |
|---|---|
| **Onde os administradores configuram os parâmetros do sistema?** | **Em uma única página centralizada de Configurações.** Todas as parametrizações (pesos da priorização, departamentos, regras de obrigatoriedade, categorias, visibilidade de responsável e usuários) ficam reunidas em uma mesma tela de gestão. |
| **Como funciona a detecção de chamados duplicados/parecidos?** | O sistema compara os dados digitados com chamados existentes e **exibe um alerta na tela**, sinalizando que já existe algo similar. **Não é um impeditivo**: o usuário é apenas avisado e pode prosseguir com o envio normalmente se desejar. |
| **Como funciona o campo "Departamento"?** | **Híbrido (Select ou Texto Livre):** Se houver departamentos cadastrados pelo administrador, o front exibe um `<Select>`. Se a base não possuir departamentos cadastrados, o campo vira um `<input type="text">` aberto. A obrigatoriedade é configurável pelo Admin (padrão: opcional). |
| **Como o solicitante consulta sua solicitação?** | A consulta pública é realizada **OU pelo E-mail Corporativo OU pelo Código Único de Acompanhamento (Token Criptográfico)**. Ao digitar o e-mail, o sistema lista diretamente todas as demandas vinculadas àquele solicitante. **Não há busca pública por protocolo sequencial**, eliminando o risco de varredura manual de chamados de terceiros. |
| **Onde devem ser validados os limites de caracteres?** | **No Frontend (UI) E no Backend/Banco simultaneamente.** A UI deve aplicar limites máximos (`maxLength`) e contadores visuais estritamente alinhados ao schema do banco para evitar truncamento silencioso (*afunilamento de dados*) ou rejeições 500 no envio. |
| **Quais campos do formulário NÃO são obrigatórios?** | • Contato Adicional (Bloco 1)<br>• Departamento (Bloco 1 — padrão opcional)<br>• Bloco 4 Completo (Documentação, soluções semelhantes, dependências, restrições, observações adicionais e anexos). |
| **Qual a diferença entre Tipo de Solicitação e Categoria?** | São duas entidades diferentes: **Tipo** define a modalidade do pedido (ex.: Automação, Manutenção, Nova Demanda); **Categoria** define a especialidade técnica (ex.: Dashboard, Engenharia de Dados, Padronização). |

---

## 3. Resolução Consolidada das Divergências (Decisões Oficiais)

| ID | Item | Descrição da Divergência | Resolução Oficial & Decisão Arquitetural |
|:---:|---|---|---|
| **D-01** | **Justificativa × Resultado Esperado** | Protótipo unificava em 1 textarea; documentação pedia 2 campos separados. | **Dois campos separados na abertura.** O solicitante preenche `justificativa` e `resultadoEsperado` de forma independente. Na conclusão da triagem interna existe outro campo (`Conclusão da Análise`), que unifica resultado e justificativa da análise técnica quando couber. |
| **D-02** | **Problema ou Oportunidade** | Ausente nas telas de protótipo inicial. | **Obrigatório.** O campo `problemaOuOportunidade` é obrigatório no Bloco 2 da UI e no schema da API. |
| **D-03** | **Bloco Operacional (14 Campos)** | Protótipo trazia versão condensada (4 campos); especificação listava 14. | **14 campos obrigatórios completos.** O protótipo era apenas conceitual/resumido; o sistema implementa integralmente os 14 campos operacionais. |
| **D-04** | **Bloco Complementar & Anexos** | Dúvida sobre obrigatoriedade do questionário complementar. | **100% Opcional.** Todo o Bloco 4 é opcional, com limites de 10 MB por anexo e validações de caracteres espelhadas entre UI e DB. |
| **D-05** | **Tipo de Solicitação × Categoria** | Supressão de "Tipo" no protótipo visual. | **Ambos existem no modelo de dados.** Tipo e Categoria são cadastrados e processados separadamente. |
| **D-06** | **Tabela de Acompanhamento × Log de Auditoria** | Protótipo antigo exibia eventos de auditoria ao usuário comum. | **Log de auditoria é 100% interno.** Acesso restrito ao painel administrativo (`GET /audit/:protocol`). O solicitante visualiza apenas o status e o andamento macro da sua solicitação. |
| **D-07** | **Consulta Pública de Solicitações** | Risco de enumeração sequencial de protocolos na busca pública. | **Busca exclusivamente por E-mail OU Código Único de Rastreio (Seed Aleatória / Criptografia).** A busca pública direta por protocolo sequencial (`NEO-2026-XXXX`) foi removida. O solicitante busca via e-mail corporativo (que lista diretamente seus chamados) ou utilizando o token criptográfico único gerado na abertura. |

---

## 4. Padrões de Tipagem, Comprimento e Validação Sincronizada (UI / Banco)

> **Diretriz de Engenharia contra Afunilamento de Dados:** Todo campo com limite no banco de dados deve ter sua restrição espelhada no Frontend via atributo HTML `maxlength`, validação de schema (ex.: Zod/Yup) e contador visual regressivo. Isso impede que textos digitados sofram cortes involuntários ou gerem erros de payload.

| Bloco / Entidade | Campo no Sistema | Tipo no Banco | Tamanho Máx. (`VARCHAR`) | Validação na UI (`maxLength`) | Justificativa / Padrão |
|---|---|---|:---:|:---:|---|
| **Segurança** | `codigoRastreio` | `VARCHAR` | 64 | - | Token único de alta entropia gerado via FPE/Feistel/Seed. |
| **Sistema** | `protocolo` | `VARCHAR` | 32 | - | Identificador interno sequencial (`NEO-2026-00012345`). |
| **Sistema** | `status` | `VARCHAR` | 50 | - | Máquina de estados interna. |
| **Sistema** | `prioridade` / `criticidade` | `VARCHAR` | 30 | - | `Baixa`, `Média`, `Alta`, `Crítica`. |
| **Bloco 1** | `nomeSolicitante` | `VARCHAR` | 150 | 150 | Nomes extensos corporativos. |
| **Bloco 1** | `emailCorporativo` | `VARCHAR` | 254 | 254 | Padrão internacional RFC 5321. |
| **Bloco 1** | `areaSolicitante` | `VARCHAR` | 100 | 100 | Gerências e diretorias. |
| **Bloco 1** | `departamento` | `VARCHAR` | 100 | 100 | Selecionado via Select ou digitado manualmente. |
| **Bloco 1** | `gestorResponsavel` | `VARCHAR` | 150 | 150 | Nome do gestor imediato. |
| **Bloco 1** | `contatoAdicional` | `VARCHAR` | 100 | 100 | Telefone formatado, ramal ou e-mail secundário. |
| **Bloco 2** | `nomeProcesso` | `VARCHAR` | 150 | 150 | Nome formal do fluxo de negócio. |
| **Bloco 2** | `tituloResumido` | `VARCHAR` | 150 | 150 | Título conciso da demanda. |
| **Bloco 2** | `tipoSolicitacao` | `VARCHAR` | 80 | - | Select/Radio de modalidade. |
| **Bloco 2** | `categoriaDemanda` | `VARCHAR` | 80 | - | Select de categoria funcional. |
| **Bloco 2** | `descricaoNecessidade` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Textarea com contador de caracteres na UI. |
| **Bloco 2** | `problemaOportunidade` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Textarea com contador de caracteres na UI. |
| **Bloco 2** | `resultadoEsperado` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Textarea com contador de caracteres na UI. |
| **Bloco 2** | `justificativa` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Textarea com contador de caracteres na UI. |
| **Bloco 3** | `descricaoProcessoAtual` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Textarea narrativo. |
| **Bloco 3** | `etapasProcesso` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Relação de passos da atividade. |
| **Bloco 3** | `sistemasUtilizados` | `VARCHAR` | 255 | 255 | ERPs, planilhas, CRMs envolvidos. |
| **Bloco 3** | `frequenciaExecucao` | `VARCHAR` | 50 | 50 | Periodicidade do processo. |
| **Bloco 3** | `volumetriaAproximada` | `VARCHAR` | 100 | 100 | Ex.: "2.500 faturas/mês". |
| **Bloco 3** | `qtdPessoasEnvolvidas` | `INTEGER` | - | - | Quantidade de operadores. |
| **Bloco 3** | `tempoMedioExecucao` | `VARCHAR` | 60 | 60 | Tempo médio unitário. |
| **Bloco 3** | `esforcoMensalHoras` | `DECIMAL(10,2)` | - | - | Total de horas/mês. |
| **Bloco 3** | `possuiControlesManuais` | `BOOLEAN` | - | - | Flag Sim/Não. |
| **Bloco 3** | `principaisRiscos` | `TEXT` / `VARCHAR` | 2.000 | 2.000 | Textarea de riscos operacionais. |
| **Bloco 3** | `impactoCliente` | `TEXT` / `VARCHAR` | 2.000 | 2.000 | Textarea de impactos na ponta. |
| **Bloco 3** | `impactoOperacional` | `VARCHAR` | 20 | - | Select (`Baixo`, `Médio`, `Alto`, `Crítico`). |
| **Bloco 3** | `prazoDesejado` | `DATE` | - | - | Seletor de data. |
| **Bloco 4** | Campos Sim/Não + Detalhes | `TEXT` / `VARCHAR` | 1.000 | 1.000 | Detalhes de documentação/sistemas similares. |
| **Bloco 4** | `observacoesAdicionais` | `TEXT` / `VARCHAR` | 2.000 | 2.000 | Observações livres do solicitante. |
| **Bloco 4** | `anexoNomeArquivo` | `VARCHAR` | 255 | - | Nome original do arquivo. |
| **Bloco 4** | `anexoStorageUrl` | `VARCHAR` | 500 | - | URI de armazenamento seguro. |
| **Triagem** | `conclusaoAnalise` | `TEXT` / `VARCHAR` | 4.000 | 4.000 | Justificativa e parecer técnico da conclusão. |

---

## 5. Fluxo de Acompanhamento Seguro & Arquitetura Criptográfica

### 5.1 Mecanismo de Consulta Pública
Para evitar ataques de força bruta e varredura sequencial (*IDOR / Protocol Enumeration*), a interface pública `/acompanhar` oferece dois métodos diretos de consulta:

```
                  ┌───────────────────────────────────────────────────────────┐
                  │              TELA DE CONSULTA PÚBLICA                     │
                  └─────────────────────────────┬─────────────────────────────┘
                                                │
                       ┌────────────────────────┴────────────────────────┐
                       ▼                                                 ▼
             [ Opção A: E-mail ]                              [ Opção B: Token Único ]
     Digita o e-mail corporativo cadastrado               Digita o Código Único de Acompanhamento
                       │                                                 │
                       ▼                                                 ▼
        Lista diretamente na tela todas                   Acessa diretamente a visualização
       as solicitações atribuídas àquele                 específica daquela solicitação
                    e-mail
```

* **Consulta por E-mail:** O usuário insere seu e-mail corporativo e a tela carrega e lista imediatamente todas as solicitações (com seus respectivos status, processos e datas) cadastradas sob aquele endereço.
* **Consulta por Código Único:** O usuário insere o código alfanumérico recebido no momento da abertura e acessa diretamente os detalhes daquela demanda.

### 5.2 Implementação Recomendada: Cifra de Feistel / FPE
Para gerar um **Código Único de Rastreio** seguro, não sequencial, único e sem colisões a partir do ID interno do banco de dados, recomenda-se a utilização de:

1. **Cifra de Feistel de Domínio Reduzido (Format-Preserving Encryption - FPE / Ciphers como FF1 ou FF3-1):**
   * Transforma o inteiro sequencial do chamado (ex.: `12345`) em uma sequência alfanumérica pseudoaleatória reversível (ex.: `MAAT-8K3P-9X2M`) usando uma chave secreta do servidor (`SECRET_SEED_KEY`).
   * **Vantagens:** 
     * **Zero Colisão:** Por ser uma permutação pseudoaleatória bijetora, cada ID gera exatamente um código único sem risco de duplicação.
     * **Não Enumerável:** Um atacante não consegue prever o próximo código nem testar sequências manuais.
     * **Sem Custo de Armazenamento Extra:** Pode ser calculado dinamicamente ou persistido na coluna `codigo_rastreio`.
2. **Alternativa via CSPRNG:** Geração de token criptográfico aleatório de alta entropia (ex.: `crypto.randomBytes(16).toString('hex')`) associado com índice de unicidade (`UNIQUE CONSTRAINT`) no banco.

---

## 6. Mapeamento Técnico & Gestão de Responsáveis

### 6.1 Registro do Mapeamento
Campos preenchidos manualmente pelo analista responsável:
* Responsável pelo mapeamento
* Data e Horário
* Duração prevista
* Modalidade (Presencial / Remoto)
* Link da reunião (quando remoto)
* Local (quando presencial)
* Participantes previstos
* Observações
* Status da confirmação

> **Regra Obrigatória:** Todo o registro de horários, links e participantes deve ser realizado de forma **manual** pelo operador, sem integração automática com calendários no MVP.

### 6.2 Cadastro Manual de Responsável
* Nome Completo | E-mail Corporativo | Função / Papel | Especialidades | Categorias Atendidas | Status (`Ativo` / `Inativo`) | Capacidade de Atendimento | Observações Administrativas.

---

## 7. Painel Administrativo, Fila e Triagem

### 7.1 Gestão da Fila Operacional
* **Colunas:** Protocolo Interno, Código de Rastreio, Data de Entrada (SLA), Processo, Área, Categoria, Prioridade, Criticidade, Status, Responsável, Previsão de Mapeamento, Última Atualização.
* **Alertas Visuais:** Indicadores visuais de SLA estourado, pendência aberta e ausência de responsável.
* **Sinalização de Similaridade na Fila:** Chamados que geraram alertas de duplicidade no momento do preenchimento recebem uma flag/ícone de destaque para orientar o analista.

### 7.2 Ações na Triagem & Capacidade de Revisão Total dos Dados
Durante a etapa de triagem técnica, **o analista/operador tem permissão para revisar e corrigir TODOS os dados preenchidos incorretamente pelo usuário solicitante** no momento da abertura (desde erros ortográficos em nomes, departamentos, sistemas utilizados, até ajustes em volumetria e descrição).

> **Garantia de Rastreabilidade (Auditoria Estrita):** Toda e qualquer edição feita pelo analista em dados preenchidos pelo usuário gera automaticamente um registro de log de auditoria com:
> * Campo alterado
> * Valor original enviado pelo usuário
> * Novo valor corrigido pelo analista
> * Identificação do analista e timestamp da alteração

### 7.3 Status de Saída da Triagem
* `Elegível para avaliação` — Prossegue para mapeamento, viabilidade e priorização.
* `Pendente de informações` — Abre campos na tela do solicitante para complementação.
* `Fora do escopo` — Encerra com justificativa técnica formal.
* `Direcionada para outra área` — Transfere a demanda registrando área de destino.
* `Duplicada` — Vincula e referencia a demanda principal (usado caso o usuário tenha enviado a solicitação mesmo após o alerta de similaridade).
* `Cancelada` — Cancela o fluxo com motivo registrado.
* `Backlog` — Mantém a demanda para priorização futura.

### 7.4 Central Unificada de Configurações Administrativas (Página Única)
Para simplificar a gestão e garantir governança centralizada, **todas as opções de parametrização do ecossistema NEO/MAAT ficam concentradas em uma única página de Configurações (`/admin/configuracoes`)**, organizada em abas lógicas:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        PAINEL DE CONFIGURAÇÕES DO SISTEMA                              │
├──────────────┬──────────────┬──────────────┬──────────────┬──────────────┬─────────────┤
│ Formulários  │  Categorias  │ Priorização  │ Similaridade │   Usuários   │ Governança  │
└──────────────┴──────────────┴──────────────┴──────────────┴──────────────┴─────────────┘
```

1. **Aba "Formulário & Campos":**
   * **Cadastro de Departamentos:** Tabela de CRUD de departamentos (adicionar, renomear, desativar). Se a lista estiver vazia, o formulário automaticamente se converte para campo de texto livre.
   * **Obrigatoriedade de Campos:** Chaves seletoras (*toggles*) para ativar/desativar a obrigatoriedade de campos parametrizáveis (ex.: *Tornar preenchimento de Departamento obrigatório*).
   * **Visibilidade do Responsável:** Chave *toggle* para definir se o nome do analista/responsável fica visível ou oculto para o solicitante na consulta pública.
2. **Aba "Categorias da Demanda":**
   * Gestão completa (CRUD) das categorias funcionais: cadastrar novas categorias além das 10 base, editar descrições, definir ordem de exibição e desativar categorias obsoletas.
3. **Aba "Matriz de Priorização & Pesos":**
   * Configuração dos pesos ponderados (de $0.1$ a $5.0$) para cada uma das 10 dimensões analíticas.
   * Calibração das faixas de corte para classificação automática do score final em *Baixa*, *Média*, *Alta* ou *Crítica*.
4. **Aba "Detecção de Similaridade":**
   * Ajuste do nível de sensibilidade / threshold de similaridade textual (ex.: disparar alerta ao atingir 75% de correspondência com chamados anteriores).
5. **Aba "Usuários & Permissões":**
   * Cadastro, edição e revogação de acessos de analistas, triadores e administradores.
6. **Aba "Governança & LGPD":**
   * Definição de políticas de retenção de dados, prazos de expurgo e regras de anonimização automática.

---

## 8. Matriz de Priorização Ponderada

A priorização é calculada com base em **10 critérios**, com notas de **1 a 5**:

1. Impacto Operacional (1 a 5)
2. Risco Operacional (1 a 5)
3. Urgência (1 a 5)
4. Volumetria (1 a 5)
5. Esforço Manual (1 a 5)
6. Impacto no Cliente (1 a 5)
7. Prazo Regulatório (1 a 5)
8. Áreas Impactadas (1 a 5)
9. Alinhamento Estratégico (1 a 5)
10. Complexidade Estimada (1 a 5)

$$\text{Score Final} = \frac{\sum_{i=1}^{10} (\text{Nota}_i \times \text{Peso}_i)}{\sum_{i=1}^{10} \text{Peso}_i}$$

* **Pesos:** Padrão inicial $1.0$ para todas as dimensões, ajustável pelo Administrador na página de configurações.
* **Classificação de Risco:** `Baixa`, `Média`, `Alta` ou `Crítica`.

---

## 9. Histórico de Auditoria & Exportação de Dados

### 9.1 Log de Auditoria (Uso Exclusivo Interno)
Registrado a cada inserção, alteração ou exclusão:
* Protocolo
* Tipo da ação (`CRIACAO`, `ALTERACAO_STATUS`, `ALTERACAO_PRIORIDADE`, `ATRIBUICAO_RESPONSAVEL`, `CORRECAO_DADOS_SOLICITANTE`, `REGISTRO_MAPEAMENTO`, `INCLUSAO_PENDENCIA`, `ALTERACAO_CONFIGURACOES`, `CONCLUSAO`, `CANCELAMENTO`)
* Operador responsável
* Data e horário exatos
* Valor anterior vs. Novo valor
* Observação / Justificativa
* Origem da alteração

### 9.2 Exportação de Dados (CSV / Excel)
* `Protocolo` | `Código de Rastreio` | `Data de Abertura` | `Área` | `Processo` | `Categoria` | `Status` | `Prioridade` | `Responsável` | `Data de Mapeamento` | `Data da Última Atualização` | `Resultado da Triagem` | `Data de Conclusão`.

---

## 10. Requisitos Não-Funcionais & Arquitetura

* **LGPD e Governança:** Rastreabilidade de ciclo de vida do dado desde a captura no formulário até o descarte/anonimização conforme prazos legais de retenção.
* **Segurança e Seeds:** Credenciais de administradores e chaves criptográficas (`SECRET_SEED_KEY` para FPE/Feistel) injetadas via `.env`.
* **Dark Mode:** Compatibilidade nativa com temas claro e escuro.
* **Página Inicial:** Inclusão de atalhos rápidos de navegação e visão panorâmica de chamados.
* **Mecanismo de Similaridade:** Implementação de busca fuzzy / n-gram / trigramas ou busca vetorial de texto no backend para alimentar o card de aviso de demandas similares em tempo de digitação.

---

## 11. Proposta de Naming & Branding: Conceito MAAT

### 11.1 Conceito Mitológico e Conexão com o Produto
Na tradição egípcia, **Maat** representa a deusa primordial da **ordem, verdade, retidão, justiça e equilíbrio cósmico**. Sua principal representação ritualística é a **Pesagem do Coração**, onde o coração era pesado contra a **Pluma da Verdade** em uma balança de perfeita precisão.

**Aplicação ao Sistema de Intake:**
Um sistema de captura e triagem de demandas cumpre a função de:
1. **Estabelecer Ordem:** Transformar pedidos desestruturados em fluxos padronizados.
2. **Pesar Demandas com Justiça:** A matriz ponderada (1 a 5) pesa esforço, risco e valor de forma imparcial.
3. **Equilíbrio e Governança:** Garantir que o trabalho da equipe técnica seja distribuído com equilíbrio e clareza.

### 11.2 Análise Crítica do Nome
* **Vantagens:** Forte peso conceitual, significado alinhado à priorização ponderada e fácil memorização.
* **Riscos:** O termo "Maat" sozinho pode soar abstrato ou estritamente mitológico em contexto corporativo B2B.
* **Recomendação:** Utilizar **Maat** acompanhado de um descritor moderno de software.

### 11.3 Sugestões de Nomes Compostos

| Nome Proposto | Posicionamento Comercial |
|---|---|
| **MAAT Flow** | Enfatiza fluxo contínuo, triagem ágil e governança de processos operacionais. *(Opção Principal)* |
| **MAAT Intake** | Nome técnico corporativo, focado na porta de entrada qualificada de requisições. |
| **MAAT Demand Engine** | Transmite a imagem de motor analítico de priorização e capacidade operacional. |
| **NEO Maat** | Integração natural como módulo de esteira do ecossistema NEO. |

### 11.4 Diretrizes de Identidade Visual e Logos

```
     CONCEITO 1: A PLUMA             CONCEITO 2: AS ASAS              CONCEITO 3: BALANÇA & GLIFO
  (Pena minimalista estilizada      (Asas geométricas de Maat       (Balança moderna formando a
    como símbolo de validação)      como esteira de proteção)         letra 'M' de MAAT Flow)
            
             /|                              \     /                             ___|___
            / |                               \___/                             [   |   ]
           /  |                               /   \                              \__|__/
          /__/                               /_____\                                |
         /                                                                         / \
```

1. **Conceito 1 — A Pluma da Verdade (Check & Validação):**
   * *Descrição:* A pluma de Maat desenhada em traços vetoriais finos e contínuos, com a haste inferior fazendo a curvatura de um símbolo de *check* / aprovação.
   * *Significado:* Simboliza a acurácia dos dados enviados e o filtro técnico da triagem.
2. **Conceito 2 — As Asas de Maat (Proteção & Amplitude):**
   * *Descrição:* Asas estilizadas e abertas em padrão geométrico flat (inspirado na ilustração clássica da deusa), criando uma moldura horizontal para o logotipo.
   * *Significado:* Transmite governança ponta a ponta e acolhimento das demandas operacionais.
3. **Conceito 3 — Balança Ponderada & Tipografia:**
   * *Descrição:* Uma balança de precisão geométrica integrada ao desenho tipográfico da letra **M** da marca **MAAT Flow**.
   * *Significado:* Representação visual direta da matriz de priorização por pesos e notas de 1 a 5.
4. **Paleta de Cores Recomendada:**
   * **Azul Cobalto Profundo (`#0F2B5C`):** Transmite autoridade institucional, segurança e verdade.
   * **Dourado / Ouro Solar (`#D4AF37`):** Remete à precisão, valor de negócio e sofisticação técnica.
   * **Cinza Chumbo (`#1E293B`) e Branco Neve (`#F8FAFC`):** Cores de contraste para excelente legibilidade em modo Claro e Escuro.