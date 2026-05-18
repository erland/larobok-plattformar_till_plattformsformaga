# Kapitel 7: Robusthet, tillgänglighet och kvalitet i en självservicemodell

## Varför detta kapitel finns

När en organisation går mot mer självservice uppstår ofta en förenklad bild av förändringen:

**Utvecklingsteamen ska kunna göra mer själva.**

Det är sant, men ofullständigt. Självservice i en stor reglerad organisation handlar inte bara om att ge fler människor fler knappar att trycka på. Det handlar om att flytta återkommande arbete från manuella beställningar till standardiserade, spårbara och kvalitetssäkrade flöden. För att det ska fungera behöver driftbarhet, tillgänglighet, robusthet och kvalitet vara inbyggda i det som erbjuds.

Annars skapas en farlig mellanform. Utvecklingsteam får större frihet, men utan gemensamma krav på loggning, övervakning, backup, återställning, kapacitet, incidenthantering, uppföljning och livscykelansvar. Driftorganisationen får då fortfarande ta konsekvenserna i produktion, men med sämre insyn och fler variationer. Säkerhetsteamet får fler avvikelser att hantera. Ledningen får svårare att förstå den samlade risken.

I scenariot **Myndigheten för Samhällstjänst** blir frågan tydlig när utvecklingsteamen vill skapa produktionsnära miljöer snabbare på en OpenShift-liknande plattform. Driftorganisationen är inte emot automatisering, men vill veta att varje ny tjänst uppfyller grundkrav på övervakning, larm, resursgränser, återställning och supportbarhet. Utvecklingsteamen upplever vissa krav som bromsande eftersom de inte alltid är tydligt formulerade eller automatiserade. Ledningen behöver därför besluta vilka operativa kvalitetskrav som ska vara obligatoriska, hur de ska verifieras och vem som får acceptera undantag.

Det här kapitlet visar hur robusthet, tillgänglighet och kvalitet kan bli en del av självservicemodellen i stället för något som kontrolleras sent, manuellt och personberoende.

## Lärandemål

Efter kapitlet ska du kunna:

- förklara varför självservice kräver standardiserade operativa krav,
- beskriva begreppen **driftbarhet**, **robusthet** och **operativa minimikrav**,
- identifiera vilka kvalitetskrav som bör byggas in i plattform, mallar och leveransflöden,
- skilja mellan krav som alltid ska gälla och krav som varierar utifrån tjänstens riskklass,
- formulera ledningsprinciper för produktionstjänster i en självservicemodell.

## Innan vi börjar

I kapitel 6 beskrevs hur säkerhet kan bli inbyggd styrning genom guardrails, policy-as-code och automatiserade kontroller. Samma grundidé gäller för robusthet och kvalitet.

En organisation som vill öka självservice behöver inte välja mellan frihet och ordning. Den behöver definiera vilken ordning som ska vara inbyggd i plattformen och vilka beslut som fortfarande kräver mänsklig bedömning.

Det centrala ledningsskiftet är detta:

> Från “drift kontrollerar kvaliteten när beställningen kommer in” till “plattformen och arbetssättet gör miniminivån på kvalitet svår att missa”.

Det betyder inte att driftorganisationens kompetens blir mindre viktig. Tvärtom. Driftens erfarenhet behöver översättas från personberoende granskning till gemensamma krav, mallar, automatiserade kontroller, standardiserade tjänster och tydliga undantagsprocesser.

## Tre begrepp: driftbarhet, robusthet och operativa minimikrav

### Driftbarhet

**Driftbarhet** betyder att en tjänst är möjlig att förstå, övervaka, felsöka, återställa och förvalta i produktion.

En applikation kan fungera i ett utvecklingstest men ändå vara svår att drifta. Den kanske saknar tydliga loggar. Den kanske inte har hälsokontroller. Den kanske använder resurser på ett oförutsägbart sätt. Den kanske inte går att starta om utan manuell handpåläggning. Den kanske kräver en specifik person för felsökning.

