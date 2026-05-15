# Övningar till kapitel 7: Robusthet, tillgänglighet och kvalitet i en självservicemodell

## Övning 1: Identifiera dolda driftkrav

Syfte: Synliggöra krav som organisationen redan förväntar sig men som inte alltid är tydligt formulerade.

1. Lista krav som brukar komma upp sent i beställningar, granskningar eller produktionssättningar.
2. Sortera dem under:
   - ägarskap,
   - övervakning och loggning,
   - återställning och kontinuitet,
   - kapacitet och resurser,
   - incident och support.
3. Markera varje krav som:
   - tydligt och dokumenterat,
   - känt men informellt,
   - oklart eller personberoende.
4. Välj tre krav som bör bli operativa minimikrav.

## Övning 2: Klassificera tre tjänster

Välj tre tjänster med olika kritikalitet.

För varje tjänst, besvara:

- Vad händer om tjänsten ligger nere i en timme?
- Vad händer om tjänsten ligger nere en arbetsdag?
- Hanterar tjänsten känsliga data?
- Vilka andra system är beroende av tjänsten?
- Vilka krav behövs på loggning, övervakning, backup och återställning?

Avsluta med att föreslå kravnivå: låg, medel eller hög.

## Övning 3: Självservice utan produktionsskuld

Välj ett självserviceflöde som skulle kunna införas, exempelvis skapande av produktionsnära miljö.

Beskriv:

- vilka val teamet ska kunna göra själv,
- vilka krav som ska vara automatiskt inbyggda,
- vilka beslut som kräver godkännande,
- vilken information som ska vara synlig för drift och säkerhet,
- hur undantag ska hanteras.

## Reflektionsfrågor för ledningsgruppen

1. Vilka delar av vår robusthet bygger i dag på personberoende kunskap?
2. Var uppstår flest oklarheter mellan utveckling och drift inför produktionssättning?
3. Vilka krav är så viktiga att de alltid ska vara inbyggda i plattformens standardflöden?
4. Vilka krav riskerar att bli onödig byråkrati om de tillämpas lika på alla tjänster?
5. Hur vet vi att självservice förbättrar helheten och inte bara flyttar arbete mellan funktioner?

## Beslutsunderlag

Fyll i tabellen som underlag för nästa ledningsdiskussion.

| Område | Nuvarande problem | Föreslaget minimikrav | Automatiseras? | Kravägare |
|---|---|---|---|---|
| Ägarskap |  |  |  |  |
| Loggning |  |  |  |  |
| Övervakning |  |  |  |  |
| Backup/återställning |  |  |  |  |
| Incidentväg |  |  |  |  |
| Resursgränser |  |  |  |  |
| Undantag |  |  |  |  |
