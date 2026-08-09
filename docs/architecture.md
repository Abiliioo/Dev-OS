# Arquitetura

## Regras globais

- Evite overengineering.
- Evite abstracoes prematuras.
- Evite bottlenecks arquiteturais.
- Componentize quando houver ganho real.
- Aplique DRY com criterio.
- Nao reconstrua componentes existentes.
- Reutilize plataforma e dependencias ja instaladas antes de criar solucao propria.
- Prefira solucoes nativas quando suficientes.
- Mantenha separacao clara de responsabilidades.
- Documente decisoes arquiteturais relevantes.

## Escada YAGNI

Antes de criar codigo novo, pergunte:

1. Isso realmente precisa existir?
2. Ja existe algo equivalente no projeto?
3. A linguagem ou stdlib resolve?
4. A plataforma resolve?
5. Ja existe dependencia instalada?
6. Uma solucao simples resolve?
7. So entao crie codigo novo.

## ADR

Use ADR para decisoes com impacto em:

- arquitetura;
- stack;
- dados;
- seguranca;
- deploy;
- dependencia relevante;
- contrato entre modulos ou servicos.

