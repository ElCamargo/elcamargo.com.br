# As fontes, hospedadas aqui

Estes arquivos estão no repositório de propósito. O site não faz **nenhuma**
requisição a serviço de terceiro, e um `<link>` para `fonts.googleapis.com`
quebraria isso — além de contar a todo visitante do site, para o Google, que
ele esteve aqui.

| Arquivo | Fonte | Onde é usada |
| --- | --- | --- |
| `fraunces-latin.woff2` | Fraunces (variável, 400–700) | títulos institucionais |
| `plex-sans-latin.woff2` | IBM Plex Sans (variável) | texto corrido |
| `plex-mono-500-latin.woff2` | IBM Plex Mono 500 | rótulo, CNPJ, registro |

Subconjunto **latin** apenas: ele cobre `U+0000-00FF`, onde estão todos os
acentos do português. Os três somam 128 KB. (O peso 600 da monoespaçada foi baixado junto e apagado:
nenhuma regra da folha pedia ele.)

Fraunces e IBM Plex são licenciadas sob a **SIL Open Font License 1.1**, que
permite hospedar e redistribuir. O texto da licença está em `OFL.txt`, ao lado
dos arquivos, como a própria licença exige.

Para trocar ou atualizar: pegue a URL do `.woff2` na folha que o
`fonts.googleapis.com/css2?...` devolve (com User-Agent de navegador moderno,
senão ele entrega woff antigo), baixe o arquivo e substitua aqui. O
`unicode-range` do `@font-face` em `style.css` tem que continuar batendo com o
do bloco `/* latin */` daquela folha.