För ledningen är driftbarhet ett strategiskt kvalitetskrav. En tjänst som inte är driftbar skapar framtida sårbarhet, även om den levereras snabbt.

Driftbarhet handlar bland annat om:

- tydliga loggar,
- mätvärden och larm,
- dokumenterade beroenden,
- hälsokontroller,
- resursgränser,
- återstartbarhet,
- spårbar konfiguration,
- känd supportmodell,
- tydlig ägare,
- möjlighet att isolera och felsöka incidenter.

### Robusthet

**Robusthet** betyder att en tjänst tål störningar, fel och förändringar utan att hela leveransen blir instabil.

Robusthet är bredare än tillgänglighet. En tjänst kan vara tillgänglig just nu men ändå inte robust om den är känslig för små ändringar, saknar återställningsförmåga eller faller okontrollerat när ett beroende inte svarar.

I en containerplattform kan robusthet exempelvis handla om att tjänster har rätt resursbegränsningar, kan startas om automatiskt, inte lagrar tillstånd på fel sätt, hanterar tillfälliga fel i beroenden och har en definierad modell för backup och återställning när data berörs.

För ledningen är robusthet ett sätt att minska den samlade produktionsrisken när förändringstakten ökar.

### Operativa minimikrav

**Operativa minimikrav** är de krav som varje tjänst måste uppfylla för att få köras i en viss miljö eller med en viss risknivå.

De ska inte vara en önskelista. De ska vara en tydlig miniminivå som är möjlig att verifiera.

Exempel på operativa minimikrav kan vara:

- tjänsten har utsedd ägare,
- tjänsten har klassning utifrån verksamhetskritikalitet,
- loggning följer gemensam standard,
- larm är kopplade till rätt mottagare,
- hälsokontroller finns,
- beroenden är dokumenterade,
- backup- och återställningskrav är definierade,
- resursgränser är satta,
- förändringar är spårbara,
- driftsättningar kan följas upp,
- incidentväg är känd,
- undantag är tidsbegränsade och godkända.

Det viktiga är att minimikraven inte bara finns i ett dokument. De behöver kopplas till plattformens självserviceflöden.

## Varför robusthet ofta blir otydlig i transformationen

Säkerhetskrav upplevs ofta som tydliga eftersom de är kopplade till policy, regelverk och risk. Drift- och kvalitetskrav kan däremot bli mer underförstådda.

Driftorganisationen vet ofta av erfarenhet vad som brukar gå fel:

- otydliga ägarskap,
- saknade larm,
- otestade återställningar,
- odokumenterade beroenden,
- speciallösningar som bara ett team förstår,
- för svaga kapacitetsbedömningar,
- ändringar som sker utan tillräcklig spårbarhet,
- system som fungerar tills de möter verklig produktionsbelastning.

Problemet är att denna kunskap ofta ligger i människor, möten och historik. Den är inte alltid översatt till tydliga plattformskrav. När organisationen automatiserar utan att först formulera dessa krav riskerar den att automatisera bort synliga flaskhalsar men samtidigt bygga in osynlig produktionsskuld.

**Produktionsskuld** är inte bara gammal teknik. Det är också summan av operativa svagheter som gör tjänster svåra att äga, förstå, övervaka och förändra över tid.

## Självservice kräver olika nivåer av krav

Alla tjänster behöver inte samma krav. En intern experimentmiljö, en testmiljö och en samhällskritisk produktionstjänst ska inte styras på exakt samma sätt.

Däremot behöver organisationen en tydlig modell för vilka krav som gäller på vilken nivå.

En enkel ledningsmodell kan bestå av fyra nivåer:

### Nivå 1: Experiment och lärande

Här ska tröskeln vara låg. Syftet är att lära, testa och utveckla idéer. Kraven bör fokusera på kostnadskontroll, grundläggande säkerhet och att inget misstas för produktion.

