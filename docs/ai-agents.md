# AI Workflow

Este e o documento canonico do AI Workflow do Abiliio Dev OS.

O AI Workflow define como agentes de IA participam do trabalho. Ele complementa o GitHub Flow, mas nao o substitui.

- GitHub Flow: controla como o trabalho e rastreado e integrado.
- AI Workflow: decide como executar, com qual agente, com qual contexto e com quais validacoes.

## Fluxo canonico

```text
Contexto -> Planejamento -> Escolha do agente -> Execucao -> Validacao -> Review -> Handoff quando necessario -> Conclusao
```

Use este fluxo de forma proporcional. Uma tarefa pequena nao precisa virar cerimonia pesada, mas uma tarefa relevante nao deve pular contexto, escopo, validacao e review.

## Relacao com o GitHub Flow

O fluxo de integracao continua definido em `docs/github-flow.md`:

```text
Issue -> Planejamento -> Branch -> Implementacao -> QA -> Pull Request -> Review -> Merge -> limpeza/sincronizacao
```

O AI Workflow opera dentro desse fluxo. Em termos praticos:

- a Issue define o problema e o escopo;
- o planejamento decide abordagem, agente e validacoes;
- a branch contem a execucao;
- QA e review verificam resultado real;
- handoff preserva contexto quando o trabalho precisa continuar em outra sessao ou agente.

## Selecao de agente

Papeis preferenciais nao sao exclusividade. Escolha o agente conforme:

- natureza da tarefa;
- necessidade de execucao local;
- profundidade da analise;
- risco;
- contexto disponivel;
- custo/esforco;
- capacidade especifica necessaria.

Nao criar roteador automatico nesta etapa.

## Papeis preferenciais

ChatGPT:

- direcao;
- planejamento;
- priorizacao;
- elaboracao de Issues e sprints;
- consolidacao de contexto;
- revisao critica;
- acompanhamento entre projetos;
- decisao sobre proximos passos.

Claude:

- auditoria;
- arquitetura;
- UI/UX;
- documentacao;
- investigacao;
- revisao profunda;
- analise de decisoes complexas.

Codex:

- implementacao;
- manipulacao local do repositorio;
- refactor controlado;
- testes;
- automacoes;
- correcoes;
- execucao repetitiva;
- validacoes locais.

## Acesso a repositorios privados

Quando ChatGPT participar de review ou homologacao direta via GitHub em um repositorio privado, o repositorio deve estar autorizado na conexao GitHub usada pelo agente.

Valide esse acesso durante o onboarding quando esse modo de trabalho for necessario.

O repositorio deve permanecer privado quando essa for a decisao do projeto. Nao altere sua visibilidade apenas para facilitar acesso de agente.

A ausencia dessa autorizacao nao bloqueia desenvolvimento local, mas limita review e verificacao direta pelo ChatGPT. Nesse caso, declare a limitacao e nao afirme ter verificado diretamente branch, commit, PR, diff ou check remoto.

Nao trate GitHub Connector como requisito universal para projetos onde ChatGPT nao precise de acesso direto ao repositorio.

## Skills

Skills representam modos de atuacao, nao agentes autonomos obrigatorios.

Skills mantidas:

- `designer`;
- `architect`;
- `developer`;
- `reviewer`;
- `qa`;
- `security`;
- `performance`;
- `release-manager`.

Estrutura minima esperada:

- objetivo;
- quando usar;
- responsabilidades;
- limites;
- entradas esperadas;
- saida esperada;
- definicao de concluido.

Sobreposicoes sao aceitaveis quando refletem pontos de vista diferentes. Por exemplo, `reviewer` revisa escopo e regressao; `qa` valida comportamento; `security` aprofunda risco de dados, auth e abuso; `performance` aprofunda custo e gargalo.

## Prompts

Prompts reutilizaveis devem ser curtos e orientados a tarefa.

Estrutura minima recomendada:

- contexto;
- objetivo;
- escopo;
- fora de escopo quando aplicavel;
- entradas relevantes;
- restricoes;
- validacao proporcional;
- retorno esperado.

Regras:

- auditoria nao executa alteracoes sem autorizacao;
- implementacao nao aumenta escopo;
- review verifica diff e resultado real;
- release nao inventa validacoes;
- prompts referenciam documentos canonicos em vez de copia-los integralmente.

## Handoff

