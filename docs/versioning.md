# Versionamento

O Abiliio Dev OS deve ser versionado.

Exemplos:

- `v1.0.0`
- `v1.1.0`
- `v1.2.0`
- `v2.0.0`

## Compatibilidade

Uma atualizacao do Dev OS nao deve quebrar automaticamente projetos existentes.

Adocao deve ser explicita:

```text
nova versao Dev OS -> review -> projeto decide adotar -> migracao -> validacao -> nova versao registrada
```

## Changelog

Mudancas relevantes devem ser registradas em `CHANGELOG.md`.

