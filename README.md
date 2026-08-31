

Besvar kort:

Accessibility før/efter: Før: 67 / Efter: 100
Lighthouse-problemer: For lav kontrast og for små touch targets.
Manuel kontrol: Tastaturnavigation, focus, headings, alt-tekster, links og 200 % zoom.
Semantisk HTML: header, nav, main, section, aside og footer blev indført.
Overflødig CSS: Bl.a. .header h1 og float: right i navigationen.
Performance før/efter: Før: 69 / Efter: 75
Optimerede billeder: Hero-billedet, de tre servicebilleder og de tre benefit-ikoner.
Flex-containere: .header, main.content, .marketing og aside.benefits.
Fjernede floats: Navigationens float: right og billed-floats på små skærme.
Breakpoint: 768px, fordi layoutet begyndte at blive for presset under denne bredde.
Mobil-layout: Navigationen bliver lodret, og marketing + benefits placeres under hinanden.
200 % zoom: Indholdet kan vokse og reflowe uden at blive klippet, bl.a. fordi height: 300px blev ændret til min-height: 300px.

