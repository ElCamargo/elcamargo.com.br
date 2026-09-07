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
CNAME         elcamargo.com.br
```

## O desenho: enxaimel

Não poder baixar fonte é uma decisão que decide a tipografia inteira: sem
tipo comprado, a personalidade tem que vir da grade, da cor e da escala.

Então o desenho é o **enxaimel** de Blumenau — a estrutura à vista. As vigas
são linhas de 2px que os painéis compartilham: a moldura desenha o topo e a
esquerda, cada painel desenha a direita e a baixo, e as linhas se somam em vez
de dobrar. Os cantos fecham de verdade. Não há sombra, não há canto arredondado
e não há cartão flutuando — a moldura é o ornamento, que é o que o enxaimel faz
com a madeira e o que a empresa diz fazer com as decisões: deixá-las à vista.

Duas vozes tipográficas, as duas do sistema:

- **sem-serifa** para ler;
- **monoespaçada** para o que é registro — rótulo de seção, CNPJ, data, estado
  do produto. Empresa que anota decisão em repositório fala nessa voz.

A cor: azul da casa (o mesmo do Lumus) na madeira, barro claro entre as vigas,
e um verde de araucária como único destaque. O âmbar está reservado ao Lumus —
a cor é do produto, não do site.

Claro e escuro são desenhados os dois, por token. O botão inverte no escuro: se
mantivesse fundo escuro com tinta clara, viraria azul médio com texto quase
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
