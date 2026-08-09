# Quality Gates

Este e o documento canonico de Quality Gates do Abiliio Dev OS.

Quality Gate nao significa rodar todas as ferramentas em toda mudanca. Significa que uma entrega nao avanca enquanto as validacoes necessarias ao seu risco nao estiverem satisfeitas.

Principio central: KISS + YAGNI + risco proporcional.

## Relacao com outros fluxos

- GitHub Flow (`docs/github-flow.md`): controla Issue, branch, PR, review, merge e limpeza.
- AI Workflow (`docs/ai-agents.md`): ajuda a escolher agente, sugerir validacoes, interpretar logs e preparar evidencias.
- Quality Gates: definem o que precisa ser verificado antes de homologacao, merge ou producao.

Agente nao substitui evidencia executada. Evidencia real > afirmacao do agente.

## Modelo de gates

Use tres estados:

- Obrigatorio: necessario para o tipo de mudanca/contexto.
- Condicional: executado quando stack, risco ou escopo justificar.
- Nao aplicavel: sem relacao com a mudanca.

Nao execute validacao artificial apenas para marcar checklist.

Fluxo conceitual:

```text
Escopo -> validacoes locais -> testes aplicaveis -> lint/typecheck/build aplicaveis -> seguranca aplicavel -> performance aplicavel -> UI/UX aplicavel -> documentacao -> checks automatizados -> review -> decisao de merge
```

## Gate de escopo

Obrigatorio para mudanca relevante:

- Issue ou objetivo atendido;
- fora de escopo respeitado;
- diff revisado;
- arquivos fora de escopo identificados;
- documentacao afetada considerada;
- riscos e limitacoes registrados.

## Validacoes locais

Valide proporcionalmente antes do PR.

Possiveis validacoes:

- `git status`;
- revisao de diff;
- `git diff --check`;
- lint;
- typecheck;
- testes;
- build;
- smoke test;
- validacao manual;
- QA visual;
- logs relevantes;
- console/browser errors.

Nao existe comando universal para todas as stacks.

## Testes

Estrategia especializada: `docs/testing.md`.

Resumo pratico:

- unit: logica isolada, regras e funcoes criticas;
- integration: contrato entre modulos, banco, APIs ou servicos;
- end-to-end: fluxo central de usuario ou negocio;
- smoke: verificacao rapida de fluxo essencial;
- regression: bug corrigido ou area com historico de falha;
- visual/manual: UI, layout, conteudo editorial ou experiencia;
- accessibility: interface, teclado, semantica, contraste e estados;
- security: dados, auth, permissoes, abuso e trust boundaries;
- performance: fluxo frequente, custo, latencia, LCP, bundle ou volume.

Bug fix deve ter, quando viavel, evidencia de regressao reproduzida e depois validada.

Nao tornar E2E obrigatorio globalmente.

## Lint, typecheck e build

Lint e condicional:

- use ferramenta existente antes de adicionar nova;
- evite lint meramente estetico;
- evite linters sobrepostos sem ganho claro.

Typecheck e condicional:

- relevante quando a stack tipada ja possui suporte/configuracao.

Build e condicional:

- relevante quando existe processo real de build;
- build de mudanca relevante deve completar sem erro;
- warnings criticos devem ser investigados;
- warnings conhecidos podem ser registrados quando nao bloqueantes.

Nao invente lint, typecheck ou build para projeto documental.

## Seguranca

Detalhamento especializado: `docs/security.md` e `skills/security.md`.

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

No Dev OS publico, nao criar scanner adicional nesta sprint.

Check automatizado nao substitui revisao contextual de seguranca.

## Performance

Performance vira gate quando houver risco ou evidencia relacionada a:

- fluxo frequente;
- LCP;
- bundle;
- queries;
- CPU;
- memoria;
- rede;
- latencia;
- custo operacional;
- volume.

Performance budget so deve existir quando houver metrica, capacidade real de medicao e limite justificavel.

