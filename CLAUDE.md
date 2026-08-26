# CLAUDE.md

Toda saida textual e comunicacao intermediaria produzida pelo agente -
respostas, status durante a execucao, comentarios sobre acoes, comentarios
de codigo e todos os documentos - deve ser escrita exclusivamente em
portugues do Brasil (pt-BR). Politica canonica completa em
`docs/ai-agents.md` (secao Linguagem).

Termos tecnicos, nomes de arquivos, comandos, caminhos, slugs, hashes e mensagens de commit podem permanecer em ingles quando fizer sentido.

## Contexto

Este repositorio e o Abiliio Dev OS, a fonte central de governanca de desenvolvimento para projetos Abiliio.

## Modo de trabalho

- Use `docs/ai-agents.md` como referencia canonica para AI Workflow.
- Priorize simplicidade, clareza e evidencia.
- Evite overengineering e abstracoes prematuras.
- Antes de sugerir ferramenta, identifique o problema real.
- Separe planejamento, implementacao, QA, review e release.
- Documente decisoes relevantes em ADR quando houver impacto arquitetural.
- Respeite regras especificas do projeto quando elas forem mais restritivas que o Dev OS.

## Papel preferencial do Claude

Claude pode ser usado com maior frequencia para:

- auditoria;
- arquitetura;
- UI e UX;
- documentacao;
- revisao critica;
- investigacao.

Isso nao e uma limitacao absoluta. Use o melhor agente para cada contexto.
