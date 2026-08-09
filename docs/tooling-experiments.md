# Tooling Experiments

Nenhuma ferramenta experimental deve ser colocada no caminho critico sem piloto controlado.

## Ponytail

Repositorio: https://github.com/dietrichgebert/ponytail

Objetivo: forcar raciocinio YAGNI antes de criar codigo novo.

Decisao DEV-03:

- adotar conceitualmente a escada YAGNI/reuse/native/minimum no AI Workflow;
- manter Ponytail como candidato a piloto controlado futuro;
- nao instalar globalmente nesta sprint;
- nao adicionar hooks;
- nao copiar integralmente o ruleset externo;
- nao recomendar modo `ultra` como padrao.

## RTK

Repositorio: https://github.com/rtk-ai/rtk

Objetivo: reduzir output de ferramentas enviado ao agente.

Medir tokens, tempo, clareza, perda de informacao e recuperacao de erro.

## Graphify

Repositorio: https://github.com/Graphify-Labs/graphify

Objetivo: criar knowledge graph local de codigo, documentacao, configs, dependencias e arquitetura.

Pilotos possiveis: CIE, SmartPayBot e DFO.

## Caveman

Repositorio: https://github.com/juliusbrussee/caveman

Objetivo: reduzir verbosidade de respostas.

Garantir compatibilidade com pt-BR antes de adotar.

## OmniRoute

Repositorio: https://github.com/diegosouzapw/OmniRoute.git

Ferramenta experimental para roteamento, fallback, compressao e multiplos providers.

Nao colocar no caminho critico agora.
