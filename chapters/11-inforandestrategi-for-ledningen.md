# Kapitel 11: Införandestrategi för ledningen

## Varför detta kapitel finns

När målbild, ansvar, säkerhet, robusthet, övergångsarkitektur och finansiering har diskuterats återstår den mest praktiska ledningsfrågan: **hur börjar vi utan att skapa ännu ett stort transformationsprogram som tappar fart?**

Många organisationer försöker införa modern plattformsförmåga genom att antingen gå för snabbt eller för brett. De startar med teknik, utbildar några team, sätter upp en plattform och hoppas att arbetssättet ska förändras av sig självt. Andra gör motsatsen: de väntar på en perfekt målbild, en fullständig styrmodell och en heltäckande arkitektur innan något får prövas i skarp verksamhet.

Båda vägarna innebär risk.

Går organisationen för snabbt kan resultatet bli otydligt ansvar, osäkra undantag, svag driftbarhet och frustration hos både utveckling och drift. Går organisationen för långsamt riskerar den att cementera dagens beställningsflöden, tappa förtroende hos utvecklingsteamen och missa det lärande som bara uppstår när nya arbetssätt används på riktigt.

Kapitlets huvudbudskap är: **införandet måste ledas som en kontrollerad förmågeförflyttning, inte som en teknisk utrullning.**

## Lärandemål

Efter kapitlet ska läsaren kunna:

- beskriva varför plattformsinförande behöver ledas stegvis men med tydlig riktning,
- skilja mellan pilot, förmågetrappa och normalisering,
- välja pilotområden som ger verkligt lärande utan att skapa onödig risk,
- formulera mätetal som visar förändrad förmåga, inte bara teknisk aktivitet,
- identifiera ledningsbeslut som krävs innan självservice kan skalas,
- planera hur nya arbetssätt blir normalläge i stället för sidospår.

## Innan vi börjar

Tidigare kapitel har visat att plattformsförmåga består av flera delar:

- teknik som kan bära nya leveransmönster,
- ansvar som gör det tydligt vem som får göra vad,
- säkerhetskrav som byggs in i plattform och pipeline,
- operativa minimikrav som skyddar robusthet och tillgänglighet,
- övergångsarkitektur som gör gammalt och nytt hanterbart,
- finansiering och prioritering som gör förmågan långsiktig.

Det betyder att införandet inte kan reduceras till frågan: “När är plattformen installerad?”

En bättre fråga är: **när har organisationen lärt sig att använda plattformen på ett sätt som förbättrar leveransförmågan utan att tappa styrbarhet?**

I det här kapitlet använder vi tre huvudbegrepp:

- **pilot**,
- **förmågetrappa**,
- **normalisering**.

## Tre huvudbegrepp

### Pilot

En **pilot** är ett avgränsat införandesteg där organisationen prövar teknik, arbetssätt, ansvar och styrning i en verklig men kontrollerad situation.

En pilot är inte bara ett tekniskt test. Den ska ge svar på frågor som:

- Fungerar ansvarsfördelningen i praktiken?
- Förstår utvecklingsteamet vilka ramar som gäller?
- Är driftbarhetskraven tydliga nog?
- Kan säkerhetskraven kontrolleras utan manuell flaskhals?
- Vet ledningen vilka undantag som kräver beslut?
- Uppstår nya beroenden till gamla plattformar?
- Skapar plattformen faktisk nytta, eller bara ny komplexitet?

En svag pilot bevisar att något går att köra. En stark pilot visar vad organisationen behöver förändra för att arbetssättet ska kunna bli normalt.

### Förmågetrappa

En **förmågetrappa** är en stegvis plan för hur organisationen ökar sin plattformsförmåga över tid.

Den beskriver inte bara fler tekniska funktioner. Den beskriver även hur ansvar, självservice, automatisering, säkerhet, driftbarhet och finansiering mognar tillsammans.

En enkel förmågetrappa kan se ut så här:

1. **Grundläggande plattform på plats**  
   Plattformen kan användas av ett fåtal team med nära stöd.

2. **Kontrollerad pilotdrift**  
   Utvalda team använder standardiserade mallar, begränsad självservice och tydliga operativa krav.

3. **Utökad självservice**  
   Fler team får göra mer själva inom godkända ramar.

4. **Normaliserad plattformsleverans**  
   Plattformen är en etablerad intern produkt med roadmap, support, uppföljning och tydlig finansiering.