Exempel på krav:

- miljön är tydligt märkt som experiment,
- inga känsliga eller produktionsliknande data används utan godkännande,
- resursförbrukning är begränsad,
- miljön har en definierad livslängd,
- teamet ansvarar för avveckling.

### Nivå 2: Utveckling och test

Här behöver team kunna arbeta effektivt, men med mer struktur. Miljöer ska vara reproducerbara och likna senare steg tillräckligt mycket för att problem ska upptäckas tidigt.

Exempel på krav:

- miljö skapas från godkända mallar,
- beroenden är kända,
- grundläggande loggning finns,
- konfiguration är spårbar,
- testdata hanteras enligt regler,
- kostnader och resurser följs upp.

### Nivå 3: Produktionsnära miljö

Här ska tjänsten börja behandlas som något som kan bli produktion. Kraven bör närma sig produktionskrav, särskilt för loggning, larm, återställning och beroenden.

Exempel på krav:

- hälsokontroller finns,
- loggning följer standard,
- övervakning är kopplad till relevant mottagare,
- resursgränser är satta,
- beroenden är dokumenterade,
- återställningskrav är definierade,
- driftsättningsflödet är spårbart.

### Nivå 4: Produktion

Här måste organisationen kunna lita på att tjänsten går att drifta, följa upp och återställa.

Exempel på krav:

- ägarskap och supportmodell är fastställda,
- tillgänglighets- och återställningskrav är beslutade,
- larm har mottagare och åtgärdsinstruktion,
- backup och återställning är testade där det krävs,
- incident- och problemhantering är kopplad till tjänsten,
- kapacitets- och belastningsantaganden är dokumenterade,
- undantag är godkända, tidsbegränsade och synliga.

Poängen är inte att skapa mer byråkrati. Poängen är att göra skillnaden mellan miljötyper tydlig så att organisationen inte överstyr experiment och understyr produktion.

## Vad ledningen måste besluta

Robusthet och kvalitet kan inte helt delegeras till enskilda team. Teamen kan bygga och följa krav, men ledningen måste besluta vilken miniminivå organisationen ska acceptera.

Fem beslut är särskilt viktiga.

### 1. Vilka krav är obligatoriska för produktion?

Ledningen behöver fastställa en gemensam miniminivå. Den ska vara tillräckligt tydlig för att kunna användas i plattformsmallar, pipelines och granskningar.

Exempel:

- ingen produktion utan ägare,
- ingen produktion utan loggning enligt standard,
- ingen produktion utan definierad incidentväg,
- ingen produktion utan klassning av verksamhetskritikalitet,
- ingen produktion utan beslutade återställningskrav när data berörs.

### 2. Vilka krav ska variera med riskklass?

Alla produktionstjänster är inte lika kritiska. En informationssida och en transaktionell samhällstjänst kan inte ha samma krav på tillgänglighet, återställningstid eller support.

Ledningen behöver därför besluta hur tjänster klassas och hur klassningen påverkar kraven.

En enkel modell kan bygga på frågor som:

- Vad händer om tjänsten ligger nere?
- Hur snabbt måste den återställas?
- Vilka användare påverkas?
- Finns legala eller regulatoriska krav?
- Hanteras känslig information?
- Finns beroenden till andra kritiska tjänster?

### 3. Vad ska automatiseras och vad ska granskas manuellt?

Vissa krav lämpar sig väl för automatisering. Andra kräver fortfarande bedömning.

Automatiserbara krav kan exempelvis vara:

- obligatoriska metadata,
- resursgränser,
- godkända mallar,
- hälsokontroller,
- loggformat,
- säkerhetsskanning,
- krav på larmkonfiguration,
- spårbarhet i pipeline.

Manuella bedömningar kan behövas för:

- riskacceptans vid avvikelse,
- bedömning av verksamhetskritikalitet,
- större arkitekturval,
- beroenden till mycket kritiska system,
- undantag från standardmönster,
- produktionssättning av ny typ av tjänst.

