# AGENTS.md

Este repositorio segue o Abiliio Dev OS.

Idioma padrao: portugues do Brasil (pt-BR) para toda saida textual e
comunicacao intermediaria produzida pelo agente - inclusive durante a
execucao (status, comentarios sobre acoes, explicacoes) - alem dos
artefatos finais (comentarios de codigo, documentacao, relatorios,
Issues e Pull Requests). Politica canonica completa em
`docs/ai-agents.md` (secao Linguagem). Comandos, paths, slugs, hashes,
nomes tecnicos e mensagens de commit podem permanecer em ingles quando
fizer sentido.

## Workflow padrao

Fluxos canonicos:

- GitHub Flow: `docs/github-flow.md`.
- AI Workflow: `docs/ai-agents.md`.
- Quality Gates: `docs/quality.md`.

1. Issue.
2. Planejamento.
3. Branch dedicada.
4. Implementacao.
5. QA.
6. Pull Request.
7. Review.
8. Merge.
9. Deploy ou publicacao.

Evite trabalhar diretamente em `main` para mudancas relevantes.

## Branches

Use nomes descritivos:

- `feature/<descricao>`
- `fix/<descricao>`
- `improvement/<descricao>`
- `refactor/<descricao>`
- `docs/<descricao>`
- `chore/<descricao>`
- `release/<versao>`

## Qualidade

Antes de concluir uma entrega:

- revise o escopo contra a Issue;
- rode validacoes proporcionais ao tipo de mudanca;
- confira `git diff --check` quando houver edicoes de texto/codigo;
- registre testes ou validacoes executadas;
- declare limitacoes e riscos conhecidos.

## Arquitetura

- Aplique YAGNI antes de criar codigo novo.
- Reutilize componentes, dependencias e recursos existentes.
- Prefira solucao nativa quando suficiente.
- Crie abstracao apenas quando ela remover complexidade real.
- Documente decisoes relevantes em `templates/adr.md`.

## Definicao de pronto

Uma entrega esta pronta para homologacao quando:

- o objetivo esta coberto;
- o fora de escopo foi respeitado;
- documentos afetados foram atualizados;
- validacoes proporcionais foram executadas;
- riscos e proximos passos foram registrados.
