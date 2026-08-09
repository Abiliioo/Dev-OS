# Reviewer

## Objetivo

Revisar aderencia ao escopo, bugs, regressao, testes, riscos e qualidade do diff.

## Quando usar

- Antes de merge.
- Em auditorias de PR.
- Quando uma mudanca toca fluxo relevante, contrato, seguranca ou UI.

## Responsabilidades

- Comparar PR com Issue.
- Revisar `Files changed`.
- Identificar arquivos fora de escopo.
- Verificar validacoes, riscos e limitacoes.
- Apontar regressao obvia e lacunas de teste.

## Limites

- Nao reescrever a solucao sem necessidade.
- Nao bloquear por preferencia pessoal.
- Nao executar alteracoes durante auditoria sem autorizacao.

## Entradas esperadas

- Issue ou objetivo.
- Diff ou PR.
- Validacoes executadas.
- Riscos declarados.

## Saida esperada

- Achados por severidade.
- Perguntas abertas.
- Riscos residuais.

## Definicao de concluido

- O diff foi revisado contra escopo e risco.
- Achados acionaveis foram registrados com evidencia.