En mogen självservicemodell blandar automatiska kontroller och mänskliga beslut. Den försöker inte automatisera bort allt omdöme.

### 4. Vem äger kraven över tid?

Ett vanligt misstag är att minimikrav tas fram som ett införandedokument och sedan blir inaktuella. Då uppstår snart samma problem igen: vissa följer gamla krav, vissa tolkar om dem och vissa skapar egna varianter.

Ledningen behöver utse kravägare för olika områden:

- driftbarhet och incidentförmåga,
- övervakning och loggning,
- säkerhet och behörighet,
- data, backup och återställning,
- kapacitet och prestanda,
- arkitektur och integrationsmönster,
- plattformsmallar och självserviceflöden.

Kravägare behöver inte utföra allt arbete själva, men de måste ansvara för att kraven är begripliga, aktuella och möjliga att följa.

### 5. Hur hanteras undantag?

Undantag kommer att behövas. Det viktiga är att de inte blir ett informellt parallellflöde.

Ett bra undantag ska ha:

- tydlig orsak,
- ansvarig ägare,
- riskbedömning,
- tidsbegränsning,
- kompensatoriska åtgärder,
- beslutande roll,
- plan för att stänga undantaget,
- synlighet för berörda funktioner.

När undantag hanteras öppet kan de bli lärande. När de hanteras informellt blir de produktionsskuld.

## Scenario: Myndigheten för Samhällstjänst inför produktionsnära självservice

På Myndigheten för Samhällstjänst har flera utvecklingsteam börjat använda den nya containerplattformen för test och utveckling. Erfarenheterna är positiva. Miljöer kan skapas snabbare. Teamen kan experimentera mer. Vissa återkommande beställningar har försvunnit.

Nu vill några team gå vidare och använda plattformen för produktionsnära miljöer.

Utvecklingschefen säger:

> “Vi kan inte behöva gå tillbaka till gamla beställningsflöden så fort något närmar sig produktion. Då tappar vi hela poängen.”

Driftchefen svarar:

> “Vi säger inte nej till självservice. Men vi behöver veta att det som skapas går att övervaka, felsöka och återställa. Annars blir det vi som står med ansvaret när något händer.”

Säkerhetschefen lägger till:

> “Säkerhetskraven börjar komma på plats, men vi behöver också se hur tillgänglighet, loggning och incidenthantering hänger ihop med plattformen.”

Ledningen inser att frågan inte är om teamen ska få självservice. Frågan är vilken **produktionsnivå** självservicen ska stödja.

De beslutar att skapa tre saker:

1. en katalog över operativa minimikrav,
2. en klassningsmodell för tjänster och miljöer,
3. ett beslutsforum för undantag och nya standardmönster.

Plattformsteamet får i uppdrag att tillsammans med drift, säkerhet och representanter från utvecklingsteamen översätta kraven till mallar och kontroller. Målet är att ett team som väljer “produktionsnära tjänst” i plattformens självserviceflöde automatiskt ska få med rätt grundkrav: loggning, hälsokontroller, resursgränser, metadata, larmkoppling och dokumenterade beroenden.

Det löser inte allt. Men det förändrar samtalet. I stället för att varje miljöbeställning blir en förhandling om vad som krävs, blir minimikraven en gemensam produktionsstandard.

## Vanliga misstag

### Misstag 1: Att tro att containerplattformen automatiskt ger robusthet

**Varför det händer:**  
Plattformen har inbyggda tekniska förmågor som schemaläggning, återstart och resurshantering. Det kan skapa bilden av att robusthet kommer av sig själv.

**Hur man undviker det:**  
Skilj på plattformens tekniska möjligheter och organisationens operativa krav. Plattformen kan stödja robusthet, men den ersätter inte beslut om ägarskap, övervakning, återställning och incidentansvar.