5. **Kontinuerlig förbättring**  
   Organisationen förbättrar löpande standarder, automatisering, säkerhetskontroller och användarupplevelse.

Poängen med en förmågetrappa är att ledningen kan se vilka beslut som hör hemma på varje nivå. Allt behöver inte vara färdigt från början, men varje steg måste vara medvetet.

### Normalisering

**Normalisering** betyder att ett nytt arbetssätt slutar vara experiment, undantag eller projekt och blir en del av organisationens ordinarie sätt att leverera.

Det är här många transformationsinitiativ misslyckas. De skapar en fungerande pilot men lyckas inte göra arbetssättet till normalläge. Då uppstår två världar:

- en ny värld där några team får arbeta modernt,
- en gammal värld där majoriteten fortsätter i beställningsflöden,
- och en ledning som inte riktigt vet vilken modell som gäller.

Normalisering kräver beslut om ansvar, finansiering, support, kompetens, riskhantering, arkitekturprinciper, undantag och avveckling av gamla arbetssätt.

Det räcker inte att säga: “Nu finns plattformen.” Ledningen måste också säga: **så här ska organisationen börja använda den som normalt leveranssätt för rätt typ av behov.**

## Scenario: Myndigheten för Samhällstjänst ska gå från ambition till införande

Myndigheten för Samhällstjänst har nu en beslutad riktning. Ledningen vill skapa bättre agil förmåga genom en containerplattform och en mer produktorienterad plattformsmodell.

Men när frågan går från strategi till införande blir skillnaderna mellan funktionerna tydliga igen.

Utvecklingscheferna vill snabbt välja några team som får börja använda plattformen. De vill visa effekt, korta ledtider och minska beroendet av manuella miljöbeställningar.

Driftcheferna vill först veta hur incidenter, övervakning, kapacitet, patchning, backup, loggning och ansvar utanför kontorstid ska fungera. De är inte emot plattformen, men vill inte ärva oklara lösningar.

Säkerhetschefen vill säkerställa att krav inte bara dokumenteras utan faktiskt kontrolleras. Riktlinjer räcker inte om teamen får större frihet.

Ekonomiansvariga vill veta vad satsningen kostar, vilka kostnader som flyttas från dagens plattformar och när någon nytta kan förväntas.

Ledningen märker att alla har rätt, men att ingen ensam funktion kan lösa helheten.

Det är här införandestrategin behövs. Den måste hålla ihop fyra perspektiv samtidigt:

- skapa lärande genom verklig användning,
- skydda produktion och samhällsviktig leverans,
- bygga förtroende mellan funktioner,
- göra det tydligt när nästa steg får tas.

## Vanliga fel i införandet

### Fel 1: att välja pilot efter entusiasm i stället för lärvärde

Det är lockande att välja det mest entusiastiska utvecklingsteamet som första pilot. Det kan vara klokt om teamet har rätt förutsättningar. Men entusiasm räcker inte.

En pilot bör väljas för att den ger relevant lärande.

En bra pilot har ofta följande egenskaper:

- tillräckligt verklig för att testa ansvar och kontroller,
- tillräckligt avgränsad för att riskerna ska vara hanterbara,
- tillräckligt viktig för att ledningen ska bry sig,
- tillräckligt representativ för att lärdomarna ska kunna återanvändas,
- tillräckligt bemannad för att inte falla på resursbrist.

En pilot som bara visar att det går att köra en enkel applikation på plattformen ger begränsat ledningsvärde. En pilot som visar hur utveckling, drift, säkerhet och förvaltning samarbetar i en ny modell ger däremot strategiskt lärande.

### Fel 2: att skala innan ramarna är stabila

När den första piloten fungerar uppstår ofta tryck att snabbt släppa in fler team. Det kan vara rätt, men bara om ramarna håller.

Ledningen bör inte skala självservice förrän det finns tydliga svar på frågor som:

- vilka typer av applikationer får använda plattformen just nu?
- vilka krav måste vara uppfyllda innan produktionssättning?
- vilka kontroller är automatiserade och vilka är manuella?
- vem godkänner undantag?
- vem äger plattformens backlog?
- vem ger support till teamen?
- hur följs kostnad, kapacitet och risk upp?
- vilka beslut ligger hos teamen och vilka ligger hos ledningen?

Att skala utan svar på dessa frågor leder sällan till snabbhet. Det leder ofta till ny köbildning, fler undantag och ökad osäkerhet.

### Fel 3: att låta införandet bli ett sidospår

