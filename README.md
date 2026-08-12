# Abiliio Dev OS

O Abiliio Dev OS e a fonte central de governanca de desenvolvimento para projetos Abiliio.

Ele nao e um produto final para usuario. E um conjunto versionado de principios, fluxos, templates, prompts e papeis de agentes para reduzir repeticao, melhorar qualidade e dar previsibilidade aos projetos.

## Objetivo

Definir, documentar, versionar e evoluir um padrao simples e reutilizavel para projetos como Dicas de Financas Online, SmartPayBot, CIE, Apontamento CBUQ, novos SaaS, automacoes, marketplaces e projetos futuros.

## Principios

- Simplicidade antes de ferramenta.
- Evolucao incremental.
- KISS, YAGNI e DRY com criterio.
- Qualidade baseada em evidencia, nao em burocracia.
- Decisoes relevantes documentadas.
- Branch, validacao e Pull Request antes de merge.
- Regras especificas do projeto vencem regras globais quando forem mais restritivas ou necessarias.

## Estrutura

- `docs/`: guias operacionais e tecnicos.
- `templates/`: modelos reutilizaveis de Issue, PR, ADR, RFC e release.
- `prompts/`: prompts operacionais para planejamento, implementacao, auditoria, review e release.
- `skills/`: responsabilidades de agentes e perfis de atuacao.
- `.github/`: templates nativos do GitHub.

## Versao atual

Versao atual: `v0.1.1-dev`

Esta versao continua sendo um checkpoint de desenvolvimento.

A baseline inicial do Abiliio Dev OS permanece composta por:

- Foundation;
- GitHub Flow;
- AI Workflow;
- Quality Gates;
- CI basico;
- Tooling Experiments.

Este checkpoint incorpora aprendizados retrocompativeis posteriores a baseline: DEV-06 - Consumer Adoption Pilot concluida, adocao minima validada em projeto consumidor real, quality gate minimo validado em repositorio consumidor e regra condicional de acesso do ChatGPT a repositorios privados registrada em `docs/ai-agents.md`.

Nenhuma ferramenta experimental foi promovida automaticamente. Futuras fases continuam condicionadas a necessidade e evidencia real.

## Como adotar em um projeto

Cada projeto deve manter arquivos locais, como `CLAUDE.md` e `AGENTS.md`, com a seguinte referencia:

```md
Este projeto segue o Abiliio Dev OS versao X.

Regras especificas deste projeto:
```

Evite copiar centenas de linhas. A referencia ao Dev OS deve ser suficiente, exceto quando o projeto exigir regras locais.

## Roadmap inicial

1. DEV-01 - Foundation documental: concluida.
2. DEV-02 - GitHub Flow: concluida.
3. DEV-03 - AI Workflow: concluida.
4. DEV-04 - Quality Gates: concluida.
5. DEV-05 - Tooling Experiments: concluida.

DEV-01 a DEV-05 formam o roadmap inicial. DEV-06 - Consumer Adoption Pilot foi a primeira validacao real dessa baseline em projeto consumidor e esta concluida.

Nenhuma DEV-07 foi iniciada. Proximas evolucoes devem continuar surgindo de necessidade e evidencia real.
