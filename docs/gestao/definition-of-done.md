# Definition of Done

A Definition of Done estabelece os critérios mínimos para que uma entrega seja considerada concluída.

Concluir a implementação ou a documentação não é suficiente. O trabalho precisa atender aos critérios da Issue, ser revisado, validado e integrado ao projeto.

## Critérios obrigatórios

Uma Issue estará concluída quando:

- [ ] todos os critérios de aceite foram atendidos;
- [ ] o entregável definido na Issue foi produzido;
- [ ] a alteração está restrita ao escopo da tarefa;
- [ ] o trabalho foi revisado por outro integrante;
- [ ] não existem comentários ou solicitações de alteração pendentes;
- [ ] as validações aplicáveis foram executadas;
- [ ] as evidências de validação foram registradas;
- [ ] a documentação necessária foi atualizada;
- [ ] nenhuma credencial, dado sensível ou informação restrita foi incluída;
- [ ] a Pull Request foi aprovada;
- [ ] a alteração foi integrada à `main`;
- [ ] a Issue e o card do GitHub Project foram atualizados;
- [ ] pendências identificadas durante o trabalho foram registradas em novas Issues.

## Validações por tipo de trabalho

### Produto

- [ ] o documento ou regra foi revisado;
- [ ] o conteúdo está coerente com o escopo atual;
- [ ] os times impactados foram consultados;
- [ ] a decisão final está registrada.

### UI/UX

- [ ] o fluxo está navegável;
- [ ] os estados previstos foram representados;
- [ ] o handoff está disponível;
- [ ] Produto validou o comportamento;
- [ ] Frontend revisou a viabilidade quando aplicável.

### Frontend

- [ ] a aplicação executa localmente;
- [ ] a interface segue o protótipo aprovado;
- [ ] os estados de interação aplicáveis foram implementados;
- [ ] a navegação por teclado foi verificada quando aplicável;
- [ ] o lint foi executado, quando disponível;
- [ ] o typecheck foi executado, quando disponível;
- [ ] o build foi executado, quando disponível.

### Backend

- [ ] a aplicação executa localmente;
- [ ] as entradas são validadas;
- [ ] os erros são tratados de forma consistente;
- [ ] o contrato da API foi documentado;
- [ ] a funcionalidade foi validada por cliente HTTP;
- [ ] o lint foi executado, quando disponível;
- [ ] o typecheck foi executado, quando disponível.

### Banco de Dados

- [ ] a migration foi executada com sucesso;
- [ ] o schema resultante foi revisado;
- [ ] o seed foi executado, quando aplicável;
- [ ] os relacionamentos e nomes foram validados;
- [ ] o Backend confirmou a integração;
- [ ] nenhuma migration já integrada à `main` foi alterada indevidamente.

## Evidências aceitas

- capturas de tela;
- vídeo curto;
- GIF da navegação;
- link para o Figma;
- resposta de requisição;
- trecho de log;
- resultado do lint;
- resultado do typecheck;
- resultado do build;
- diagrama;
- documento revisado;
- instruções de reprodução.

## Quando a Issue não pode ser considerada concluída

A Issue não deve ser movida para `Done` quando:

- existe apenas uma implementação parcial;
- ainda há comentários pendentes;
- a Pull Request não foi integrada;
- os critérios de aceite não foram atendidos;
- a validação não foi registrada;
- a documentação necessária não foi atualizada;
- existem erros conhecidos que impedem o uso esperado.

`Done` representa uma entrega integrada, revisada e verificável.
