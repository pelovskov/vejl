Denne side viser de vigtigste Markdown-muligheder. Kig i **kildefilen**
`markdown-eksempel.md` for at se, hvordan hver ting er skrevet.

---

## 1. Overskrifter

Skrives med `#`. Ét `#` = største overskrift, seks `######` = mindste.
Brug kun ét `#` pr. side (Jekyll-temaer laver ofte selv sidetitlen fra
front matter, så start gerne dine afsnit med `##`).

## 2. Tekst

Almindelig tekst skrives bare i en løbende linje. En tom linje starter et
nyt afsnit.

*kursiv* med enkelt stjerne, **fed** med dobbelt stjerne, ***begge dele***,
~~gennemstreget~~ med to tildeer.

To mellemrum sidst på en linje  
giver et linjeskift uden nyt afsnit.

`kode midt i teksten` skrives med backticks.

## 3. Lister

Punktopstilling:

- Første punkt
- Andet punkt
  - Underpunkt (indryk 2 mellemrum)
  - Endnu et underpunkt
- Tredje punkt

Nummereret:

1. Gør dette
2. Så dette
3. Til sidst dette

Afkrydsningsliste:

- [x] Opgave der er klaret
- [ ] Opgave der mangler

## 4. Links og billeder

[Almindeligt link](https://example.com)

[Link til en anden side på dit eget site]({{ site.baseurl }}/en-anden-side/)

Billede:

![Beskrivende tekst til billedet](/assets/billeder/eksempel.jpg)

Billede der også er et link:

[![Beskrivende tekst](/assets/billeder/eksempel.jpg)](https://example.com)

Vil du styre størrelsen, må du bruge HTML — det virker fint i Markdown:

<img src="/assets/billeder/eksempel.jpg" alt="Beskrivende tekst" width="400">

## 5. Citat

> Sådan laver man et citat.
>
> — Kilden

## 6. Kode

Kodeblok med farvelægning — angiv sproget efter de tre backticks:

```html
<p>Hej verden</p>
```

```css
body { font-family: Georgia, serif; }
```

## 7. Tabel

| Kolonne | Beskrivelse        | Bemærkning |
|---------|--------------------|------------|
| A       | Første kolonne     | venstre    |
| B       | Anden kolonne      | venstre    |
| C       | Tredje kolonne     |            |

Justering styres med kolon i stregen:

| Venstre | Midt | Højre |
|:--------|:----:|------:|
| x       |  x   |     x |

## 8. Vandret streg

Tre bindestreger på en linje for sig:

---

## 9. Fodnote

Her er en påstand med en note.[^1]

[^1]: Og her er noten. Den vises automatisk nederst på siden.

---

## 10. Fold ud og fold sammen

Det er HTML — `<details>` og `<summary>` — og det virker direkte i
Markdown-filer på GitHub Pages.

<details>
<summary>Klik her for at se mere</summary>

Indholdet her er skjult, indtil man klikker.

</details>

**Vigtigt om Markdown inde i en foldeboks:** Jekyll bruger kramdown, og
den behandler som udgangspunkt ikke Markdown inde i HTML-blokke. Du har to
muligheder:

Enten en tom linje efter `</summary>` og før `</details>` (som ovenfor —
så virker det i de fleste tilfælde), eller `markdown="1"` på taggen:

<details markdown="1">
<summary>Foldeboks med rigtig Markdown indeni</summary>

- Punkt et
- Punkt to

Her kan man også have **fed tekst**, links og billeder.

![Eksempelbillede](/assets/billeder/eksempel.jpg)

</details>

En boks der er åben fra start — tilføj `open`:

<details open markdown="1">
<summary>Denne er foldet ud på forhånd</summary>

Klik for at folde sammen.

</details>

Flere bokse under hinanden fungerer som en slags harmonika:

<details markdown="1">
<summary>Spørgsmål 1</summary>

Svar 1.

</details>

<details markdown="1">
<summary>Spørgsmål 2</summary>

Svar 2.

</details>

---

## 11. Plus og minus i stedet for trekanten

Standardmarkøren er en lille trekant. Vil du hellere have **+** og **−**,
skal der lidt CSS til. Læg det i din CSS-fil (fx `assets/css/style.scss`),
eller sæt det i en `<style>`-blok øverst på selve siden:

```css
details > summary {
  list-style: none;          /* fjerner trekanten i Firefox m.fl. */
  cursor: pointer;
  padding: 0.5em 0.5em 0.5em 1.8em;
  position: relative;
  background: #f4f4f4;
  border-radius: 4px;
  font-weight: 600;
}

details > summary::-webkit-details-marker {
  display: none;             /* fjerner trekanten i Safari/Chrome */
}

details > summary::before {
  content: "+";
  position: absolute;
  left: 0.6em;
  font-weight: 700;
}

details[open] > summary::before {
  content: "−";              /* minustegn (U+2212), pænere end bindestreg */
}

details > div,
details > p {
  padding: 0.5em 1em;
}
```

Resultatet ser sådan ud:

<style>
.demo details > summary { list-style: none; cursor: pointer; padding: .5em .5em .5em 1.8em; position: relative; background: #f4f4f4; border-radius: 4px; font-weight: 600; }
.demo details > summary::-webkit-details-marker { display: none; }
.demo details > summary::before { content: "+"; position: absolute; left: .6em; font-weight: 700; }
.demo details[open] > summary::before { content: "−"; }
</style>

<div class="demo" markdown="1">

<details markdown="1">
<summary>Prøv at klikke her</summary>

Nu står der et minus i stedet for et plus.

</details>

</div>

---

## 12. Ting der er værd at vide

- **Front matter** øverst (de tre streger med `layout:` og `title:`) skal
  være allerførst i filen, ellers behandler Jekyll ikke siden.
- **Filnavne**: brug små bogstaver og bindestreger, ingen æ, ø, å eller
  mellemrum. `min-vejledning.md` — ikke `Min Vejledning.md`.
- **Stier til billeder** starter med `/` fra roden af dit site. Ligger
  siden i en undermappe, er det stadig `/assets/...`.
- **HTML virker** overalt i Markdown, så du kan altid falde tilbage på det,
  når Markdown ikke rækker.
- **Tomme linjer betyder noget.** Mangler der en tom linje før en liste
  eller en tabel, bliver den ikke omsat.
