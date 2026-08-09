# Quality Gates

Qualidade deve ser proporcional a complexidade e risco do projeto.

Nao instale ferramentas apenas porque existem. Primeiro identifique a lacuna, depois escolha a ferramenta.

## Gates possiveis

- lint;
- typecheck;
- testes unitarios;
- testes de integracao;
- testes end-to-end;
- auditoria de documentacao;
- `git diff --check`;
- build;
- smoke tests;
- performance budget;
- seguranca;
- QA visual;
- accessibility review.

## Regra de adocao

Cada projeto ativa somente o que fizer sentido para seu contexto.

Uma ferramenta so deve ser adotada se responder:

- qual problema resolve;
- se o problema realmente existe;
- quanto custa adotar;
- quanto custa manter;
- como remover se nao funcionar;
- se existe alternativa mais simples ou nativa.

