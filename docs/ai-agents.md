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

## Eficiencia de modelos, agentes e contexto

Principio central:

> Economize contexto sem economizar validacao.

Evite trabalho repetido, leitura repetida, modelo excessivamente caro,
delegacao desnecessaria e reconstrucao de contexto sem causa. Essa economia
nunca justifica:

- pular teste ou gate aplicavel;
- deixar de validar dado critico;
- confiar cegamente em resumo;
- fazer merge ou deploy sem conferir o estado real;
- inferir codigo que precisa ser lido;
- reduzir seguranca operacional, recuperacao de erro ou qualidade.

### Roteamento conceitual de modelos

Use tres papeis conceituais:

1. exploracao barata: localizar, inventariar e resumir fatos simples;
2. execucao padrao: implementar, testar, documentar e operar o fluxo comum;
3. escalonamento critico: tratar raciocinio dificil, alto risco e review
   independente quando houver ganho real.

O mapeamento concreto pertence somente a esta secao canonica. Prompts,
skills, `AGENTS.md` e arquivos especificos de fornecedor devem referenciar
os papeis, sem repetir a matriz completa. Nao criar roteador automatico ou
infraestrutura complexa apenas para representar esses tres papeis.

> Se nao existir motivo concreto para escalar, use o modelo de execucao padrao.

### Mapeamento Claude

Para ambientes Claude, o mapeamento atual e:

```text
CHEAP_RESEARCH_MODEL = Haiku 4.5
DEFAULT_EXECUTION_MODEL = Sonnet 5
CRITICAL_REVIEW_MODEL = Opus 5.5
```

Fable nao faz parte do roteamento padrao atual.

Haiku 4.5 e preferencial para localizar arquivos, testes e simbolos; fazer
busca textual; mapear commits, Pull Requests e Issues; inventariar
dependencias; resumir logs extensos e realizar pesquisa factual simples.
Nao e o padrao para arquitetura, concorrencia, migrations, seguranca,
implementacao critica, review final ou decisoes dificeis.

Sonnet 5 e o modelo padrao para implementacao, correcao de bugs, testes,
Git/GitHub, refatoracao, documentacao, QA, investigacao normal, resolucao de
conflitos, analise de codigo, deploy ou preflight bem especificado e tarefas
tecnicas comuns.

Opus 5.5 deve ser escalado quando houver ganho claro de raciocinio, como em
arquitetura complexa, investigacao forense, concorrencia dificil,
integridade de dados, migrations criticas, seguranca, incidentes, decisoes
metodologicas, conflito arquitetural, ambiguidade relevante encontrada pelo
modelo padrao, segunda analise independente ou review final de codigo
critico.

Nao use Opus como padrao para busca, edicao mecanica, teste simples,
documentacao normal, refactor localizado ou tarefa administrativa. Nao
comece pelo modelo critico apenas "para garantir".

Quando o runtime permitir controlar esforco:

- Haiku: baixo ou medio normalmente;
- Sonnet: medio por padrao; alto para implementacao complexa ou operacao
  critica;
- Opus: alto somente quando a tarefa justificar;
- evite esforco maximo para tarefas triviais.

Fallback:

- Haiku indisponivel: use Sonnet;
- Opus indisponivel: use Sonnet com esforco alto e review adicional quando
  necessario;
- Sonnet indisponivel: use o melhor modelo de execucao disponivel.

O workflow nao deve bloquear somente porque um modelo especifico nao esta
disponivel. Preserve o papel necessario e registre a adaptacao quando ela
for relevante para risco, custo ou independencia do review.

### Delegacao e subagentes

> Delegue quando a delegacao trouxer beneficio mensuravel.

Execute diretamente quando a tarefa for pequena, localizada, bem
especificada, continuacao direta, exigir poucos arquivos ou custar menos do
que reconstruir contexto em outro agente.

Delegue quando:

- a investigacao for ampla;
- muitos arquivos, commits, Pull Requests ou Issues precisarem ser mapeados;
- pesquisa puder poluir o contexto principal;
- houver tarefas realmente independentes;
- paralelismo trouxer ganho real;
- review independente for necessario;
- preservar o contexto principal trouxer vantagem.

Delegacao nao e obrigatoria. Nao crie subagente apenas porque a ferramenta
permite.

Contrato de subagente:

> Um subagente = uma tarefa delimitada.

Cada subagente deve receber objetivo especifico, escopo explicito,
entregavel verificavel e limite de atuacao. Evite dois agentes pesquisando a
mesma coisa, pedidos como "analise o projeto inteiro" e envio de contexto
completo sem necessidade.

Paralelize somente tarefas independentes. Se B depende de A, execute
`A -> B`, nao `A || B`. Modele as dependencias corretas antes de aumentar a
quantidade de agentes.

