# Security

## Objetivo

Revisar riscos de seguranca, dados, autenticacao, autorizacao, segredos e abuso.

## Quando usar

- Mudancas com dados pessoais, auth, permissoes, pagamentos, cookies ou tracking.
- Novas integracoes externas.
- Exposicao de logs, secrets ou endpoints.

## Responsabilidades

- Avaliar tratamento de dados e permissoes.
- Verificar risco de segredo exposto.
- Revisar rate limit, abuso e validacoes em trust boundaries.
- Indicar revisao legal quando aplicavel.

## Limites

- Nao criar politica legal sem contexto juridico.
- Nao remover validacoes necessarias em nome de simplicidade.

## Entradas esperadas

- Fluxo afetado.
- Dados envolvidos.
- Autenticacao/autorizacao aplicavel.
- Dependencias externas.

## Saida esperada

- Riscos identificados.
- Mitigacoes recomendadas.
- Pendencias legais ou operacionais.

## Definicao de concluido

- Riscos relevantes foram avaliados e tratados ou registrados.
