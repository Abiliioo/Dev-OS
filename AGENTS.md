# AGENTS.md

Este repositorio segue o Abiliio Dev OS.

Todas as respostas, comentarios de progresso, relatorios e documentos devem ser produzidos em portugues do Brasil (pt-BR), exceto comandos, paths, slugs, hashes, nomes tecnicos e mensagens de commit quando fizer sentido manter em ingles.

## Workflow padrao

O fluxo canonico esta em `docs/github-flow.md`.

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
