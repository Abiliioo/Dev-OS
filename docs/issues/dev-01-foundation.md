# [Nova funcao] DEV-01 - Foundation do Abiliio Dev OS

## Contexto

O Abiliio Dev OS sera a fonte central de governanca, workflow, qualidade, arquitetura, IA e documentacao para projetos Abiliio.

## Problema

As mesmas instrucoes de desenvolvimento sao repetidas em varios projetos, gerando retrabalho, inconsistencia e perda de contexto.

## Objetivo

Criar a fundacao documental independente do Abiliio Dev OS, sem instalar ferramentas ou montar CI/CD complexo nesta etapa.

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

- [ ] Repositorio local criado.
- [ ] Branch `feature/dev-01-foundation` criada.
- [ ] Arquitetura documental inicial criada.
- [ ] Documentos raiz criados.
- [ ] Templates iniciais criados.
- [ ] Prompts iniciais criados.
- [ ] Papeis de agentes criados.
- [ ] Entrega apresentada para homologacao antes do primeiro merge.

## Riscos

- Criar regras amplas demais antes de validar em projetos reais.
- Transformar ferramentas candidatas em obrigatorias sem benchmark.
- Duplicar conteudo demais nos projetos consumidores.

## Dependencias

- Criacao/publicacao do repositorio GitHub `abiliio-dev-os`.
- Criacao da Issue correspondente no GitHub apos o remoto existir.

