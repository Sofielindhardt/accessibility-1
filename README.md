Performance start: 67
Performance før optimering: 92
Performance efter billede optimering: 100



# Opgave 24 – Organisér `.marketing` med Flexbox

De tre servicebokse skal stå under hinanden.

Her kan `.marketing` fungere som endnu en flex-container:

```css
.marketing {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
```

Strukturen bliver:

```text
.marketing
│
├── .services
├── .services
└── .services
```

Her betyder:

```text
flex-direction: column
→ serviceboksene placeres lodret
```

## Lad serviceboksene dele pladsen

I stedet for at give hver serviceboks en fast procenthøjde kan du lade Flexbox fordele den tilgængelige plads:

```css
.services {
  flex: 1;
}
```

Det er mere fleksibelt end eksempelvis:

```css
.services {
  height: 32.2%;
}
```

### Hvorfor?

`flex: 1` betyder i denne sammenhæng, at de tre serviceområder får mulighed for at dele den ledige plads i `.marketing`.

Det gør det lettere at få servicekolonnen til visuelt at flugte med Benefits-kolonnen uden at bruge en "magisk" procentværdi.

---

# Opgave 25 – Brug Flexbox i `aside.benefits`

Benefits-området indeholder flere elementer, der skal organiseres lodret.

Du må gerne tage udgangspunkt i:

```css
aside.benefits {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.4rem;
}
```

Her får du et andet eksempel på Flexbox:

```text
main.content
→ row

.marketing
→ column

aside.benefits
→ column
```

### Det vigtige er ikke at bruge Flexbox overalt

Brug Flexbox, når det løser et konkret layoutproblem.

Du skal kunne forklare:

- hvorfor `main.content` bruger Flexbox
- hvorfor `.marketing` bruger `column`
- hvorfor `.services` bruger `flex: 1`
- hvorfor `aside.benefits` bruger `column`

---

# Opgave 26 – Tilføj ét CSS breakpoint med media query

Desktop-layoutet skal nu tilpasses mindre skærme.

Du behøver kun **ét breakpoint**, hvis det giver et velfungerende layout.

> Du skal ikke tilføje flere breakpoints bare for at have flere.

## Hvad er et breakpoint?

Et breakpoint er det punkt, hvor layoutet har behov for at ændre sig.

Tænk derfor:

```text
Hvornår begynder mit layout at få problemer?
```

og ikke:

```text
Hvor mange breakpoints skal jeg have?
```

---

## Brug `max-width` i denne opgave

Starterprojektet er bygget som et desktop-layout. Derfor bruger vi i denne opgave `max-width` til at tilpasse layoutet til mindre skærme.

### `max-width`

```css
@media (max-width: 768px) {
    ...
}
```

betyder:

```text
Når viewporten er 768 px eller smallere
→ brug reglerne inde i media query'en
```

Du kan tænke det sådan:

```text
Standard CSS
→ desktop / større skærme

max-width
→ tilpasning til mindre skærme
```

Horiseon-starterprojektet er allerede bygget som et desktop-layout, så `max-width` passer naturligt til denne opgave.

---

## Hjælp – sådan kan du starte dit breakpoint

Du må gerne tage udgangspunkt i:

```css
@media (max-width: 768px) {
  main.content {
    flex-direction: column;
  }

  .benefits {
    width: 100%;
  }
}
```

Det betyder, at hovedlayoutet på mindre skærme går fra:

```text
DESKTOP

.marketing | .benefits
```

til:

```text
MINDRE SKÆRM

.marketing
.benefits
```

Du skal herefter undersøge, om du også skal tilpasse:

- headeren
- navigationen
- floats på billeder
- margins
- paddings
- billedstørrelser

### Eksempel på yderligere muligheder

```css
@media (max-width: 768px) {
  .header {
    flex-direction: column;
  }

  .header nav {
    float: none;
    margin-right: 0;
  }

  main.content {
    flex-direction: column;
  }

  .benefits {
    width: 100%;
  }
}
```

> Eksemplet er stilladsering og ikke nødvendigvis hele løsningen. Test din egen side og tilføj kun de regler, der er nødvendige.

---

## Test breakpointet

Brug Chrome DevTools og ændr langsomt viewportens bredde.

Undersøg:

```text
Over breakpointet
→ desktop-layout

Ved breakpointet
→ layoutet skifter

Under breakpointet
→ layoutet skal stadig være læsbart og brugbart
```

Hvis ét breakpoint løser problemerne tilfredsstillende, er det nok.

---

# Opgave 27 – Test navigationen på små skærme

På større skærme har du allerede gjort navigationen vandret og fjernet bullets. Nu skal du undersøge, om den samme løsning fungerer på mindre skærme.

Test navigationen ved blandt andet:

```text
320 px
480 px
```

Kontrollér:

- Kan alle links læses?
- Bliver links klippet?
- Overlapper de logoet?
- Er der passende afstand mellem links?
- Kan de fortsat bruges med tastatur?

Overvej om:

```css
flex-wrap
```

eller ændring af `flex-direction` kan være relevant.

---

# Opgave 28 – Sammenlign med referencebilledet og gennemfør afsluttende responsive test

## Sammenlign med referencebilledet

Sammenlign dit resultat med referencebilledet.

Vurder:

