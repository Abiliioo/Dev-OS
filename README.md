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

## Versao inicial

Versao atual: `v0.1.0-dev`

Esta versao cobre a foundation documental da DEV-01. Ela ainda nao instala ferramentas, nao define CI/CD complexo e nao torna experimentos obrigatorios.

## Como adotar em um projeto

Cada projeto deve manter arquivos locais, como `CLAUDE.md` e `AGENTS.md`, com a seguinte referencia:

```md
Este projeto segue o Abiliio Dev OS versao X.

Regras especificas deste projeto:
```

Evite copiar centenas de linhas. A referencia ao Dev OS deve ser suficiente, exceto quando o projeto exigir regras locais.

## Roadmap inicial

1. DEV-01 - Foundation documental.
2. DEV-02 - GitHub Flow.
3. DEV-03 - AI Workflow.
4. DEV-04 - Quality Gates.
5. DEV-05 - Tooling Experiments.

