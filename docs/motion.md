# Motion

Motion deve comunicar:

- mudanca;
- estado;
- hierarquia;
- continuidade;
- resposta;
- causalidade.

Nao adicione animacao apenas para "dar vida".

## Perguntas antes de animar

- Isso precisa se mover?
- Melhora entendimento?
- Ajuda a perceber mudanca de estado?
- Melhora continuidade?
- Fornece feedback?

## Aplicacoes adequadas

- transicoes;
- hover;
- focus;
- loading;
- progress;
- feedback;
- entrada e saida;
- mudanca de estado;
- modal;
- lista;
- card;
- tela.

## Evitar por padrao

- motion decorativo;
- hover scale indiscriminado;
- pulsing indiscriminado;
- stagger em toda lista;
- spring exagerado em acoes utilitarias;
- fade-in de todos os elementos;
- animacao de mount para conteudo estatico sem motivo.

Motion deve ser proporcional ao contexto. Interfaces de produtividade e alta frequencia tendem a pedir mais contencao e rapidez. Marketing, portfolio e experiencias playful podem aceitar maior expressividade quando isso fizer parte do objetivo.

## Acessibilidade

Sempre respeite `prefers-reduced-motion`.

Reduced motion nao significa remover todo feedback. Significa fornecer alternativa apropriada.

## Performance

Considere custo de animacao, LCP, responsividade e dispositivos menos potentes.

Nao obrigue biblioteca de animacao. Prefira CSS ou recursos nativos quando forem suficientes.

## Referencia candidata

`design-motion-principles` e uma referencia externa opcional para Create/Audit em projetos de UI relevantes. Nao e obrigatoria e nao deve ser instalada globalmente sem ganho real.

https://github.com/kylezantos/design-motion-principles