Ett annat vanligt fel är att skapa en modern plattform som bara används av en liten grupp, medan organisationens styrning, finansiering och ansvar fortsätter som tidigare.

Då blir plattformen ett sidospår. Den kan vara tekniskt bra men organisatoriskt svag.

Tecken på sidospår är:

- plattformsteamet finansieras som ett projekt utan långsiktigt ägarskap,
- gamla beställningsflöden finns kvar som huvudmodell,
- säkerhetskrav hanteras olika i olika flöden,
- driftansvar är oklart när tjänster går i produktion,
- ledningen följer upp teknisk leverans men inte förändrad förmåga,
- team får olika svar beroende på vem de frågar.

Normalisering kräver att ledningen successivt flyttar styrning, finansiering och förväntningar från det gamla arbetssättet till det nya.

## En ledningsmodell för införande i fem steg

### Steg 1: Besluta om riktning och principer innan detaljer

Ledningen behöver börja med några tydliga principer. De ska vara tillräckligt konkreta för att styra beslut men inte så detaljerade att de låser införandet.

Exempel på principer:

- Självservice ska öka, men bara inom kontrollerade och spårbara ramar.
- Säkerhetskrav ska i första hand byggas in i plattform och pipeline.
- Driftbarhet är ett inträdeskrav till produktionsnära miljöer.
- Undantag ska vara få, tidsatta och ägda.
- Plattformen ska förvaltas som intern produkt, inte som engångsprojekt.
- Befintliga plattformar ska inte avvecklas genom önsketänkande utan genom beslutade migreringsprinciper.

Principerna gör att organisationen kan fatta många vardagsbeslut utan att varje fråga måste eskaleras.

### Steg 2: Välj pilot med både nytta och riskkontroll

Pilotvalet bör göras gemensamt av utveckling, drift, säkerhet, arkitektur och verksamhetsnära ledning.

En användbar beslutsfråga är:

**Vilken pilot ger mest lärande om den framtida modellen till lägst acceptabel risk?**

Det betyder att piloten varken ska vara trivial eller ohanterligt kritisk.

För Myndigheten för Samhällstjänst kan en första pilot exempelvis vara en tjänst som:

- har verkliga användare men inte är den mest samhällskritiska tjänsten,
- behöver integration med befintlig IBM MQ- eller Oracle-miljö,
- kan dra nytta av automatiserad leverans,
- har ett engagerat utvecklingsteam,
- har tydlig produktägare,
- kan uppfylla operativa minimikrav,
- ger lärande om loggning, övervakning, behörigheter och releaseflöde.

Det viktiga är inte den exakta tekniken. Det viktiga är att piloten testar de målkonflikter som ledningen faktiskt behöver lösa.

### Steg 3: Sätt mätetal som visar förmåga

Många plattformsinitiativ mäter fel saker. De mäter antal kluster, antal migrerade applikationer eller antal team som fått åtkomst. Det kan vara relevant, men det visar inte automatiskt bättre agil förmåga.

Ledningen bör komplettera aktivitetsmått med förmågemått.

Exempel på förmågemått:

| Område | Fråga att mäta |
|---|---|
| Ledtid | Hur lång tid tar det från godkänt behov till användbar miljö eller tjänst? |
| Självservice | Vilka standardåtgärder kan team utföra själva utan manuell handpåläggning? |
| Kvalitet | Hur ofta behöver beställningar eller leveranser kompletteras på grund av otydlighet? |
| Säkerhet | Vilka krav kontrolleras automatiskt och med vilken täckning? |
| Driftbarhet | Hur många tjänster uppfyller operativa minimikrav före produktionssättning? |
| Robusthet | Hur snabbt kan tjänster återställas vid kända feltyper? |
| Ekonomi | Vilken kapacitet används till ny förmåga, support, stabilitet och teknisk skuld? |
| Förtroende | Upplever utveckling, drift och säkerhet att modellen är tydligare än tidigare? |

Mätetalen ska inte användas för att skapa skuld. De ska användas för att se om införandet faktiskt förändrar organisationens leveransförmåga.

### Steg 4: Skala genom förmågetrappan, inte genom massanslutning

När de första piloterna fungerar bör ledningen inte fråga: “Hur många team kan vi släppa in nu?”

En bättre fråga är: **vilken förmågenivå är vi redo att erbjuda fler team?**

Det kan innebära att organisationen först skalar en begränsad men stabil tjänst:

