# Tooling Experiments

Este e o documento canonico para experimentos de ferramentas do Abiliio Dev OS.

Nenhuma ferramenta experimental deve ser colocada no caminho critico sem piloto controlado, baseline e plano de remocao.

## Principios

- Evidencia no nosso contexto > promessa externa.
- Benchmark sem baseline nao e evidencia.
- Menos output nao significa automaticamente menos custo total.
- Menos texto so e ganho quando informacao essencial e capacidade de diagnostico sao preservadas.
- Ferramentas diferentes nao devem ser comparadas como concorrentes quando resolvem problemas distintos.
- O experimento deve responder: esta ferramenta melhora suficientemente o problema que se propoe a resolver?
- Uma variavel relevante por vez.
- Nenhuma ferramenta vira padrao global sem evidencia suficiente.

## Protocolo de experimento

Todo experimento deve registrar:

- ferramenta;
- versao testada, quando conhecida;
- hipotese;
- problema alvo;
- ambiente;
- baseline;
- cenario;
- metricas;
- resultado;
- qualidade preservada/perdida;
- limitacoes;
- riscos;
- impacto operacional;
- mudancas realizadas no ambiente;
- rollback;
- decisao.

Decisoes possiveis:

- ADOTAR;
- OPCIONAL;
- CONTINUAR PILOTO;
- REJEITAR.

Nao concluir sem evidencia.

## Metricas

Use metricas proporcionais ao problema.

Para ferramentas de output de shell, como RTK:

- exit code;
- linhas de output;
- caracteres/bytes quando mensuravel de forma simples;
- informacao relevante preservada;
- capacidade de diagnostico;
- esforco necessario;
- tempo aproximado como dado secundario.

Nao estimar custo financeiro/token com precisao falsa.

## Seguranca antes de instalar

Antes de qualquer instalacao futura, verificar:

- origem;
- integridade;
- licenca;
- permissoes;
- arquivos modificados;
- configuracao global;
- PATH;
- hooks;
- rede;
- telemetria;
- secrets;
- cache;
- rollback.

Nenhuma credencial deve entrar no repositorio ou nos registros de experimento.

## Baseline

A ferramenta nunca define o baseline.

O baseline deve ser executado antes de instalar ou ativar a ferramenta.

Para RTK, o baseline e a execucao normal de comandos sem RTK.

## Baseline RTK - Fase 1

Ambiente:

- repositorio: Abiliioo/Dev-OS;
- sistema: Windows / PowerShell;
- branch: `feature/dev-05-tooling-experiments`;
- RTK: nao instalado (`rtk` nao encontrado no PATH);
- Graphify: nao instalado;
- Caveman: nao instalado;
- OmniRoute: nao instalado;
- configuracao global: nao alterada.

| Cenario | Comando | Exit | Linhas | Caracteres | Tempo aprox. ms | Observacao |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| A1 - Git status | `git status --short --branch` | 0 | 1 | 39 | 249 | Confirma branch atual e estado clean/dirty |
| A2 - Historico recente | `git log --oneline --decorate -n 8` | 0 | 6 | 351 | 147 | Preserva hashes, mensagens e ponteiros de branch |
| A3 - Diff/stat contra main | `git diff --stat main..HEAD` | 0 | 0 | 0 | 128 | Baseline sem diff nesta fase antes de editar |
| B1 - Busca de referencias canonicas | `rg -n "docs/(github-flow|ai-agents|quality|tooling-experiments)\\.md|Quality Gates|AI Workflow|GitHub Flow|RTK" README.md AGENTS.md CHANGELOG.md ROADMAP.md docs prompts skills .github` | 0 | 39 | 3167 | 78 | Preserva arquivos, linhas e termos encontrados |
| C1 - Inventario versionado | `git ls-files` | 0 | 47 | 1012 | 125 | Preserva lista de arquivos versionados |
| D1 - Historico verboso com stats | `git log --stat --oneline -n 5` | 0 | 54 | 2626 | 150 | Preserva commits, arquivos alterados e estatisticas |

Informacoes essenciais que nao podem desaparecer no futuro teste com RTK:

- branch atual;
- estado clean/dirty;
- hashes relevantes;
- arquivos encontrados;
- linhas de ocorrencias relevantes;
- erros e warnings;
- arquivos alterados por commit;
- estatisticas de diff quando existirem.

Limitacao do testbed:

