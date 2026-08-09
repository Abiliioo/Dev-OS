# Seguranca e Operacao

Avalie conforme o projeto:

- rate limit;
- revisao de seguranca;
- secrets scanning;
- dependency scanning;
- performance budget;
- backups;
- logs;
- monitoramento;
- separacao frontend/backend;
- tratamento de dados pessoais;
- autenticacao;
- autorizacao;
- recuperacao de senha;
- antifraude;
- protecao contra abuso.

## Revisao obrigatoria por contexto

Mudancas que impactem coleta de dados, cookies, tracking, pagamentos, autenticacao, dados pessoais ou obrigacoes legais devem incluir revisao das paginas e politicas legais antes do deploy.

## Quality Gate de seguranca

Dispare review de seguranca quando houver:

- autenticacao;
- autorizacao;
- dados pessoais;
- pagamentos;
- secrets;
- uploads;
- integracoes externas;
- endpoints;
- permissoes;
- logs sensiveis;
- trust boundaries.

Prefira recursos nativos da plataforma quando disponiveis. Em repositorios publicos, secret scanning nativo do GitHub deve ser preferido antes de scanner customizado.

Nao confunda check automatizado com revisao contextual de seguranca.
