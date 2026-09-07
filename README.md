# elcamargo.com.br — o site da empresa

Site institucional da **ElCamargo Soluções em TI LTDA**, de Blumenau/SC.

## Sem build, de propósito

Duas páginas HTML e uma folha de estilo. Sem npm, sem framework, sem etapa de
compilação — o GitHub Pages serve os arquivos direto da `main`, e editar o site é
abrir o arquivo e salvar.

Um site de duas páginas não paga o custo de uma cadeia de ferramentas: cada
dependência é uma coisa que quebra sozinha em seis meses, e este site precisa
continuar de pé sem manutenção.

**Nenhuma requisição externa.** Nem fonte do Google, nem ícone de CDN, nem
medidor de audiência. O favicon é um SVG embutido no próprio HTML. É a mesma
regra que os produtos seguem, e não faria sentido o site que fala deles não
seguir também.

```
index.html    início, produtos, como trabalhamos, contato
lumus.html    a página do Lumus, com os links do app
style.css     a folha, comentada
fontes/       os .woff2, a licença OFL e o LEIA-ME
CNAME         elcamargo.com.br
```

## O desenho: enxaimel

Blumenau é cidade de casa enxaimel, e enxaimel é **estrutura à vista** — a viga
aparece, a junta aparece, nada se esconde atrás de reboco. É a mesma coisa que a
empresa diz fazer com as decisões. O site inteiro sai daí.

**Nada disso usa imagem.** Toda a estética é geometria CSS: sem foto, sem SVG de
banco de imagem, sem direito autoral de terceiro para gerenciar.

Quatro peças:

- **A gaiola.** A moldura desenha topo e esquerda, cada painel desenha direita e
  baixo. As linhas *somam* em vez de dobrar e o canto fecha de verdade — é o que
  separa "estrutura" de "cartõezinhos com borda".
- **A cavilha.** Um quadrado dourado de 7px na junta. Na casa é o pino de madeira
  que trava a viga; na placa de circuito é o pad de solda. O mesmo desenho lê
  como as duas coisas.
- **A empena.** A casa da abertura, desenhada inteira em `clip-path` e
  gradiente: frontão pontudo, pendural, nível, mão-francesa em dois vãos só, e
  enchimento de tijolo nos vãos de baixo.
- **O frechal.** Divisor de seção: viga fina com cavilhas espaçadas.

### Duas armadilhas anotadas no CSS

**O sentido do gradiente é contraintuitivo.** `to top right` aponta o *eixo*
para o canto superior direito, e as faixas saem **perpendiculares** a ele —
desenham `\`, não `/`. Trocar os dois lados põe o telhado de cabeça para baixo.

```
"/"  →  to bottom right          "\"  →  to top right
```

**A casa precisa contrastar com o painel atrás dela.** Com `--painel` e
`--parede-cova` na mesma cor, o `clip-path` recorta uma silhueta perfeita e
invisível. No tema escuro isso inverte: lá `--parede-cova` tem que ficar mais
*claro* que `--painel`.

## A paleta e a tipografia

```
--viga        #241A15   marrom quase preto: a madeira
--terracota   #8C4A2F   a mesma madeira um tom acima, e o tijolo
--parede      #F4F1E9   reboco colonial: fundo das seções
--painel      #FBF9F4   o claro de dentro dos cards
--mata        #14452F   verde escuro: links e ação
--ouro        #B8912F   dourado fosco: cavilha, hover, detalhe
```

O verde e o dourado são o Brasil em versão fosca — nada de saturação de
bandeira. **`--ouro` nunca é texto no claro** (dá só 2,8:1 sobre o reboco): ele
é linha, cavilha e fundo de hover com tinta escura por cima. Menor contraste de
texto medido no site: 5,8:1.

Três vozes: **Fraunces** (serifada) no institucional, **IBM Plex Sans** no texto
corrido, **IBM Plex Mono** no que é registro — rótulo, CNPJ, estado do produto.
Empresa que anota decisão em repositório fala nessa terceira voz.

As fontes são **servidas daqui**, de `fontes/`. Um `<link>` para
`fonts.googleapis.com` quebraria a regra de zero requisição externa e ainda
contaria ao Google cada visita. Ver `fontes/LEIA-ME.md`.

Claro e escuro são desenhados os dois, por token. O botão inverte no escuro: se
mantivesse fundo escuro com tinta clara, viraria marrom médio com texto quase
preto.

## Como publicar

1. **GitHub Pages**: *Settings → Pages → Source → Deploy from a branch →
   `main` / `/ (root)`*.
2. **DNS**, no painel do Registro.br (*ELCAMARGO.COM.BR → DNS*), quatro registros
   A para o apex:

   ```
   @    A    185.199.108.153
   @    A    185.199.109.153
   @    A    185.199.110.153
   @    A    185.199.111.153
   ```

   E, para o Lumus, que mora em outro repositório:

   ```
   lumus    CNAME    elcamargo.github.io.
   ```

3. **Enforce HTTPS** no painel do Pages, depois que o certificado sair — leva de
   minutos a uma hora.

   Se o certificado **não** sair sozinho (o site responde em `http://` e o
   `https://` não abre), o remédio é tirar e recolocar o domínio: *Settings →
   Pages → Custom domain*, apagar o campo, **Save**, digitar
   `elcamargo.com.br` de novo, **Save**. Isso reenfileira a emissão. Só depois
   a caixa *Enforce HTTPS* fica clicável.

## Antes de publicar

- [ ] `contato@elcamargo.com.br` precisa existir. As duas páginas e o rodapé
      apontam para ele, e a ficha da Play Store vai exibi-lo em público.
      Encaminhamento grátis pelo Cloudflare Email Routing, ou caixa real no
      plano gratuito do Zoho Mail.
- [ ] Conferir o texto do `index.html`: ele fala pela empresa.

## Os produtos citados

| Produto | Repositório | Estado |
|---|---|---|
| Lumus — Kids Game Hub | [`ElCamargo/KidsGameHub`](https://github.com/ElCamargo/KidsGameHub) | no ar, público |
| Collectors Community | `ElCamargo/CollectorsCommunityApp` | privado, beta Android em preparação |

O site só afirma o que existe: o Collectors aparece como *em desenvolvimento* e
sem data, porque é o que ele é hoje.

### O endereço do Lumus

Os botões apontam hoje para `elcamargo.github.io/KidsGameHub/`, não para
`lumus.elcamargo.com.br`. O subdomínio já está no DNS, mas **ainda não
responde**: o progresso de quem joga fica gravado no navegador preso ao
endereço em que foi gravado, e a troca só acontece quando todas as famílias que
já usam tiverem salvado a cópia. Apontar para o endereço novo antes disso é
entregar um 404 a quem clicou.

Quando a migração acontecer, trocar os links nas duas páginas e no rodapé.

---

**ElCamargo Soluções em TI LTDA** · CNPJ 57.299.418/0001-69 · Blumenau, Santa Catarina
