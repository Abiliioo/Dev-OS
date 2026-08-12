# Roadmap

## DEV-01 - Foundation

Status: concluida.

Objetivo: criar o repositorio e a arquitetura documental.

Entregas:

- `README.md`
- `CLAUDE.md`
- `AGENTS.md`
- `docs/`
- `templates/`
- `prompts/`
- `skills/`
- roadmap

Fora de escopo:

- CI/CD complexo;
- observabilidade;
- ferramentas globais;
- automacoes profundas;
- infraestrutura de producao.

## DEV-02 - GitHub Flow

Status: concluida.

- Issue templates.
- PR template.
- Labels.
- Branch naming.
- Conventional Commits.
- Milestones.
- Processo de review.

## DEV-03 - AI Workflow

Status: concluida.

- Skills.
- Prompts.
- Papeis de agentes.
- Motion Principles.
- Ponytail.
- Diretrizes de eficiencia.

## DEV-04 - Quality Gates

Status: concluida.

- Checklists.
- CI basico.
- Testes.
- Lint.
- Build.
- Security checks.
- Performance budgets.

## DEV-05 - Tooling Experiments

Status: concluida.

Resultados:

- RTK: piloto executado; rejeitado no contexto atual.
- Graphify: auditado; candidato a piloto futuro.
- Caveman: auditado; sem justificativa de piloto agora.
- OmniRoute: auditado; sem justificativa de piloto agora.

Nenhum experimento deve virar padrao global sem benchmark e plano de remocao.

## Closeout do roadmap inicial

DEV-01 a DEV-05 formam a baseline inicial do Abiliio Dev OS.

O roadmap inicial esta concluido.

## DEV-06 - Consumer Adoption Pilot

Status: concluida - aprovado com ajustes.

Objetivo: validar a baseline `v0.1.0-dev` em projeto consumidor real.

Resultados:

- auditoria read-only de aplicacao existente;
- criacao controlada de projeto consumidor preservando historico;
- adocao minima do Dev OS sem copia integral da documentacao;
- GitHub Flow aplicado de ponta a ponta;
- quality gate minimo executado com sucesso no consumidor;
- review/homologacao direta via GitHub validada;
- projeto original preservado;
- finding de acesso a repositorios privados identificado;
- finding promovido para Issue #13 e incorporado ao AI Workflow.

A transformacao completa do produto consumidor nao foi necessaria para responder a pergunta central do piloto.

Nenhuma DEV-07 foi iniciada. O proximo passo do Dev OS e uso real, nao expansao proativa de infraestrutura.

## Closeout do checkpoint v0.1.1-dev

DEV-01 a DEV-05 formam a baseline inicial.

DEV-06 foi a primeira validacao real dessa baseline em projeto consumidor.

`v0.1.1-dev` e o checkpoint apos o Consumer Adoption Pilot e seu ajuste retrocompativel.

Proximas mudancas devem continuar surgindo de necessidade real observada nos projetos consumidores.
