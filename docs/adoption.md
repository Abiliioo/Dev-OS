# Adocao por Projetos

Todos os projetos devem apontar para o Dev OS, mas regras especificas do projeto vencem regras globais quando forem mais restritivas ou necessarias por contexto.

## Estrutura sugerida

Cada projeto deve manter ao menos o entry point aplicavel ao runtime adotado,
como:

- `CLAUDE.md`
- `AGENTS.md`

Com:

```md
Este projeto segue o Abiliio Dev OS versao X.

Regras especificas deste projeto:
```

## Evite duplicacao

Nao copie centenas de linhas do Dev OS para cada projeto. Referencie a versao adotada e documente apenas excecoes locais.

## Projeto novo

Adote explicitamente uma versao do Dev OS e referencie as fontes canonicas
pelos entry points aplicaveis. Nao copie a matriz de modelos nem a politica
completa para o projeto consumidor.

## Projeto existente

Use o fluxo de migracao explicita:

```text
nova versao -> review -> decisao de adocao -> atualizacao do marcador
-> preservacao das excecoes locais -> validacao -> registro da adocao
```

Nao existe sincronizacao automatica ou bulk sync. Preserve customizacoes
locais durante a migracao.

## Overrides

O projeto pode declarar overrides explicitos em seus entry points. Eles
podem ser mais restritivos ou necessarios ao contexto, mas nao devem reduzir
silenciosamente seguranca, validacao critica, gates obrigatorios ou qualidade.

Excecoes que reduzam uma garantia global devem registrar justificativa,
risco, mitigacao e proximo passo conforme `docs/quality.md`.