Nao criar numeros arbitrarios.

`skills/performance.md` permanece como perspectiva operacional especializada. Nao criar `docs/performance.md` sem lacuna real.

## UI / UX

Para projetos com UI relevante, use `docs/design.md`, `docs/motion.md` e `skills/designer.md`.

Avalie proporcionalmente:

- estados `idle`, `loading`, `success`, `error`;
- feedback;
- responsividade;
- acessibilidade;
- reduced motion;
- regressao visual;
- comportamento mobile;
- console/browser errors.

Nao aplicar este gate em projeto sem UI.

## Documentacao

Atualizacao documental e obrigatoria quando a mudanca altera:

- comportamento;
- configuracao;
- instalacao;
- arquitetura;
- contrato;
- workflow;
- operacao;
- deployment;
- decisao permanente.

Se nenhuma documentacao foi impactada, nao exija alteracao artificial.

## Niveis de risco

Use apenas tres niveis.

Baixo:

- documentacao;
- texto;
- ajuste isolado sem comportamento.

Medio:

- comportamento localizado;
- componente;
- integracao nao critica.

Alto:

- auth;
- pagamentos;
- dados;
- infraestrutura;
- migrations;
- contratos criticos;
- seguranca;
- fluxo central.

Quanto maior o risco, maior a profundidade de testes, review e evidencia.

Nao criar score matematico.

## Matriz por tipo de projeto

Referencia inicial, nao contrato rigido.

| Tipo | Gates tipicos |
| --- | --- |
| Documental | escopo, diff, `git diff --check`, estrutura Markdown, links quando aplicavel, review |
| Frontend | escopo, lint, typecheck quando existir, testes, build, UI/accessibility quando aplicavel |
| Backend/API | escopo, lint, typecheck quando existir, testes, seguranca, integracao, build/startup quando aplicavel |
| Automacao/script | escopo, lint quando existir, testes ou casos representativos, comportamento de erro, seguranca quando aplicavel |

## Definition of Done

Pronto para homologacao:

- objetivo coberto;
- fora de escopo respeitado;
- validacoes proporcionais executadas;
- riscos e limitacoes registrados;
- pendencias reais declaradas.

Pronto para merge:

- objetivo atendido;
- escopo respeitado;
- gates aplicaveis satisfeitos;
- evidencias reais registradas;
- regressoes relevantes verificadas;
- riscos registrados;
- documentacao afetada atualizada;
- excecoes explicitas;
- checks automatizados aplicaveis verdes.

Pronto para producao:

- pronto para merge;
- deploy/release revisado quando aplicavel;
- rollback ou mitigacao definido quando houver risco operacional;
- smoke test ou validacao pos-deploy planejada quando aplicavel.

## Excecoes

Uma excecao pode ser aceita quando um gate:

- nao se aplica;
- esta temporariamente indisponivel;
- falha por problema conhecido;
- possui falso positivo.

Registre:

- gate;
- motivo;
- risco;
- mitigacao;
- responsavel/decisao quando aplicavel;
- proximo passo se houver.

Nao ignore check vermelho sem registrar motivo e risco.

## Evidencias

Formato objetivo:

- validacao/comando;
- resultado;
- ambiente quando relevante;
- evidencia manual ou screenshot quando necessario;
- limitacao;
- risco residual.

Resumo > log gigante.

Nunca afirme que teste passou sem execucao real.

## Automacao inicial do Dev OS

O primeiro check automatizado do Dev OS e `quality`, definido em `.github/workflows/quality.yml`.

Objetivo unico:

- validar o diff real de Pull Requests destinados a `main` com `git diff --check`.

Ele detecta:

- whitespace errors;
- marcadores de conflito introduzidos no diff.

Ele nao valida:

- links;
- Markdown semantico;
- seguranca contextual;
- arquitetura;
- UI/UX;
- testes de projeto consumidor;
- ausencia de risco.

O check remoto so pode ser validado depois que o PR da DEV-04 existir.