Use handoff quando houver valor real em preservar contexto:

- mudanca de chat;
- mudanca de agente;
- sessao longa interrompida;
- investigacao complexa;
- sprint interrompida;
- contexto que precisa sobreviver a sessao.

Conteudo minimo sugerido:

- objetivo;
- estado atual;
- decisoes confirmadas;
- evidencias relevantes;
- arquivos, branches ou commits importantes;
- validacoes executadas;
- pendencias reais;
- proximo passo.

Nao copie toda a conversa. Nao registre raciocinio interno irrelevante.

## Eficiencia de contexto

Principios:

- fonte canonica > copia;
- contexto proporcional a tarefa;
- leitura seletiva antes de leitura massiva;
- nao repetir documentacao ja disponivel;
- logs completos somente quando necessarios;
- relatorios finais objetivos;
- referencie arquivos, commits, Issues e PRs quando isso reduzir ambiguidade;
- nao sacrifique recuperacao de erro, seguranca ou qualidade para economizar tokens.

Nao criar metricas ou benchmarks complexos nesta sprint.

## YAGNI e Ponytail

Antes de criar codigo, regra, prompt, skill ou ferramenta nova, aplique a escada:

1. precisa existir?
2. ja existe no projeto?
3. stdlib resolve?
4. plataforma nativa resolve?
5. dependencia instalada resolve?
6. solucao simples resolve?
7. somente entao criar codigo novo.

Reducao de codigo nunca justifica remover:

- seguranca;
- validacoes necessarias;
- integridade de dados;
- acessibilidade;
- tratamento de erros necessario.

Ponytail fica registrado como referencia externa e candidato a piloto controlado futuro. Nao instalar globalmente, nao adicionar hooks, nao copiar o ruleset externo integralmente e nao recomendar modo `ultra` como padrao.

## Motion e Design Review

Para projetos com UI relevante, use `docs/design.md`, `docs/motion.md` e `skills/designer.md`.

Motion deve comunicar funcao real, como mudanca, estado, hierarquia, continuidade, resposta ou causalidade.

Antes de animar, pergunte:

- precisa se mover?
- melhora entendimento?
- ajuda a perceber mudanca de estado?
- melhora continuidade?
- fornece feedback?

Design Review assistido por IA deve ser proporcional. Use quando houver interface relevante e problema real a revisar; nao crie trabalho apenas para preencher checklist.

`design-motion-principles` fica registrado como referencia externa opcional para Create/Audit em projetos de UI quando houver ganho real. Nao instalar globalmente nesta sprint.

## Estados assincronos e feedback

Quando aplicavel, acoes assincronas relevantes devem ter estados claros:

- `idle`;
- `loading`;
- `success`;
- `error`.

Use feedback proporcional em acoes como salvar, enviar, processar, importar, exportar, upload, pagamento e chamadas externas.

Skeleton screens nao sao obrigatorios. Use somente quando houver espera perceptivel e layout previsivel.

Lazy loading deve ter beneficio real e nao prejudicar LCP ou experiencia inicial.

## Linguagem

Esta secao e a fonte canonica da politica de idioma dos agentes.

Idioma padrao: portugues do Brasil (pt-BR).

Toda comunicacao humana produzida por agentes deve ser escrita em pt-BR,
incluindo:

- respostas e relatorios de progresso;
- documentacao operacional e arquitetural;
- ADRs;
- comentarios de codigo, docstrings e comentarios TODO/FIXME;
- mensagens explicativas em scripts;
- descricoes de Issues e Pull Requests;
- comentarios de revisao.

Podem permanecer em ingles quando houver motivo tecnico:

- identificadores de codigo (funcoes, classes, variaveis, arquivos ja
  consolidados);
- comandos, parametros e flags;
- APIs, endpoints, schemas e nomes de campos externos;
- nomes de bibliotecas, frameworks e tecnologias;
- mensagens literais exigidas por protocolos ou sistemas externos;
- caminhos, slugs e hashes;
- o prefixo de Conventional Commits (`feat:`, `fix:`, `docs:`, etc.) - a
  descricao apos o prefixo segue pt-BR.

Nao traduza identificadores ou termos tecnicos apenas para cumprir esta
regra. Nao faca varredura retroativa de codigo existente somente para
traduzir comentarios; aplique a partir de conteudo novo ou efetivamente
modificado.