### Misstag 2: Att kopiera gamla driftkrav utan att förenkla dem

**Varför det händer:**  
Driftorganisationen vill skydda produktionen och utgår från befintliga checklistor. De kan vara byggda för en äldre beställningsmodell.

**Hur man undviker det:**  
Översätt driftkraven till minimikrav, mallar och automatiserade kontroller. Ta bort krav som inte längre fyller en tydlig funktion och behåll krav som skyddar verklig produktion.

### Misstag 3: Att behandla alla tjänster som lika kritiska

**Varför det händer:**  
Det känns enklare och rättvist att ha samma krav för allt.

**Hur man undviker det:**  
Inför risk- och verksamhetsklassning. Låt kravnivån bero på tjänstens betydelse, data, beroenden och återställningsbehov.

### Misstag 4: Att skapa självservice utan tydlig supportmodell

**Varför det händer:**  
Organisationen fokuserar på att göra det lätt att skapa miljöer, men glömmer vem som hjälper till när något inte fungerar.

**Hur man undviker det:**  
Definiera supportansvar för plattform, applikation, beroenden och gemensamma tjänster. Självservice betyder inte “ingen support”. Det betyder att vanliga åtgärder är standardiserade och att ansvar är tydligt.

### Misstag 5: Att låta undantag bli permanenta

**Varför det händer:**  
Ett team har bråttom, ett beroende är svårt eller en standard passar inte. Undantaget godkänns för att komma vidare, men följs aldrig upp.

**Hur man undviker det:**  
Gör undantag tidsbegränsade, synliga och ägda. Följ upp återkommande undantag som signaler om att standarden behöver förbättras.

## Ledningsverktyg: operativ miniminivå för självservice

Ett praktiskt sätt att börja är att låta ledningen besluta om en gemensam miniminivå för produktionsnära självservice.

Använd följande frågor i ledningsgruppen:

1. Vilka krav måste alltid vara uppfyllda innan en tjänst får köras produktionsnära?
2. Vilka krav ska variera beroende på tjänstens kritikalitet?
3. Vilka kontroller kan byggas in i plattform och pipeline?
4. Vilka kontroller kräver fortfarande mänsklig bedömning?
5. Vem äger varje kravområde över tid?
6. Hur synliggör vi undantag?
7. Hur vet vi att kraven faktiskt förbättrar leveransförmågan och inte bara skapar mer administration?

En möjlig miniminivå kan uttryckas som principer:

- Varje tjänst ska ha en ägare.
- Varje tjänst ska ha en tydlig miljötyp.
- Varje produktionsnära tjänst ska ha loggning och övervakning enligt standard.
- Varje tjänst med data ska ha beslutade krav på backup och återställning.
- Varje produktionssatt tjänst ska ha definierad incidentväg.
- Varje undantag ska vara synligt, tidsbegränsat och ägt.
- Varje standardkrav ska ha en ansvarig kravägare.

Detta är inte en komplett kravkatalog. Det är en ledningsmässig startpunkt.

## Rekommendationer till ledningen

1. **Gör driftbarhet till ett ledningskrav, inte en sen teknisk kontroll.**  
   Om tjänster inte går att övervaka, felsöka eller återställa har organisationen inte byggt verklig agil förmåga.

2. **Skapa en gemensam modell för miljö- och tjänsteklassning.**  
   Självservice behöver olika krav för experiment, test, produktionsnära miljö och produktion.

3. **Översätt driftens erfarenhet till plattformens standarder.**  
   Den tysta kunskap som finns i driftorganisationen behöver bli mallar, kontroller och tydliga minimikrav.

4. **Automatisera det som är entydigt.**  
   Krav på metadata, resursgränser, loggning, hälsokontroller och spårbarhet bör så långt möjligt byggas in i plattform och pipeline.

5. **Behåll mänskliga beslut där omdöme behövs.**  
   Riskklassning, större undantag och nya driftmönster bör inte döljas i automatisering.

