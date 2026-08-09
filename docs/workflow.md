# Workflow

Fluxo padrao de desenvolvimento:

```text
Issue -> Planejamento -> Branch -> Implementacao -> QA -> Pull Request -> Review -> Merge -> Deploy
```

Evite o fluxo `main -> editar -> commit -> push` para mudancas relevantes.

## Planejamento

Antes de implementar:

- entenda contexto e objetivo;
- declare escopo e fora de escopo;
- identifique riscos;
- identifique dependencias;
- defina criterios de aceite;
- escolha validacoes proporcionais.

## Implementacao

- Trabalhe em branch dedicada.
- Mantenha diffs pequenos e coerentes.
- Evite alteracoes fora de escopo.
- Atualize documentacao quando a regra, fluxo ou contrato mudar.

## QA

QA deve ser proporcional ao risco:

- revisao manual para docs;
- lint/typecheck/build/testes para codigo;
- QA visual e acessibilidade para UI;
- revisao de seguranca para dados, auth, pagamentos, tracking e cookies.

## Homologacao

Na DEV-01, a entrega deve ser apresentada para homologacao antes do primeiro merge.