O Dev OS e majoritariamente documental e pequeno. Ele e suficiente para baseline inicial de Git, busca e inventario, mas limitado para medir RTK em outputs naturalmente grandes de testes, builds, logs ou monorepos. Se a Fase 2 mostrar pouco output, um segundo repositorio real, somente leitura e autorizado, pode ser necessario para cenarios mais representativos.

## RTK

Repositorio: https://github.com/rtk-ai/rtk

Problema alvo:

reduzir output de shell consumido pelo agente.

Ficha pre-instalacao:

- origem/projeto: `rtk-ai/rtk`, GitHub publico;
- licenca atual confirmada: Apache-2.0;
- instalacao documentada: Homebrew, script Linux/macOS, Cargo via Git, binarios pre-built;
- Windows: ha binario `rtk-x86_64-pc-windows-msvc.zip`; uso deve ser por terminal;
- Codex: documentacao publica menciona `rtk init -g --codex`;
- risco de colisao de nome: documentacao alerta que `cargo install rtk` pode instalar outro projeto chamado RTK; preferir Git URL quando aprovado;
- instalacao local: nao executada;
- `rtk` no PATH local: nao encontrado nesta Fase 1;
- executaveis criados: PENDENTE, depende do metodo de instalacao;
- arquivos/configuracoes alterados: PENDENTE, depende de `rtk init`;
- PATH: PENDENTE;
- hooks: PENDENTE, documentacao menciona hook/rewriter para alguns agentes;
- rede: PENDENTE;
- telemetria: PENDENTE;
- secrets: nenhum necessario identificado para baseline;
- cache: PENDENTE;
- forma de desativar/remover: documentacao menciona `rtk init -g --uninstall` para instalacoes globais e remocao de binario conforme metodo;
- recuperacao de output original: PENDENTE para validacao na Fase 2;
- uso isolado em vez de global: PENDENTE para validacao; deve ser preferido se viavel.

Decisao Fase 1:

CONTINUAR PILOTO.

Motivo: ha problema alvo claro e baseline coletado, mas RTK ainda nao foi instalado nem testado neste ambiente.

## Plano Fase 2 - Piloto RTK

Objetivo:

Comparar baseline normal vs RTK ativo nos mesmos cenarios.

Regras:

- instalar somente apos aprovacao explicita;
- preferir metodo isolado/reversivel;
- registrar versao instalada;
- registrar arquivos/configuracoes alterados;
- nao alterar configuracao global sem autorizacao;
- repetir os cenarios A1, A2, A3, B1, C1 e D1;
- comparar linhas, caracteres, exit code, tempo aproximado e informacao preservada;
- registrar informacao perdida;
- confirmar se erros/warnings continuam visiveis;
- confirmar como recuperar output completo;
- executar rollback ao final se o piloto pedir ambiente limpo.

Criterios de decisao:

- ADOTAR: ganho claro e recorrente, baixo risco e baixa friccao;
- OPCIONAL: ganho claro apenas em certos cenarios;
- CONTINUAR PILOTO: resultado promissor mas evidencia insuficiente;
- REJEITAR: perda de informacao, incompatibilidade, risco ou custo operacional maior que beneficio.

Menos output so e positivo se preservar informacao suficiente para executar e diagnosticar a tarefa.

## Graphify

Repositorio: https://github.com/Graphify-Labs/graphify

Problema alvo:

criar knowledge graph local de codigo, documentacao, configs, dependencias e arquitetura.

Status Fase 1:

- nao instalado;
- nao benchmarkado;
- futuro piloto deve avaliar repositorios grandes e perguntas multi-hop;
- nao adotar se busca/leitura normal resolver com menor custo.

## Caveman

Repositorio: https://github.com/juliusbrussee/caveman

Problema alvo:

reduzir verbosidade de respostas.

Status Fase 1:

- nao instalado;
- nao benchmarkado;
- futuro piloto deve avaliar clareza, completude, pt-BR, handoff e recuperacao de erro;
- resposta menor nao e automaticamente melhor.

## OmniRoute

Repositorio: https://github.com/diegosouzapw/OmniRoute.git

Problema alvo:

roteamento, fallback, compressao e multiplos providers.

Status Fase 1:

- nao instalado;
- nao benchmarkado;
- testar somente depois de experimentos de menor superficie;
- nao migrar configuracao principal do Dev OS durante piloto;
- nao armazenar secrets no repositorio.