- standardiserad utvecklingsmiljö,
- standardiserad pipeline,
- standardiserad applikationsmall,
- standardiserad loggning,
- standardiserad sårbarhetskontroll,
- standardiserad produktionssättningsprocess.

Det är bättre att erbjuda få välfungerande självserviceförmågor än många ofärdiga möjligheter som kräver individuell tolkning.

Ledningen bör också besluta vilka team som får gå före. Prioritering kan baseras på:

- verksamhetsnytta,
- teknisk lämplighet,
- risknivå,
- beroenden till befintliga plattformar,
- teamets förmåga att ta ansvar,
- behov av lärande för organisationen,
- möjlighet att återanvända resultat.

### Steg 5: Normalisera och avveckla gamla mönster

Till sist måste ledningen bestämma när det nya arbetssättet blir normalläge för vissa typer av behov.

Det kan uttryckas som principer:

- Nya tjänster av viss typ ska i första hand prövas mot containerplattformen.
- Undantag från standardflödet kräver motivering och tidsatt beslut.
- Miljöbeställningar som motsvarar standardiserade plattformstjänster ska successivt ersättas av självservice.
- Befintliga system ska bedömas mot migreringsprinciper, inte flyttas slentrianmässigt.
- Plattformens backlog ska vara synlig för berörda chefer och prioriteras utifrån helhetsnytta.

Normalisering handlar inte om att allt ska flyttas. Det handlar om att organisationen ska sluta behandla det nya arbetssättet som ett experiment när det väl är moget nog att vara standard för rätt typ av behov.

## Beslut som ledningen behöver fatta tidigt

En införandestrategi blir snabbt svag om centrala beslut skjuts upp. Följande beslut behöver normalt fattas tidigt, även om detaljerna kan utvecklas över tid.

### 1. Vilken typ av behov ska plattformen först lösa?

Plattformen bör inte försöka lösa allt samtidigt. Ledningen behöver välja första användningsområde.

Exempel:

- nya egenutvecklade tjänster,
- modernisering av vissa befintliga applikationer,
- interna stödtjänster,
- API-nära tjänster,
- batch- eller integrationsnära komponenter,
- utvecklings- och testmiljöer före produktionsmiljöer.

Valet påverkar säkerhetskrav, driftkrav, kompetensbehov och integrationsmönster.

### 2. Vilka risknivåer är accepterade i första steget?

Alla tjänster har inte samma risk. Ledningen bör definiera vilka riskklasser eller tjänstetyper som är lämpliga för första fasen.

Det är ofta klokt att börja där organisationen får verkligt lärande men inte maximal konsekvens vid fel.

### 3. Vad krävs för produktionssättning?

Produktionssättning ska inte bygga på personberoende bedömningar. Det bör finnas en tydlig miniminivå.

Exempel på krav:

- ansvarig produktägare,
- definierad supportmodell,
- loggning och övervakning,
- backup- eller återställningsstrategi där det behövs,
- säkerhetskontroller i pipeline,
- dokumenterad beroendebild,
- tydlig incidentväg,
- kapacitetsbedömning,
- spårbar konfiguration.

Kraven behöver vara tillräckligt tydliga för att teamen ska kunna planera mot dem.

### 4. Vem äger undantagen?

Undantag kommer att uppstå. Det viktiga är att de inte blir osynliga.

Ledningen bör besluta:

- vem som får bevilja undantag,
- hur länge de gäller,
- hur risk dokumenteras,
- vem som äger åtgärden,
- när undantaget ska omprövas.

Undantag utan ägare blir snabbt ny teknisk och organisatorisk skuld.

### 5. Hur finansieras plattformen under övergången?

Under en period kommer organisationen bära både gammalt och nytt. Det måste vara ett medvetet beslut.

Om finansieringen bygger på att den nya plattformen omedelbart ska ersätta gamla kostnader uppstår ofta besvikelse. Övergången kräver extra kapacitet för lärande, automatisering, support, migration och parallell drift.

## Ledningens införandekanvas

Ett praktiskt sätt att starta är att fylla i en enkel införandekanvas. Den kan användas i ledningsgruppen eller i ett gemensamt forum för utveckling, drift, säkerhet, arkitektur och verksamhet.

