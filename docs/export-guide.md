# Exportguide

## Grundregel
Exporter ska utgå från `docs/export-metadata.yaml` och kapitelordningen där.

## EPUB
- Använd metadata för titel, undertitel, författare, språk och identifierare.
- Lägg inte in en innehållsförteckning som eget textkapitel.
- Använd luftig CSS för rubriker, brödtext, listor, tabeller och kodblock.
- Rendera markdown som riktig formatering.

## PDF
- PDF ska ha en genererad innehållsförteckning före inledningen.
- Rubriker, listor, tabeller och kodblock ska renderas som formaterad text.
- Använd metadata för dokumenttitel och författare där det är praktiskt möjligt.

## DOCX
- Markdown ska renderas till Word-stilar, inte kopieras rått.

## Kontroll före export
- Kontrollera att författare är ifylld.
- Kontrollera att kapitelordningen i metadata stämmer.
- Kontrollera att alla refererade bilder finns.
- Om `assets/cover/cover.png` saknas ska exportören antingen skapa omslag först eller exportera utan omslag efter uttryckligt beslut.
