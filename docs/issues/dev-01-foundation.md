# [Nova funcao] DEV-01 - Foundation do Abiliio Dev OS

## Contexto

O Abiliio Dev OS sera a fonte central de governanca, workflow, qualidade, arquitetura, IA e documentacao para projetos Abiliio.

Esta DEV-01 foi o bootstrap inicial do proprio Dev OS. A partir da DEV-02, o fluxo completo `Issue -> Planejamento -> Branch -> Implementacao -> QA -> PR -> Review -> Merge` passa a ser obrigatorio para mudancas relevantes.

Issue oficial no GitHub: #1 - [Nova funcao] DEV-01 - Foundation do Abiliio Dev OS.

## Problema

As mesmas instrucoes de desenvolvimento sao repetidas em varios projetos, gerando retrabalho, inconsistencia e perda de contexto.

## Objetivo

Criar a fundacao documental independente do Abiliio Dev OS, sem instalar ferramentas ou montar CI/CD complexo nesta etapa.

## Estado real

- Repositorio GitHub criado em `Abiliioo/Dev-OS`.
- Branch padrao do GitHub definida como `main`.
- Issue oficial #1 criada manualmente no GitHub.
- Branch `feature/dev-01-foundation` criada e publicada.
- Baseline inicial registrado: `65a5264 docs: add dev os foundation`.
- Foundation revisada e homologada.
- Issue #1 deve permanecer aberta ate o merge do Pull Request final da DEV-01.

## Escopo

- Criar estrutura documental inicial.
- Criar `README.md`, `CLAUDE.md` e `AGENTS.md`.
- Criar docs iniciais de workflow, GitHub Flow, qualidade, arquitetura, coding, design, motion, testes, seguranca, observabilidade, deployment e agentes.
- Criar templates de Issue, PR, ADR, RFC e release.
- Criar prompts operacionais.
- Criar papeis iniciais de agentes.
- Criar roadmap inicial.

## Fora de escopo

- GitHub Actions complexas.
- Observabilidade.
- CI/CD completo.
- Datadog, New Relic, OpenTelemetry.
- Stryker, Codecov.
- OmniRoute.
- RTK global.
- Graphify strict.
- Automacoes profundas.
- Infraestrutura de producao.

## Criterios de aceite

- [x] Repositorio local criado.
- [x] Repositorio GitHub criado em `Abiliioo/Dev-OS`.
- [x] Branch padrao definida como `main`.
- [x] Issue oficial #1 criada no GitHub.
- [x] Branch `feature/dev-01-foundation` criada e publicada.
- [x] Baseline `65a5264 docs: add dev os foundation` registrado.
- [x] Arquitetura documental inicial criada.
- [x] Documentos raiz criados.
- [x] Templates iniciais criados.
- [x] Prompts iniciais criados.
- [x] Papeis de agentes criados.
- [x] Entrega apresentada para homologacao antes do primeiro merge.
- [ ] Pull Request final da DEV-01 criado, revisado e mergeado.

## Riscos

- Criar regras amplas demais antes de validar em projetos reais.
- Transformar ferramentas candidatas em obrigatorias sem benchmark.
- Duplicar conteudo demais nos projetos consumidores.

## Dependencias

- Pull Request final da DEV-01.
- Review e merge do Pull Request final para fechamento automatico ou manual da Issue #1.
