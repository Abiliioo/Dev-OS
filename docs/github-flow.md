# GitHub Flow

Este e o documento canonico do GitHub Flow do Abiliio Dev OS.

O objetivo e dar rastreabilidade e qualidade sem transformar o processo em burocracia. Mudancas relevantes seguem o fluxo completo; microalteracoes de baixo risco podem usar um fluxo simplificado, desde que nao voltem a ser feitas informalmente em `main`.

## Fluxo padrao

```text
Issue -> Planejamento -> Branch -> Implementacao -> QA -> Pull Request -> Review -> Merge -> limpeza/sincronizacao
```

## Fluxo simplificado

Pode ser usado para microalteracoes de baixo risco, como correcao pequena de texto, ajuste documental trivial ou organizacao sem impacto de comportamento.

Mesmo no fluxo simplificado:

- nao trabalhe direto em `main` quando a mudanca for relevante;
- mantenha branch curta;
- valide o diff;
- registre o motivo no PR ou commit;
- nao use microalteracao como atalho para esconder trabalho planejavel.

## Issues

Crie Issue para unidades de trabalho planejaveis e relevantes:

- bug;
- melhoria;
- nova funcao;
- divida tecnica relevante;
- refactor relevante;
- auditoria;
- release;
- sprint.

Nao crie Issue separada para cada microajuste descoberto durante uma implementacao ja coberta por uma Issue.

Tipos minimos:

- Correcao;
- Melhoria;
- Nova funcao.

Estrutura minima:

- contexto;
- problema;
- objetivo;
- escopo;
- fora de escopo;
- criterios de aceite;
- riscos;
- dependencias.

Use campos adicionais quando agregarem valor:

- evidencias e passos para reproduzir em bugs;
- impacto esperado em melhorias;
- referencias e restricoes em novas funcoes.

## Issue Templates

A fonte canonica para templates operacionais do GitHub fica em `.github/ISSUE_TEMPLATE/`.

Templates genericos em `templates/` podem ser usados fora do GitHub ou como referencia copiavel, mas nao substituem os templates nativos.

Templates nativos atuais:

- `.github/ISSUE_TEMPLATE/bug.md`
- `.github/ISSUE_TEMPLATE/improvement.md`
- `.github/ISSUE_TEMPLATE/feature.md`

Os templates devem ser curtos o suficiente para uso real.

## Pull Requests

Todo PR destinado a `main` deve:

- mencionar a Issue relacionada;
- explicar o que mudou;
- explicar por que mudou;
- descrever como foi validado;
- listar arquivos ou areas relevantes;
- registrar riscos e limitacoes;
- informar impactos conhecidos;
- declarar fora de escopo;
- registrar proximos passos quando aplicavel.

Use `Closes #123` quando o merge do PR deve fechar a Issue automaticamente.

Use referencias sem fechamento automatico, como `Refs #123` ou `Related to #123`, quando o PR contribui para a Issue mas nao a conclui.

A fonte canonica do template operacional de PR fica em `.github/PULL_REQUEST_TEMPLATE.md`. O arquivo `templates/pull-request.md` e apenas uma versao generica reutilizavel fora do GitHub.

## Branches

Padroes:

- `feature/<descricao>`
- `fix/<descricao>`
- `improvement/<descricao>`
- `refactor/<descricao>`
- `docs/<descricao>`
- `chore/<descricao>`
- `release/<versao>`

Regras:

- use `kebab-case`;
- prefira nomes curtos e descritivos;
- evite nomes genericos como `test`, `temp` ou `changes`;
- crie branches a partir de `main` atualizada;
- nao desenvolva mudancas relevantes diretamente em `main`.

Nao adicione branch por ambiente sem necessidade real.

## Commits

Use Conventional Commits de forma proporcional:

- `feat:`
- `fix:`
- `docs:`
- `refactor:`
- `test:`
- `chore:`
- `perf:`
- `style:`

Mensagens podem permanecer em ingles.

Commits devem:

- representar uma unidade logica;
- evitar arquivos fora de escopo;
- evitar segredos;
- evitar artefatos temporarios;
- ser compreensiveis isoladamente.

Nao instalar Commitlint apenas para impor esta convencao nesta etapa.

## Labels

O conjunto inicial de labels fica documentado em `.github/labels.md`.

Labels devem ter funcao operacional clara. Nao crie label apenas porque parece comum.

Nesta etapa, nao ha automacao de sincronizacao de labels. Se as labels reais do GitHub ainda nao existirem, a pendencia e operacional e deve ser tratada manualmente ou em sprint futura apropriada.

## Milestones

Milestones sao opcionais.

Use quando houver valor real para agrupar:

- uma sprint relevante;
- uma release;
- varias Issues relacionadas;
- uma entrega maior.

Nao crie milestone para microtarefas ou para cada Issue individual.

## Review

Todo PR deve passar por review proporcional antes do merge.

O review minimo verifica:

- Issue relacionada e escopo;
- diff real em `Files changed`;
- arquivos fora de escopo;
- testes ou validacoes;
- riscos;
- limitacoes;
- documentacao afetada;
- regressoes obvias;
- seguranca quando aplicavel;
- consistencia arquitetural quando aplicavel.

Review proporcional nao e burocracia. Mudancas pequenas podem ter review simples; mudancas de alto risco exigem review mais profundo.

## Merge

O GitHub oferece tres estrategias principais.

### Squash and merge

Vantagens:

- mantem `main` mais limpa;
- transforma o PR em uma unidade logica;
- reduz ruido de commits intermediarios.

Desvantagens:

- perde a granularidade original da branch;
- pode esconder a sequencia real de trabalho quando ela tem valor.

Uso recomendado:

- padrao inicial para branches de trabalho quando o PR representa uma unidade logica e commits intermediarios nao agregam valor.

### Merge commit

Vantagens:

- preserva a estrutura da branch;
- mantem commits individuais visiveis;
- deixa claro quando uma linha de trabalho entrou em `main`.

Desvantagens:

- pode deixar o historico mais ruidoso em PRs pequenos;
- exige commits internos mais bem cuidados.

Uso recomendado:

- releases, integracoes maiores ou casos em que preservar a historia da branch tem valor.

### Rebase and merge

Vantagens:

- produz historico linear;
- preserva commits individuais sem merge commit.

Desvantagens:

- pode dificultar leitura de contexto do PR;
- exige cuidado maior com conflitos e historico reescrito.

Uso recomendado:

- opcional, quando o time explicitamente preferir historico linear e souber lidar com o trade-off.

## Limpeza apos merge

Depois do merge:

- confirme que a Issue foi fechada ou atualizada corretamente;
- remova a branch remota quando nao for mais necessaria;
- sincronize o repositorio local com `main`;
- remova a branch local ja mergeada;
- confirme working tree limpa.
