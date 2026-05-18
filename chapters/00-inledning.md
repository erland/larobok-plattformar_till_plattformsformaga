# Inledning: varför den här boken behövs

Stora reglerade organisationer står ofta inför en besvärlig dubbelrörelse. De behöver leverera snabbare, förändra oftare och ge utvecklingsteam mer handlingsutrymme. Samtidigt får de inte tappa kontrollen över säkerhet, kvalitet, tillgänglighet, robusthet, spårbarhet och kostnader.

Det är lätt att beskriva detta som en teknisk fråga. En containerplattform ska införas. Kanske nämns OpenShift, Kubernetes, automatiserade pipelines, självservice, standardiserade mallar och moderna arbetssätt. Men om ledningen behandlar plattformen som enbart ny teknik kommer organisationen ofta att få ett gammalt arbetssätt med ett nytt tekniskt skal.

Den här boken utgår från en annan tanke: containerplattformen är inte huvudpersonen. Den är en katalysator. Den gör det tydligt vilka beslut organisationen inte längre kan skjuta framför sig.

## Bokens huvudmodell: från teknik till förmåga

Bokens centrala modell är enkel, men viktig:

1. **Plattform som teknik** – exempelvis containerplattform, CI/CD, nätverk, lagring, loggning och säkerhetskomponenter.
2. **Plattformstjänst** – ett avgränsat erbjudande som användare kan nyttja, till exempel en standardiserad applikationsyta, en pipeline, en loggningstjänst eller en databaskoppling.
3. **Plattformsprodukt** – en styrd intern produkt med ägare, målgrupp, backlog, supportmodell, finansiering, livscykel och tydliga kvalitetskrav.
4. **Plattformsförmåga** – organisationens samlade förmåga att använda plattformar för snabbare, säkrare och mer robust leverans.

Förflyttningen i boken går alltså inte från “gammal teknik” till “ny teknik”. Den går från att se plattformar som komponenter till att bygga en organisatorisk förmåga där utveckling, drift, säkerhet, arkitektur och ledning arbetar med samma spelplan.

Det är först när alla fyra nivåerna hänger ihop som containerplattformen kan ge verklig effekt. Teknik utan tjänster blir svår att använda. Tjänster utan produktansvar blir svåra att utveckla. Produkter utan organisatorisk förmåga blir isolerade initiativ. Plattformsförmåga uppstår när teknik, ansvar, styrning, finansiering, säkerhet och vardagligt arbetssätt stödjer varandra.


## Vem boken är för

Boken är skriven för chefer och ledare i stora reglerade organisationer. Den riktar sig särskilt till dig som har ansvar för produktion, utveckling, säkerhet, arkitektur, förvaltning eller plattform.

Du behöver inte vara expert på containerteknik. Däremot behöver du vara beredd att se hur teknikval, styrning, ansvar, finansiering och organisationskultur hänger ihop.

En central utgångspunkt är att många chefer förstår sin egen del av organisationen väl, men har begränsad insyn i andra funktioners vardag. Utveckling ser väntetider och beroenden. Drift ser spretiga beställningar, otydliga krav och risk för instabilitet. Säkerhet ser krav som inte kan väljas bort. Ledningen ser ofta ökande tryck från verksamheten och undrar varför modern teknik inte automatiskt ger snabbare leverans.

Alla kan ha rätt samtidigt.

## Bokens återkommande scenario

För att göra resonemangen konkreta följer boken den fiktiva organisationen **Myndigheten för Samhällstjänst**.

Myndigheten har en stor och komplex IT-miljö. Där finns etablerade plattformar och tekniker som applikationsservrar, meddelandeköer, databaser, sökplattformar och lagringslösningar. Utvecklingsteam kan i vissa fall leverera automatiskt via CI/CD när miljön väl finns på plats. Samtidigt kräver nya eller förändrade miljöer ofta beställningar, koordinering, kvalitetssäkring och manuell hantering.

Säkerhetsteamet styr främst genom riktlinjer. Driftorganisationen tar emot och genomför miljöbeställningar. En driftskoordinerande funktion kvalitetssäkrar större förändringar. Utvecklingsteamen vill automatisera mer och kunna göra mer själva. Alla funktioner försöker förbättra sin egen situation, men helheten blir inte tillräckligt snabb, tydlig eller förutsägbar.

När myndigheten börjar planera för containerteknik blir frågan större än teknik: vilken organisationsförmåga behöver byggas?

## Bokens grundbudskap

Bokens huvudbudskap är att agil förmåga i en reglerad organisation inte uppstår genom att bara ge team mer frihet. Den uppstår när ledningen skapar ett system där frihet, ansvar och kontroll hänger ihop.

Det kräver bland annat:

- tydlig målbild för vad som ska bli snabbare och varför,
- gemensam förståelse för utvecklingens, driftens och säkerhetens olika uppdrag,
- standardiserade plattformstjänster som kan användas utan ny förhandling varje gång,
- inbyggda kontroller snarare än sena manuella granskningar,
- finansiering och ägarskap för plattformsförmågan,
- beslut om när greenfield är rätt väg och när befintlig organisation måste förändras.

## Hur boken ska användas

Boken är inte tänkt att läsas som en teknisk manual. Den är ett besluts- och reflektionsstöd för ledning.

Varje kapitel bygger på en konkret ledningsfråga. Kapitlen beskriver målkonflikter, förklarar centrala begrepp och ger handlingsinriktade rekommendationer. Använd gärna boken i ledningsgrupper, styrgrupper, arkitekturforum, plattformsinitiativ eller gemensamma workshops mellan utveckling, drift och säkerhet.

Du får mest nytta av boken om du hela tiden ställer två frågor:

1. Vad betyder detta i vår organisation?
2. Vilket beslut behöver ledningen fatta, förtydliga eller ompröva?

## Bokens upplägg

De första kapitlen bygger gemensam förståelse för nuläge, målbild och varför en containerplattform är ett strategiskt vägval. Därefter behandlas ansvar, säkerhet, robusthet och kvalitet i en mer självbetjänad modell. Bokens senare delar fokuserar på greenfield kontra förändring i befintlig organisation, övergångsläge, finansiering, införande och ledningens gemensamma spelplan.

Målet är inte att sälja in en viss organisationsmodell. Målet är att ge dig bättre frågor, tydligare beslutspunkter och en mer realistisk bild av vad som krävs för att gå från beställningsflöde till plattformsförmåga.
