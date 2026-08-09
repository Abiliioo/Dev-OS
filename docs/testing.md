# Testing

Testes devem acompanhar risco e impacto.

## Tipos

- unitarios;
- integracao;
- end-to-end;
- smoke tests;
- regressao;
- regressao visual;
- acessibilidade;
- seguranca;
- performance.

## Quando usar

- Unitarios: logica isolada, regras de negocio e funcoes criticas.
- Integracao: contrato entre modulos, banco, APIs ou servicos.
- End-to-end: fluxo central de usuario ou negocio.
- Smoke: verificacao rapida de que o fluxo essencial ainda abre/executa.
- Regressao: bug corrigido ou area com historico de falha.
- Visual/manual: layout, conteudo, UI e experiencia.
- Acessibilidade: interface, teclado, semantica, contraste e estados.
- Seguranca: dados, auth, permissoes, abuso e trust boundaries.
- Performance: fluxo frequente, custo, latencia, LCP, bundle ou volume.

## Regra pratica

Para mudancas pequenas, valide o comportamento tocado.

Para mudancas em contratos compartilhados, fluxos de usuario, dados, auth ou pagamentos, amplie a cobertura.

Correcoes de bugs devem, quando viavel, registrar evidencia de que a regressao foi reproduzida e depois validada.

Nao torne E2E obrigatorio globalmente.

## Ferramentas candidatas

- Playwright;
- Codecov;
- Endtest;
- Stryker;
- ferramentas especificas da stack.

Nenhuma e obrigatoria globalmente.