O relatorio do subagente deve ser compacto e conter, conforme aplicavel:

- conclusao;
- evidencias;
- arquivos e linhas relevantes;
- commits ou SHAs;
- testes e comandos;
- riscos e incertezas;
- recomendacao, quando solicitada.

Nao retorne arquivo ou log inteiro sem necessidade, contexto irrelevante ou
repeticao da descricao da tarefa.

### Read-report-first

> Leia primeiro o relatorio. Leia diretamente somente o que precisa ser
> confirmado.

O agente principal nao deve reler automaticamente toda a investigacao do
subagente. Leia a fonte diretamente quando o arquivo sera modificado, o
codigo for critico, houver ambiguidade ou conflito, a decisao for de alto
risco, uma afirmacao importante precisar de validacao ou o review exigir
independencia real.

Decisao critica nunca deve depender exclusivamente do resumo de um
subagente.

### Delta-first review

Quando um candidato anterior recebeu review completo e o novo candidato
contem apenas um delta pequeno, comece por `git diff A..B` e revise
prioritariamente o que mudou. Reexecute os gates potencialmente invalidados,
os gates criticos e os que dependem do trecho alterado.

Nao reconstrua automaticamente toda a auditoria. Amplie a revisao quando o
delta puder invalidar uma premissa anterior ou quando a criticidade exigir.

### Fatos ja comprovados

> Nao reinvestigue fatos ja comprovados nesta execucao ou fase, exceto quando
> o novo delta puder invalida-los.

Gate automatizado barato pode ser reexecutado. Nao repita investigacao cara
sem causa; registre a evidencia anterior e a razao de qualquer nova
verificacao.

### Contexto incremental

Prefira carregar:

- base SHA e candidate SHA;
- `git diff`, hashes e resultados `PASS`/`FAIL`;
- linhas e nomes de arquivos especificos;
- Issues, Pull Requests e commits relevantes;
- decisoes e fatos ainda validos.

Evite recarregar historico inteiro, arquivos completos, logs gigantes,
explicacoes ja registradas e decisoes que nao mudaram.

Para arquivos, prefira `busca -> trecho -> arquivo completo somente quando
necessario`. Antes de editar, leia o contexto necessario da regiao e as
invariantes relacionadas.

Para logs extensos, extraia exit code, `PASS`/`FAIL`, warnings relevantes,
stack trace necessario, primeira causa e metricas importantes. Em caso de
falha, expanda apenas o trecho necessario.

Use Git como contexto compacto quando aplicavel:

- `git diff`;
- `git show`;
- `git log --oneline`;
- `git range-diff`;
- `git blame` quando necessario;
- `git merge-base`.

Trate SHAs como referencias compactas de contexto, sem confundir referencia
com validacao do conteudo critico.

### Implementacao e review

Em ambientes que suportem modelos distintos, a preferencia conceitual e:

```text
modelo de execucao padrao implementa
-> modelo critico revisa quando a criticidade justificar
```

Evite que o mesmo agente ou modelo seja a unica revisao independente do
proprio trabalho critico. Tarefas comuns nao exigem escalonamento artificial.

### Overrides de projeto

O mecanismo e:

```text
GLOBAL DEFAULT
+ PROJECT OVERRIDE EXPLICITO
```

Overrides locais legitimos continuam permitidos quando forem mais
restritivos ou necessarios ao contexto. Eficiencia de contexto, modelo ou
custo nao pode reduzir silenciosamente seguranca, validacao critica, gate
obrigatorio ou requisito de qualidade.

Se uma excecao precisar reduzir uma garantia global, registre e justifique a
decisao conforme `docs/quality.md`, incluindo risco, mitigacao e proximo
passo. Nao criar schema complexo de overrides sem necessidade.

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

A regra cobre toda saida textual e comunicacao intermediaria produzida
pelo agente, nao apenas artefatos finais de documentacao. Isso inclui,
durante a propria execucao de uma tarefa:

- mensagens intermediarias, status e titulos de etapa;
- comentarios sobre o que esta sendo feito e por que;
- explicacoes antes e depois de chamadas de ferramenta;
- resumos de resultado, avisos, decisoes e analises;
- explicacoes de mensagens de erro produzidas por ferramentas externas.

Tambem inclui os artefatos finais:

- respostas e relatorios de progresso;
- documentacao operacional e arquitetural;
- ADRs;
- comentarios de codigo, docstrings e comentarios TODO/FIXME;
- mensagens explicativas em scripts;
- descricoes de Issues e Pull Requests;
- comentarios de revisao.

Quando uma ferramenta externa retornar uma mensagem em ingles, a
explicacao do agente sobre essa mensagem deve ser em pt-BR; a mensagem
literal da ferramenta pode ser citada como esta.

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