6. **Mät om självservice förbättrar helheten.**  
   Följ inte bara antal skapade miljöer. Följ även incidenter, återkommande undantag, återställningsförmåga, ledtid till produktion och upplevd tydlighet hos teamen.

## Övningar

### Övning 1: Identifiera era dolda driftkrav

Samla representanter från drift, utveckling, säkerhet och arkitektur. Be varje grupp svara på frågan:

> Vilka krav förväntar vi oss att en produktionstjänst uppfyller, även om de inte alltid står tydligt i beställningen?

Sortera svaren i fem kategorier:

- ägarskap,
- övervakning och loggning,
- återställning och kontinuitet,
- kapacitet och resurser,
- incident och support.

Markera sedan vilka krav som redan är automatiserade, vilka som är manuella och vilka som är otydliga.

### Övning 2: Skapa tre kravnivåer

Välj en verklig eller fiktiv tjänst. Definiera krav för:

1. utveckling/test,
2. produktionsnära miljö,
3. produktion.

Beskriv vad som skiljer nivåerna åt. Undvik att göra produktionskraven till en allmän önskelista. Fokusera på det som är nödvändigt för att tjänsten ska kunna ägas och drivas.

### Fördjupning: Undantagsanalys

Gå igenom fem aktuella eller historiska undantag från drift- eller kvalitetskrav.

För varje undantag:

- Varför behövdes det?
- Vem godkände det?
- Var det tidsbegränsat?
- Finns det kvar?
- Borde standarden ändras, eller borde undantaget stängas?

Syftet är att se om undantag används som lärande eller som permanent genväg.

## Beslut att fatta

- Vilka driftbarhetskrav är obligatoriska innan ett team får använda självservice i produktionsnära miljöer?
- Vilka krav på övervakning, loggning, backup, återställning och incidenthantering ska vara standard?
- Vilken lägstanivå för robusthet ska plattformen garantera, och vad ligger fortfarande på applikationsteamen?

## Snabb sammanfattning

- Självservice fungerar bara om driftbarhet, robusthet och kvalitet är inbyggda i modellen.
- Driftbarhet betyder att en tjänst går att förstå, övervaka, felsöka, återställa och förvalta.
- Robusthet betyder att tjänsten tål störningar och förändringar utan att helheten blir instabil.
- Operativa minimikrav gör det tydligt vad som alltid måste gälla för produktionsnära miljöer och produktion.
- Alla tjänster behöver inte samma krav, men organisationen behöver en gemensam klassningsmodell.
- Ledningen måste besluta vilka krav som är obligatoriska, vilka som beror på riskklass och hur undantag hanteras.
- Driftorganisationens erfarenhet bör översättas till plattformsmallar, kontroller och självserviceflöden.

## Kontrollfrågor

1. Vad är skillnaden mellan att en tjänst fungerar och att den är driftbar?
2. Varför räcker det inte att containerplattformen har tekniska funktioner för återstart och resurshantering?
3. Vilka operativa minimikrav bör gälla för en produktionsnära tjänst i er organisation?
4. Vilka krav kan ni automatisera i plattform eller pipeline?
5. Vilka krav kräver fortfarande mänsklig bedömning?
6. Hur hanterar ni undantag i dag, och hur synliga är de för ledningen?
7. Vilka gamla driftkrav bör förenklas innan de förs in i en självservicemodell?

## Nästa steg

I nästa kapitel behandlas ett av bokens viktigaste strategiska vägval: **greenfield eller förändring i befintlig organisation**.

När kraven på säkerhet, robusthet, tillgänglighet och kvalitet blir tydligare kan ledningen bättre bedöma om organisationen bör skapa en separat ny lösning, förändra befintliga strukturer stegvis eller kombinera båda vägarna. Kapitel 8 visar hur detta vägval kan göras mer medvetet och mindre ideologiskt.
