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

Observacao metodologica:

Este baseline foi exploratorio. O dado decisorio do piloto RTK e o baseline pareado da Fase 2, recapturado no mesmo HEAD antes de executar RTK.

## RTK

Repositorio: https://github.com/rtk-ai/rtk

Problema alvo:

reduzir output de shell consumido pelo agente.

Ficha pre-instalacao:

- origem/projeto: `rtk-ai/rtk`, GitHub publico;
- release estavel testada: `v0.45.0`;
- licenca atual confirmada: Apache-2.0;
- instalacao documentada: Homebrew, script Linux/macOS, Cargo via Git, binarios pre-built;
- asset Windows usado: `rtk-x86_64-pc-windows-msvc.zip`;
- tamanho do asset: 4.041.041 bytes;
- SHA-256 local: `34cea9009a8099acdaf85147b971d95f65efabfa63fb3aea7d3e2b73e6f517c3`;
- checksum oficial da release: corresponde ao SHA-256 local em `checksums.txt`;
- Windows: binario executado por caminho absoluto em pasta temporaria;
- Codex: documentacao publica menciona `rtk init -g --codex`;
- risco de colisao de nome: documentacao alerta que `cargo install rtk` pode instalar outro projeto chamado RTK; preferir Git URL quando aprovado;
- instalacao local: nao executada;
- integracao com Codex: nao executada;
- `rtk` no PATH local: nao encontrado antes ou depois do piloto;
- executaveis criados: apenas `rtk.exe` extraido em pasta temporaria;
- arquivos/configuracoes alterados: nenhum arquivo conhecido de configuracao RTK foi criado;
- PATH: nao alterado;
- hooks: nao criados;
- rede: usada apenas para baixar release e `checksums.txt` oficiais;
- telemetria: `RTK_TELEMETRY_DISABLED=1` definido somente no processo do piloto;
- secrets: nenhum necessario identificado para baseline;
- cache: nenhum diretorio RTK conhecido foi criado;
- forma de desativar/remover: documentacao menciona `rtk init -g --uninstall` para instalacoes globais e remocao de binario conforme metodo;
- recuperacao de output original: usar comando bruto sem RTK ou `rtk run` para execucao raw conforme `rtk --help`;
- uso isolado em vez de global: validado por caminho absoluto sem PATH/hook.

### Piloto RTK - Fase 2

HEAD pareado:

`8a666077b9fa01eef1b501e2c226dcbab0a3729a`

RTK foi adquirido de release oficial estavel `v0.45.0`, extraido para pasta temporaria fora do repositorio e executado sempre por caminho absoluto. Nenhum `rtk init` foi executado.

### Baseline RAW pareado

| Cenario | Comando | Exit | Linhas | Caracteres | Tempo aprox. ms | Essencial |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| A1 | `git status --short --branch` | 0 | 1 | 83 | 244 | branch e clean/dirty |
| A2 | `git log --oneline --decorate -n 8` | 0 | 7 | 445 | 225 | hashes, mensagens e ponteiros |
| A3 | `git diff --stat main..HEAD` | 0 | 4 | 212 | 143 | arquivos alterados e estatisticas |
| B1 | `rg -n "docs/(github-flow|ai-agents|quality|tooling-experiments)\\.md|Quality Gates|AI Workflow|GitHub Flow|RTK" README.md AGENTS.md CHANGELOG.md ROADMAP.md docs prompts skills .github` | 0 | 50 | 4777 | 52 | arquivos, linhas e ocorrencias |
| C1 | `git ls-files` | 0 | 47 | 1012 | 134 | inventario versionado |
| D1 | `git log --stat --oneline -n 5` | 0 | 55 | 2671 | 193 | commits, arquivos e stats |

### Resultado RTK

