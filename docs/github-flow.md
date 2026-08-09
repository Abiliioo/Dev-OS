# GitHub Flow

## Issues

Toda unidade de trabalho planejavel deve possuir uma Issue.

Nao crie Issue para cada microajuste surgido durante a implementacao. Crie Issues para unidades relevantes:

- sprint;
- bug;
- melhoria;
- nova funcao;
- divida tecnica;
- auditoria;
- refactor;
- release.

Toda Issue deve conter:

- contexto;
- problema;
- objetivo;
- escopo;
- fora de escopo;
- criterios de aceite;
- riscos;
- dependencias.

## Pull Requests

Todo PR para a branch principal deve:

- mencionar a Issue relacionada;
- explicar o que mudou;
- explicar por que mudou;
- descrever como foi validado;
- registrar riscos e limitacoes;
- listar arquivos relevantes;
- informar testes executados;
- informar impactos conhecidos;
- incluir `Closes #123` quando aplicavel.

## Branches

Padroes sugeridos:

- `feature/<descricao>`
- `fix/<descricao>`
- `improvement/<descricao>`
- `refactor/<descricao>`
- `docs/<descricao>`
- `chore/<descricao>`
- `release/<versao>`

## Commits

Use Conventional Commits quando fizer sentido:

- `feat:`
- `fix:`
- `docs:`
- `refactor:`
- `test:`
- `chore:`
- `perf:`
- `style:`