| Fråga | Ledningens svar |
|---|---|
| Varför inför vi plattformsförmågan? |  |
| Vilka problem i dagens beställningsflöde ska minska först? |  |
| Vilken typ av tjänster eller team ingår i första steget? |  |
| Vilka risker accepterar vi inte? |  |
| Vilka kontroller måste vara inbyggda från början? |  |
| Vilka operativa minimikrav gäller för första produktionssättning? |  |
| Vilket pilotområde ger mest relevant lärande? |  |
| Vilka beslut får piloten fatta själv? |  |
| Vilka beslut måste eskaleras? |  |
| Hur mäter vi förbättrad förmåga? |  |
| När får fler team anslutas? |  |
| Vad ska normaliseras efter piloten? |  |
| Vilka gamla arbetssätt ska minska eller avvecklas? |  |

Kanvasen är inte ett dokument för dokumentationens skull. Den är ett sätt att tvinga fram de beslut som annars ofta blir underförstådda.

## Ledningsrekommendationer

### Rekommendation 1: börja med ett verkligt problem, inte med plattformens funktioner

Införandet bör utgå från ett problem som ledningen vill lösa. Exempel:

- för långa ledtider för miljöer,
- för många felaktiga beställningar,
- för mycket manuell koordinering,
- för otydliga säkerhetskrav,
- för svår produktionssättning,
- för låg spårbarhet,
- för mycket beroende av enskilda experter.

När problemet är tydligt blir det lättare att avgöra om plattformen faktiskt skapar nytta.

### Rekommendation 2: låt piloten pröva hela operativa modellen

En pilot som bara testar teknik ger för lite ledningslärande. Piloten bör pröva:

- ansvar,
- självservice,
- säkerhetskontroller,
- driftbarhet,
- support,
- incidentväg,
- kostnadsuppföljning,
- undantag,
- prioritering,
- relationen till befintliga plattformar.

Det betyder inte att allt måste vara perfekt. Men det måste vara synligt.

### Rekommendation 3: bygg förtroende genom tydliga gränser

Utvecklingsteam får större frihet när ramarna är tydliga. Drift och säkerhet får större trygghet när kraven är inbyggda och spårbara. Ledningen får bättre styrning när undantag, risker och kapacitet är synliga.

Förtroende skapas inte genom löften om att “alla ska samarbeta bättre”. Det skapas genom tydliga gränser, fungerande återkoppling och gemensamma beslut.

### Rekommendation 4: skapa en rytm för lärande

Införandet bör ha en återkommande ledningsrytm. Exempelvis:

- månadsvis uppföljning av pilotens lärdomar,
- kvartalsvis prioritering av plattformsbacklog,
- regelbunden genomgång av undantag och risker,
- återkommande beslut om vilka självserviceförmågor som får skalas,
- tydlig uppföljning av gamla flöden som ska minska.

Rytmen gör att införandet inte försvinner in i teknikorganisationen eller fastnar i projektstyrning.

### Rekommendation 5: säg nej tydligare

En viktig ledningsuppgift är att säga nej till fel expansion.

Det kan vara nej till att ansluta ett team som inte kan ta ansvar ännu. Nej till produktionssättning utan operativa minimikrav. Nej till undantag utan ägare. Nej till att bygga speciallösningar som förstör plattformens standardisering. Nej till att kalla något självservice när det egentligen är manuell handpåläggning bakom kulisserna.

Ett tydligt nej skyddar förmågan. Otydliga ja skapar ofta framtida köer.

## Vanliga misstag

### Misstag: införandet drivs som teknikprojekt

**Varför det händer:**  
Det är lättare att planera teknikleveranser än organisationsförmåga. Kluster, pipelines och verktyg känns konkreta.

**Hur man undviker det:**  
Koppla varje teknisk leverans till en förmåga: kortare ledtid, bättre spårbarhet, minskad manuell hantering, tydligare ansvar eller högre driftbarhet.

### Misstag: piloten får undantag som inte kan skalas

**Varför det händer:**  
Organisationen vill få piloten att lyckas och löser hinder genom specialhantering.

**Hur man undviker det:**  
Skilj mellan tillfälliga pilotundantag och framtida standard. Dokumentera vad som måste normaliseras innan nästa team ansluts.

### Misstag: gamla flöden lämnas orörda

**Varför det händer:**  
Det känns tryggare att lägga till nytt än att förändra befintliga styr- och beställningsmodeller.

**Hur man undviker det:**  
Besluta vilka gamla miljöbeställningar, godkännanden eller manuella kontroller som ska minska när motsvarande plattformstjänst är mogen.

### Misstag: ledningen efterfrågar effekt för tidigt men finansierar lärande för svagt