| Cenario | Comando | Exit | Linhas | Caracteres | Tempo aprox. ms | Qualidade |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| A1 | `<RTK_EXE> git status --short --branch` | 0 | 1 | 85 | 408 | PRESERVADA |
| A2 | `<RTK_EXE> git log --oneline --decorate -n 8` | 0 | 7 | 429 | 210 | PARCIAL |
| A3 | `<RTK_EXE> git diff --stat main..HEAD` | 0 | 4 | 211 | 336 | PRESERVADA |
| B1 | `<RTK_EXE> rg -n ...` | 0 | 50 | 4777 | 227 | PRESERVADA |
| C1 | `<RTK_EXE> git ls-files` | 0 | 47 | 1012 | 266 | PRESERVADA |
| D1 | `<RTK_EXE> git log --stat --oneline -n 5` | 0 | 55 | 2671 | 376 | PRESERVADA |

### Comparacao RAW vs RTK

| Cenario | Reducao linhas | Reducao caracteres | Diagnostico |
| --- | ---: | ---: | --- |
| A1 | 0.0% | -2.4% | sem ganho; output levemente maior |
| A2 | 0.0% | 3.6% | pequeno ganho; uma linha longa foi compactada/truncada |
| A3 | 0.0% | 0.5% | ganho irrelevante |
| B1 | 0.0% | 0.0% | passthrough efetivo |
| C1 | 0.0% | 0.0% | passthrough efetivo |
| D1 | 0.0% | 0.0% | passthrough efetivo |

Observacoes:

- neste testbed documental pequeno, RTK nao trouxe reducao recorrente de linhas;
- a reducao de caracteres foi inexistente ou marginal;
- A2 teve compactacao pequena, mas com perda parcial de detalhe textual;
- comandos de busca, inventario e log com stat foram essencialmente passthrough;
- tempos medidos sao secundarios e variaram mais do que o ganho de output.

### Recuperacao e falha segura

`rtk --help` mostrou comandos `run` e `proxy`, indicando caminhos para execucao raw/passthrough quando necessario.

Falha segura testada:

- comando RTK: `<RTK_EXE> git show definitely-not-a-real-ref-for-rtk-pilot`;
- exit RTK: 128;
- comando RAW equivalente: `git show definitely-not-a-real-ref-for-rtk-pilot`;
- exit RAW: 128;
- resultado: erro fatal do Git preservado o suficiente para diagnostico.

`rtk gain` retornou exit 1 com erro de inicializacao de tracking database (`Acesso negado`). Nao foi feita correcao por configuracao global; o erro foi registrado como evidencia de friccao operacional neste ambiente.

### Side effects e rollback

Snapshot pre-RTK:

- `rtk` no PATH: nao encontrado;
- `RTK_TELEMETRY_DISABLED` persistente: ausente em User/Machine;
- diretorios conhecidos (`AppData\\Roaming\\rtk`, `AppData\\Local\\rtk`, `.rtk`, `.config\\rtk`): ausentes;
- arquivos RTK no repositorio: ausentes.

Snapshot pos-RTK:

- nenhum diretorio conhecido de config/cache RTK foi criado;
- PATH nao contem a pasta do piloto;
- `rtk` continua ausente do PATH;
- variavel `RTK_TELEMETRY_DISABLED` nao foi persistida;
- repositorio permaneceu intacto.

Rollback:

- removida apenas a pasta temporaria `abiliio-dev-os-rtk-pilot`;
- nenhum arquivo pre-existente foi removido;
- nenhum arquivo do repositorio foi criado para RTK;
- nenhum hook foi criado;
- AGENTS/CLAUDE/Codex nao foram alterados.

### Decisao do piloto RTK

REJEITAR para adocao no Dev OS neste momento.

Justificativa:

- no testbed atual nao houve ganho recorrente de reducao de output;
- varios cenarios foram passthrough efetivo;
- houve friccao com `rtk gain`/tracking database;
- o beneficio observado nao compensa integrar RTK ao Codex ou alterar configuracao global agora.

Esta decisao nao invalida um piloto futuro em repositorio maior e read-only, com outputs naturalmente grandes de testes, builds ou logs, caso haja autorizacao explicita.

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
