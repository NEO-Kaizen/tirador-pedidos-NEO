# Definition of Ready

A Definition of Ready estabelece os critérios mínimos para que uma Issue esteja pronta para ser iniciada.

Uma tarefa não deve sair do Backlog apenas porque possui um título. Antes de movê-la para `Ready`, o time deve confirmar que existe informação suficiente para executar o trabalho sem depender de suposições importantes.

## Critérios obrigatórios

Uma Issue estará pronta quando:

- [ ] possui contexto suficiente para explicar por que a tarefa existe;
- [ ] possui objetivo claro;
- [ ] possui entregável definido;
- [ ] possui critérios de aceite verificáveis;
- [ ] está vinculada ao time responsável;
- [ ] possui responsável definido ou será atribuída antes do início;
- [ ] possui prioridade definida;
- [ ] está associada à Sprint correspondente;
- [ ] suas dependências são conhecidas;
- [ ] não possui decisão essencial pendente;
- [ ] está pequena o suficiente para ser concluída dentro da Sprint;
- [ ] possui referências necessárias, como protótipo, documento, contrato ou regra de negócio;
- [ ] foi revisada pelo líder do time ou pela pessoa responsável pelo refinamento.

## Critérios por tipo de trabalho

### Produto

- [ ] a necessidade do usuário está descrita;
- [ ] a regra de negócio está clara;
- [ ] o impacto sobre outros fluxos foi considerado.

### UI/UX

- [ ] existe fluxo ou requisito validado;
- [ ] o frame, protótipo ou referência visual está disponível;
- [ ] os estados necessários foram identificados.

### Frontend

- [ ] o comportamento esperado está definido;
- [ ] o protótipo ou especificação visual está disponível;
- [ ] as dependências de API são conhecidas;
- [ ] estados de carregamento, erro, vazio e sucesso foram considerados quando aplicáveis.

### Backend

- [ ] o caso de uso está descrito;
- [ ] entradas e saídas esperadas estão definidas;
- [ ] regras de validação estão claras;
- [ ] dependências com banco ou outros módulos foram identificadas.

### Banco de Dados

- [ ] as entidades e relacionamentos envolvidos estão identificados;
- [ ] o impacto sobre dados existentes foi considerado;
- [ ] a necessidade de migration ou seed foi definida.

## Quando a Issue não estiver pronta

1. mantenha a Issue no Backlog;
2. registre a pendência na própria Issue;
3. identifique quem deve fornecer a informação;
4. comunique o líder do time;
5. retome o refinamento antes de iniciar o desenvolvimento.

Uma Issue em `Ready` representa um compromisso de que o trabalho pode começar com clareza suficiente.