- overordnet placering
- indbyrdes afstand
- størrelsesforhold
- læsbarhed
- desktop-layout
- mobile-layout

Du skal **ikke** nødvendigvis lave en pixel-perfekt kopi.

Du skal kunne forklare dine layoutvalg.

---

## Test flere viewport-størrelser

Test mindst:

```text
320 px
480 px
768 px
1024 px
1440 px
```

Kontrollér:

- ingen unødvendig vandret scrolling
- ingen overlappende indhold
- navigationen fungerer
- teksten er læsbar
- billederne passer til containeren
- Benefits fungerer både desktop og mobil
- keyboard focus er stadig synligt

Test også ved:

```text
200 % zoom
```

---

# Opgave 29 – Afsluttende Lighthouse-test

Kør til sidst Lighthouse igen.

Registrér:

| Måling        | Før | Efter |
| ------------- | --: | ----: |
| Accessibility |     |       |
| Performance   |     |       |

### Målsætning

```text
Accessibility: 100
Performance: 90 eller højere
```

Responsive webdesign vurderes manuelt med Device Toolbar og zoom-test.

---

# Dokumentér dine resultater

Besvar kort:

1. Hvad var Accessibility-score før og efter?
2. Hvilke accessibility-problemer fandt Lighthouse?
3. Hvilke accessibility-problemer krævede manuel kontrol?
4. Hvilke semantiske HTML-ændringer foretog du?
5. Hvilke CSS-regler blev overflødige efter HTML-ændringerne?
6. Hvad var Performance-score før og efter?
7. Hvilke billeder optimerede du?
8. Hvor meget blev filstørrelserne reduceret?
9. Hvilke elementer gjorde du til flex-containere?
10. Hvilke gamle floats kunne fjernes?
11. Hvilket breakpoint valgte du, og hvorfor valgte du netop dette?
12. Hvordan ændrer layoutet sig på en mobil skærm?
13. Hvad sker der ved 200 % zoom?

---

# Kontrol af din løsning

## DEL 1 – Web Accessibility

- [ ] Accessibility-baseline er dokumenteret.
- [ ] `<title>` er beskrivende.
- [ ] `<meta name="viewport">` er tilføjet.
- [ ] Semantisk HTML er anvendt.
- [ ] Rene layout-wrappers bruger et passende neutralt element, fx `<div>`.
- [ ] Eksisterende CSS-selectors er kontrolleret og tilpasset efter semantiske HTML-ændringer.
- [ ] Navigationen bruger et passende semantisk HTML-element.
- [ ] Navigationen vises uden bullets og med horisontale menupunkter på større skærme.
- [ ] Dokumentstrukturen er logisk.
- [ ] Headingstrukturen er logisk.
- [ ] Informative billeder har relevante `alt`-tekster.
- [ ] Dekorative billeder bruger `alt=""`.
- [ ] Anchor-links fungerer.
- [ ] Horiseon-logoet fungerer som link til `index.html`.
- [ ] Links kan identificeres.
- [ ] Farvekontrast er kontrolleret.
- [ ] Tastaturtest er gennemført.
- [ ] Keyboard-fokus er tydeligt.
- [ ] Siden er testet ved 200 % zoom.
- [ ] Faste højder er vurderet.
- [ ] CSS er ryddet op.
- [ ] HTML er valideret.
- [ ] Lighthouse Accessibility er kørt igen.
- [ ] Accessibility-score er 100.

## DEL 2 – Web Performance

- [ ] Performance-baseline er dokumenteret.
- [ ] Billeddimensioner er undersøgt.
- [ ] Filstørrelser er undersøgt.
- [ ] Relevante billeder er konverteret til WebP.
- [ ] HTML-referencer er opdateret.
- [ ] Hero-billedets CSS-reference er kontrolleret.
- [ ] Billedkvalitet er vurderet.
- [ ] Network-panelet er anvendt til kontrol.
- [ ] Lighthouse Performance er kørt igen.
- [ ] Performance-score er 90 eller højere.

## DEL 3 – Responsive Webdesign

- [ ] Layoutet er analyseret i Device Toolbar.
- [ ] Headeren anvender et passende Flexbox-layout.
- [ ] Hovedindholdet anvender et passende Flexbox-layout.
- [ ] Overflødige floats er fjernet.
- [ ] Billeder er responsive.
- [ ] Problematiske faste størrelser er vurderet.
- [ ] Der er tilføjet ét relevant CSS breakpoint med en media query (flere er tilladt, hvis de faktisk er nødvendige).
- [ ] Navigationen fungerer på små skærme.
- [ ] Siden er testet ved 320 px.
- [ ] Siden er testet ved 480 px.
- [ ] Siden er testet ved 768 px.
- [ ] Siden er testet ved 1024 px.
- [ ] Siden er testet ved 1440 px.
- [ ] Der er ingen unødvendig vandret scrolling.
- [ ] Siden fungerer ved 200 % zoom.
- [ ] Resultatet er sammenlignet med referencebilledet.

---



# Aflevering

Aflever hele projektmappen.

Dokumentér desuden:

```text
Accessibility før / efter
Performance før / efter
Responsive test ved flere viewport-bredder
```

Du skal kunne forklare mindst:

- tre accessibility-forbedringer
- to performance-forbedringer
- to responsive design-valg