**Varför det händer:**  
Plattformsförmåga betraktas som investering som snabbt ska ge avkastning, men lärande, support och automatisering underskattas.

**Hur man undviker det:**  
Gör övergångskostnaden explicit. Följ upp både nyttorealisering och kapacitet som krävs för att bygga förmågan.

### Misstag: självservice lanseras utan användarstöd

**Varför det händer:**  
Självservice misstolkas som att team ska klara sig själva.

**Hur man undviker det:**  
Bygg dokumentation, utbildning, support, exempelmallar och återkopplingskanaler som en del av plattformsprodukten.

## Övningar

### Övning 1: välj första pilot

Samla representanter från utveckling, drift, säkerhet, arkitektur och verksamhetsledning. Identifiera tre möjliga pilotområden.

Bedöm varje alternativ utifrån:

- verksamhetsnytta,
- risknivå,
- teknisk lämplighet,
- integrationsbehov,
- teamets mognad,
- möjlighet att testa operativ modell,
- lärvärde för organisationen,
- möjlighet att återanvända resultat.

Avsluta med att välja den pilot som ger bäst balans mellan lärande och riskkontroll.

### Övning 2: skapa en förmågetrappa

Beskriv fem steg från dagens läge till normaliserad plattformsleverans.

För varje steg, ange:

- vilken självservice som finns,
- vilka kontroller som är inbyggda,
- vilka operativa krav som gäller,
- vilka team som får använda förmågan,
- vilka beslut som krävs för nästa steg,
- vilka gamla arbetssätt som kan minska.

### Övning 3: formulera mätetal

Välj fem mätetal som visar om införandet förbättrar organisationens förmåga.

Undvik att bara mäta teknisk aktivitet. Inkludera minst ett mått för:

- ledtid,
- kvalitet,
- säkerhet,
- driftbarhet,
- förtroende eller samarbete.

### Fördjupning: identifiera normaliseringsbeslut

Lista vilka beslut som krävs för att det nya arbetssättet ska bli normalläge för en viss typ av tjänster.

Exempel:

- nya tjänster av viss riskklass ska först prövas mot plattformen,
- vissa miljöbeställningar ska ersättas av självservice,
- vissa säkerhetskontroller ska vara automatiserade,
- undantag ska omprövas efter viss tid,
- plattformens roadmap ska prioriteras i ett gemensamt forum.

## Beslut att fatta

- Vilken pilot ska väljas för att lära organisationen rätt saker utan att skapa orimlig risk?
- Vilka beslut måste fattas före piloten för att den inte ska bli ett lokalt experiment utan organisatoriskt lärande?
- När ska självservice breddas, och vilka bevis krävs innan nästa steg tas?

## Snabb sammanfattning

- Införandet av plattformsförmåga ska ledas som en förmågeförflyttning, inte som en teknisk utrullning.
- En pilot ska ge lärande om ansvar, styrning, säkerhet, driftbarhet och nytta, inte bara visa att tekniken fungerar.
- En förmågetrappa hjälper ledningen att skala stegvis utan att tappa kontroll.
- Normalisering är det steg där nya arbetssätt blir ordinarie sätt att leverera för rätt typ av behov.
- Mätetal bör visa förbättrad förmåga, inte bara teknisk aktivitet.
- Ledningen behöver fatta tidiga beslut om pilotval, risknivå, produktionskrav, undantag och finansiering.
- Gamla arbetssätt måste successivt minska, annars blir plattformen ett sidospår.

## Ledningsfrågor

1. Varför är en pilot som bara testar teknik otillräcklig i en stor reglerad organisation?
2. Vilka egenskaper bör ett bra pilotområde ha?
3. Vad är skillnaden mellan att skala genom massanslutning och att skala genom en förmågetrappa?
4. Vilka mätetal skulle visa att er organisation faktiskt får bättre agil förmåga?
5. Vilka gamla arbetssätt behöver minska när nya självserviceförmågor blir mogna?
6. Vem i er organisation bör äga beslut om undantag under införandet?
7. När skulle ni våga säga att ett nytt plattformsbaserat arbetssätt är normaliserat?

## Nästa steg

Nästa kapitel samlar bokens rekommendationer i en gemensam spelplan för ledningen. Där knyts nuläge, målbild, ansvar, säkerhet, robusthet, greenfieldval, övergångsarkitektur, finansiering och införande ihop till ett praktiskt ramverk för gemensamma beslut.
