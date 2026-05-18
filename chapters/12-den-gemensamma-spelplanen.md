# Kapitel 12: Den gemensamma spelplanen

## Varför detta kapitel finns

De tidigare kapitlen har behandlat nuläge, målbild, containerplattform, plattformsprodukter, ledningsansvar, säkerhet, robusthet, greenfield, övergångsarkitektur, finansiering och införandestrategi. Varje område är viktigt, men inget av dem räcker ensamt.

Den stora risken i en reglerad organisation är inte att någon saknar ambition. Tvärtom finns ofta många starka ambitioner samtidigt:

- utveckling vill leverera snabbare och med mindre friktion,
- drift vill skydda stabilitet, kvalitet och förutsägbarhet,
- säkerhet vill minska risk och säkerställa efterlevnad,
- arkitektur vill undvika teknisk splittring och ohanterliga beroenden,
- verksamheten vill få effekt av digitalisering utan att vänta för länge,
- ledningen vill öka förändringsförmågan utan att tappa kontroll.

Problemet uppstår när dessa ambitioner styrs var för sig. Då får organisationen många lokalt rimliga beslut men en svag helhet. Resultatet blir spretiga beställningar, manuella granskningar, otydliga undantag, svårprioriterad plattformsutveckling och återkommande diskussioner om vem som egentligen ansvarar för vad.

Det här kapitlet samlar därför bokens rekommendationer i en **gemensam spelplan**.

En gemensam spelplan är inte en detaljerad projektplan. Den är ett ledningsramverk som gör det tydligt:

- vilken förmåga organisationen försöker bygga,
- vilka principer som ska styra svåra avvägningar,
- vilka beslut som måste fattas gemensamt,
- vilka förmågor som behöver utvecklas över tid,
- hur frihet och kontroll ska balanseras,
- hur organisationen ser skillnad på verklig förflyttning och symbolisk aktivitet.

Kapitlets huvudbudskap är: **agilare leverans i en reglerad organisation kräver inte mindre styrning, utan bättre gemensam styrning.**

## Lärandemål

Efter kapitlet ska läsaren kunna:

- beskriva vad en gemensam spelplan är och varför den behövs,
- skilja mellan gemensam riktning, beslutsramverk och förmågekarta,
- formulera ledningsprinciper för självservice, säkerhet, robusthet och förändringstakt,
- identifiera beslut som behöver tas i ett gemensamt ledningsforum,
- använda en enkel förmågekarta för att bedöma organisationens mognad,
- omsätta bokens rekommendationer till en handlingsdriven ledningsagenda.

## Innan vi börjar

Boken har konsekvent utgått från att organisationen inte har ett enskilt problem. Den har ett samspel mellan flera problem:

- gamla beställningsflöden möter nya krav på automatisering,
- separerade ansvar möter behov av snabbare helhetsleverans,
- riktlinjebaserad säkerhet möter behov av inbyggda kontroller,
- stabil drift möter behov av tätare förändring,
- teknisk plattform möter organisatoriska arbetssätt som inte alltid har förändrats,
- greenfield lockar med fart men riskerar att skapa parallella världar,
- brownfield skapar förankring men riskerar att fastna i arv och kompromisser.

Därför behöver ledningen hålla ihop tre saker samtidigt:

1. **Riktning** – vart organisationen ska.
2. **Beslut** – vilka avvägningar som ska göras och av vem.
3. **Förmåga** – vad organisationen faktiskt kan göra i vardagen.

I det här kapitlet använder vi tre huvudbegrepp:

- **gemensam spelplan**,
- **beslutsramverk**,
- **förmågekarta**.

## Tre huvudbegrepp

### Gemensam spelplan

En **gemensam spelplan** är en överenskommen ledningsmodell för hur organisationen ska utveckla och använda sin plattformsförmåga.

Den svarar på frågor som:

- Varför bygger vi en containerplattform eller modern plattformsförmåga?
- Vilka problem ska den lösa?
- Vilka problem ska den inte lösa?
- Vilka typer av team och tjänster ska omfattas först?
- Vilken frihet ska utvecklingsteam få?
- Vilka krav är icke förhandlingsbara?
- Hur ska säkerhet och driftbarhet byggas in?
- Hur hanteras undantag?
- Hur finansieras och prioriteras plattformen?
- När är ett nytt arbetssätt tillräckligt moget för att bli normalläge?

En gemensam spelplan är inte samma sak som konsensus i varje detalj. I en stor organisation kommer utveckling, drift, säkerhet och verksamhet ibland att vilja olika saker. Spelplanen gör det möjligt att ta konflikterna på rätt nivå, med gemensamma principer, i stället för att låta dem återuppstå i varje beställning, varje release och varje undantagsärende.

### Beslutsramverk

Ett **beslutsramverk** är en praktisk struktur för vilka beslut som ska fattas, vem som ska fatta dem och vilka kriterier som ska användas.

I en organisation som inför plattformsförmåga behövs beslut på flera nivåer:

- strategiska beslut om målbild, finansiering och risk,
- taktiska beslut om prioriteringar, införandevågor och standarder,
- operativa beslut om mallar, behörigheter, krav och support,
- undantagsbeslut när ett team behöver avvika från normalmodellen.

Utan beslutsramverk hamnar fel frågor på fel nivå. Ledningen diskuterar detaljer som borde hanteras av plattformsteamet, medan viktiga risk- och mandatfrågor lämnas till enskilda projekt. Det leder till tröghet och otydlighet.

Ett bra beslutsramverk gör tre saker:

1. Det lyfter principiella avvägningar till rätt ledningsnivå.
2. Det delegerar återkommande vardagsbeslut till rätt funktion.
3. Det gör undantag synliga, spårbara och tidsbegränsade.

### Förmågekarta

En **förmågekarta** är en översikt över vilka organisatoriska förmågor som behövs för att målbilden ska fungera i praktiken.

Den beskriver inte bara teknik. Den visar exempelvis förmågor som:

- plattformsproduktledning,
- säkerhetskrav som kod,
- driftbarhetsstandarder,
- självservice och behörighetsstyrning,
- observability och incidentförmåga,
- kapacitetsstyrning,
- övergångsarkitektur,
- ekonomisk uppföljning,
- kompetensutveckling,
- förändringsledning.

Förmågekartan hjälper ledningen att undvika en vanlig fälla: att tro att plattformen är färdig när tekniken är installerad. En plattform utan förmågor runt omkring blir snabbt ännu en teknisk komponent som organisationen måste samordna manuellt.

## Scenariot: Myndigheten för Samhällstjänst samlar ledningen

På Myndigheten för Samhällstjänst har containerplattformen nu gått från idé till verkligt vägval. Flera utvecklingsteam vill använda den. Driften ser möjligheter till standardisering men oroar sig för nya otydliga ansvar. Säkerhetsteamet vill undvika att självservice blir en genväg runt kontroller. Arkitektur vill inte skapa en ny teknikö utan koppling till befintliga tjänster. Ekonomifunktionen frågar hur kostnaderna ska fördelas. Verksamheten undrar när snabbare leverans faktiskt märks.

Efter flera månader av diskussioner inser ledningen att frågan inte längre kan behandlas som ett teknikinitiativ.

De beslutar därför att skapa en gemensam spelplan.

Den första versionen ryms på några sidor och består av fem delar:

1. gemensam målbild,
2. styrande principer,
3. ansvar och mandat,
4. beslutsforum och undantagshantering,
5. förmågekarta och införandeordning.

Det viktiga är inte att spelplanen är perfekt. Det viktiga är att den gör ledningens avvägningar synliga och möjliga att följa upp.

## Del 1: Gemensam målbild

En målbild behöver vara tillräckligt tydlig för att styra beslut, men inte så detaljerad att den blir en teknisk ritning. För en organisation som Myndigheten för Samhällstjänst kan målbilden formuleras så här:

> Vi ska utveckla en plattformsförmåga som gör det möjligt för godkända team att leverera förändringar snabbare, säkrare och mer förutsägbart genom standardiserad självservice, inbyggda kontroller och tydligt ansvar för driftbarhet, säkerhet och livscykel.

Den formuleringen är användbar därför att den binder ihop flera perspektiv:

- utveckling får snabbare och mer förutsägbar väg till miljöer och leverans,
- drift får standardisering, driftbarhetskrav och tydligare ansvar,
- säkerhet får inbyggda kontroller i stället för enbart efterhandsgranskning,
- ledning får styrbarhet, prioritering och uppföljning,
- verksamheten får en tydligare koppling mellan teknikplattform och leveranseffekt.

Målbilden bör också säga vad plattformen inte är. Exempelvis:

- den är inte en frizon från säkerhets- och driftkrav,
- den är inte en generell lösning för alla befintliga system,
- den är inte en ersättning för tydligt produkt- och systemägarskap,
- den är inte färdig bara för att den tekniska installationen fungerar,
- den är inte ett sätt att flytta allt ansvar till utvecklingsteamen.

Denna typ av negativa avgränsningar är viktiga. De minskar risken att olika grupper läser in helt olika förväntningar i samma initiativ.

## Del 2: Styrande principer

En gemensam spelplan behöver principer som hjälper organisationen fatta beslut när mål står mot varandra. Principerna ska vara få, tydliga och användbara.

Här är ett förslag på tio styrande principer för en reglerad organisation.

### 1. Självservice ges inom definierade ramar

Utvecklingsteam ska kunna göra mer själva, men friheten ska vara kopplad till tydliga villkor. Självservice betyder inte att varje team själv får definiera säkerhetsnivå, driftbarhet eller arkitekturprinciper.

Ledningsfråga: Vilka åtgärder får team göra själva, i vilka miljöer och med vilka kontroller?

### 2. Kontroller ska byggas in där de kan automatiseras

Säkerhets- och kvalitetskrav ska så långt möjligt byggas in i plattform, pipeline, mallar och policyer. Manuell granskning ska reserveras för riskbedömningar, undantag och nya typer av beslut.

Ledningsfråga: Vilka kontroller ska vara automatiserade innan självservice får skalas?

### 3. Driftbarhet är ett inträdeskrav, inte en efterkontroll

Tjänster som ska köras produktionsnära måste uppfylla operativa minimikrav. Loggning, övervakning, backup, återställning, incidenthantering och ansvar kan inte läggas till som en sen kvalitetssäkring.

Ledningsfråga: Vilka driftbarhetskrav är obligatoriska för olika risknivåer?

### 4. Plattformen är en intern produkt

Plattformen ska ha användare, produktägarskap, prioriteringar, livscykel, roadmap och supportmodell. Den ska inte styras enbart som infrastruktur eller projektleverans.

Ledningsfråga: Vem äger plattformens värde, prioritering och användarupplevelse?

### 5. Säkerhet äger krav och riskmodell, inte varje manuell grind

Säkerhetsfunktionen ska vara kravägare och riskrådgivare. Den ska definiera krav, kontrollpunkter och risknivåer, men inte behöva vara manuell passagepunkt för varje normal förändring.

Ledningsfråga: Vad måste säkerhetsteamet godkänna, och vad ska kontrolleras automatiskt?

### 6. Greenfield kräver integrationsplan från dag ett

En ny lösning eller ny organisatorisk enhet får inte bli en permanent parallell värld. Om greenfield väljs ska ledningen redan från början besluta hur resultatet ska integreras, normaliseras eller avgränsas.

Ledningsfråga: Vad är planen för att undvika två konkurrerande leveransmodeller?

### 7. Befintligt arv hanteras med medvetna migreringsprinciper

Alla system ska inte flyttas samtidigt. Alla system ska kanske inte flyttas alls. Ledningen behöver principer för vilka tjänster som ska moderniseras, vilka som ska ligga kvar och vilka som ska avvecklas.

Ledningsfråga: Vilka kriterier avgör om en tjänst ska flyttas, byggas om, kapslas in eller ligga kvar?

### 8. Finansiering ska följa långsiktig förmåga

Plattformen behöver kapacitet för utveckling, stabilitet, support, riskreducering och teknisk livscykel. Om finansieringen bara täcker införandet skapas en ny skuld.

Ledningsfråga: Hur finansieras plattformens utveckling och drift efter första införandet?

### 9. Undantag ska vara synliga och tidsbegränsade

Reglerade organisationer behöver undantag, men undantag får inte bli dold normalmodell. Varje undantag ska ha ägare, riskbedömning, giltighetstid och plan för återgång eller permanent beslut.

Ledningsfråga: Vem får bevilja undantag, hur länge gäller de och hur följs de upp?

### 10. Mätning ska visa förmåga, inte bara aktivitet

Antal migrerade applikationer, antal pipelines eller antal team på plattformen säger inte ensamt om organisationen blivit bättre. Mätning behöver visa ledtid, kvalitet, risk, återställningsförmåga, användarnöjdhet och minskad manuell samordning.

Ledningsfråga: Vilka mätetal visar att organisationen faktiskt blivit mer agil och mer styrbar?

## Del 3: Ansvar och mandat

En spelplan utan mandat blir en avsiktsförklaring. Därför behöver ledningen beskriva vem som ansvarar för vad.

Ett enkelt sätt är att skilja mellan fem ansvarstyper.

### Strategiskt ägarskap

Strategiskt ägarskap handlar om riktning, finansiering, risknivå och prioritering. Det bör ligga hos ett ledningsforum där produktion, utveckling, säkerhet, arkitektur och verksamhetsnära ansvar är representerade.

Det strategiska ägarskapet ska besluta:

- varför plattformsförmågan finns,
- vilka mål den ska uppnå,
- hur den finansieras,
- vilka risknivåer som accepteras,
- vilka större avvägningar som gäller,
- när arbetssättet ska skalas eller bromsas.

### Produktägarskap för plattformen

Produktägarskap handlar om att göra plattformen användbar och värdeskapande för interna användare. Det ska inte blandas ihop med driftansvar, även om rollerna behöver samarbeta nära.

Produktägarskapet ska ansvara för:

- roadmap,
- prioriterad backlog,
- användarbehov,
- tjänstekatalog,
- dokumentation,
- stöd till anslutande team,
- förbättring av användarupplevelse.

### Operativt plattformsansvar

Operativt ansvar handlar om att plattformen fungerar säkert, stabilt och enligt överenskommen servicenivå.

Det omfattar exempelvis:

- drift,
- kapacitet,
- patchning,
- övervakning,
- incidenthantering,
- säker konfiguration,
- backup och återställning där det är relevant,
- teknisk livscykel.

### Säkerhets- och riskansvar

Säkerhetsfunktionen bör äga riskmodell, kravtolkning och kontrollprinciper. Den bör också delta i utformningen av automatiserade kontroller och undantagshantering.

Den ska inte behöva godkänna varje standardiserad leverans om kraven redan är inbyggda och verifierade.

### Teamansvar

Utvecklings- eller produktteam som använder plattformen behöver tydligt ansvar för det de bygger och kör.

Det kan omfatta:

- applikationens kod och konfiguration,
- efterlevnad av plattformens mallar och krav,
- driftbarhetsinformation,
- incidentdeltagande,
- livscykel för egna komponenter,
- informationsklassning och verksamhetsnära riskförståelse,
- kostnadsmedveten användning av plattformens resurser.

Det viktiga är att teamansvar inte definieras som “ni får göra allt själva”. Det definieras som “ni får större handlingsutrymme inom tydliga ramar och med tydligt ansvar”.

## Del 4: Beslutsforum och undantagshantering

En stor organisation behöver inte fler möten. Den behöver rätt beslut på rätt plats.

Ett fungerande beslutsforum för plattformsförmåga bör ha tre nivåer.

### Ledningsforum för plattformsförmåga

Detta forum hanterar strategiska och principiella frågor:

- målbild,
- finansiering,
- prioritering mellan stabilitet och ny funktionalitet,
- riskacceptans,
- införandevågor,
- större undantag,
- ändrade ansvarsförhållanden,
- beslut om greenfield, brownfield eller hybrid väg.

Forumet ska inte fastna i detaljer om enskilda pipelines, mallar eller verktyg. Dess uppgift är att hålla spelplanen levande.

### Taktiskt plattformsforum

Detta forum hanterar prioriteringar och samordning mellan plattformsteam, säkerhet, drift, arkitektur och representanter för användande team.

Det kan besluta eller bereda:

- tjänstekatalog,
- standardmallar,
- nya självserviceförmågor,
- kommande kravändringar,
- supportmodell,
- tekniska beroenden,
- migreringsordning,
- förbättringar baserade på användarfeedback.

### Operativt forum

Det operativa forumet hanterar vardagsfrågor:

- incidenter,
- kapacitetsproblem,
- fel i mallar,
- återkommande supportärenden,
- förbättring av dokumentation,
- konkreta hinder för team,
- observationer från övervakning och drift.

När dessa tre nivåer blandas ihop uppstår antingen tröghet eller risk. Antingen måste varje fråga eskaleras, eller så fattas strategiska beslut i operativa sammanhang där rätt mandat saknas.

## Del 5: Förmågekartan

Förmågekartan är ett praktiskt sätt att se vad organisationen faktiskt behöver bygga upp. Här är en enkel modell med tio förmågeområden.

### 1. Målbild och styrningsprinciper

Finns en gemensam, beslutad och kommunicerad riktning? Vet cheferna vilka avvägningar som gäller?

Mognadstecken:

- målbild finns och används i beslut,
- principer är få och begripliga,
- målkonflikter hanteras öppet,
- ledningen följer upp förmåga, inte bara aktivitet.

### 2. Plattform som intern produkt

Finns produktägarskap, roadmap och tjänstekatalog?

Mognadstecken:

- plattformen har definierade användare,
- backlog prioriteras utifrån nytta, risk och kapacitet,
- support och dokumentation är planerade,
- användarfeedback påverkar utvecklingen.

### 3. Självservice och delegering

Kan team göra mer själva på ett säkert och spårbart sätt?

Mognadstecken:

- självservice är kopplad till behörigheter och krav,
- vanliga behov kräver inte manuell samordning,
- delegering sker stegvis,
- undantag är synliga.

### 4. Säkerhet och regelefterlevnad

Är säkerhetskraven inbyggda i arbetssättet?

Mognadstecken:

- krav är översatta till kontroller,
- policyer kan automatiseras där det är lämpligt,
- risknivåer är definierade,
- säkerhetsfunktionen arbetar mer med krav och risk än med repetitiv granskning.

### 5. Driftbarhet och robusthet

Kan tjänster förstås, övervakas, felsökas och återställas?

Mognadstecken:

- operativa minimikrav finns,
- loggning och övervakning är standardiserade,
- incidentansvar är tydligt,
- backup och återställning är prövade där det behövs.

### 6. Arkitektur och samexistens

Finns principer för hur gammalt och nytt ska fungera tillsammans?

Mognadstecken:

- övergångsarkitektur är dokumenterad,
- beroenden till befintliga plattformar är kända,
- migreringsprinciper används,
- organisationen undviker både totalstopp och okontrollerad flytt.

### 7. Finansiering och kapacitet

Har plattformen långsiktig finansiering och realistisk kapacitet?

Mognadstecken:

- kostnader följs upp,
- kapacitet för support och livscykel finns,
- prioriteringar är transparenta,
- finansiering täcker mer än införandeprojektet.

### 8. Kompetens och rollförståelse

Förstår funktionerna varandras situation och ansvar?

Mognadstecken:

- chefer delar gemensamt språk,
- utveckling, drift och säkerhet tränar på gemensamma scenarier,
- nya roller är tydligt beskrivna,
- ansvarsförändringar följs av kompetensutveckling.

### 9. Införande och normalisering

Finns en plan för att gå från pilot till normalläge?

Mognadstecken:

- piloter väljs för lärande, inte bara synlighet,
- förmågetrappa finns,
- beslut tas innan skalning,
- gamla arbetssätt avvecklas eller avgränsas när nya införs.

### 10. Uppföljning och lärande

Mäter organisationen rätt saker och justerar kursen?

Mognadstecken:

- mätetal visar ledtid, kvalitet, risk och återställning,
- återkommande hinder analyseras,
- spelplanen uppdateras,
- ledningen agerar på insikter.

## Ett konkret beslutsunderlag för ledningen

När Myndigheten för Samhällstjänst samlar sitt ledningsforum kan de använda följande frågor som startpunkt.

### A. Riktning

1. Vilka verksamhetsproblem ska plattformsförmågan lösa?
2. Vilka problem ska den inte lösa i första skedet?
3. Vilka typer av tjänster ska prioriteras?
4. Vad betyder snabbare leverans i vår organisation?
5. Vad får inte försämras när leveransen blir snabbare?

### B. Ansvar

1. Vem äger plattformens strategiska mål?
2. Vem äger plattformens produktutveckling?
3. Vem ansvarar för drift och teknisk livscykel?
4. Vem äger säkerhetskrav och riskmodell?
5. Vilket ansvar får teamen när de får mer självservice?

### C. Kontroll

1. Vilka kontroller ska vara inbyggda?
2. Vilka kontroller kräver fortfarande manuell bedömning?
3. Vilka krav är absoluta för produktion?
4. Hur hanteras undantag?
5. Hur följer vi upp att kontrollerna fungerar?

### D. Förändringstakt

1. Vilken pilot ger bäst lärande med acceptabel risk?
2. När är organisationen redo att skala till fler team?
3. Vilka gamla arbetssätt ska avvecklas, ändras eller behållas?
4. Vilka beroenden till befintliga plattformar begränsar takten?
5. Vad är vår plan för normalisering?

### E. Finansiering

1. Hur finansieras plattformen efter införandet?
2. Hur prioriteras support, stabilitet och ny funktionalitet?
3. Hur synliggörs kostnader för team och verksamhet?
4. Hur undviker vi att plattformsteamet blir en ny flaskhals?
5. Vilka investeringar krävs i kompetens och arbetssätt?

Dessa frågor kan användas som workshopunderlag, ledningsagenda eller checklista inför större beslut.

## Vanliga misstag

### Misstag 1: Spelplanen blir för teknisk

**Varför det händer:**  
Tekniken är konkret. Det är lättare att diskutera plattformsfunktioner än ansvar, mandat och finansiering.

**Hur man undviker det:**  
Låt den gemensamma spelplanen börja med målbild, principer och beslut. Lägg tekniska detaljer i underliggande arkitektur- och plattformsdokument.

### Misstag 2: Ledningen beslutar mål men inte målkonflikter

**Varför det händer:**  
Alla kan enas om att leveranser ska bli snabbare, säkrare och mer robusta. Det svåra är vad som gäller när målen krockar.

**Hur man undviker det:**  
Formulera principer för avvägningar. Exempel: “Självservice får skalas först när operativa minimikrav och automatiserade kontroller finns för aktuell risknivå.”

### Misstag 3: Plattformen får produktägare men inget mandat

**Varför det händer:**  
Organisationen inför moderna roller men behåller gamla beslutsvägar.

**Hur man undviker det:**  
Definiera vilka beslut produktägarskapet faktiskt får ta, vilka som kräver ledningsforum och vilka som ska hanteras operativt.

### Misstag 4: Undantag blir dold normalmodell

**Varför det händer:**  
Organisationen vill vara pragmatisk och hjälpa team vidare. Efter ett tag finns många speciallösningar som ingen längre ser som undantag.

**Hur man undviker det:**  
Inför undantagslogg med ägare, risk, giltighetstid och plan. Följ upp undantag i taktiskt forum och eskalera mönster till ledningen.

### Misstag 5: Man mäter införande i stället för förmåga

**Varför det händer:**  
Det är lätt att räkna antal team, miljöer, pipelines och migrerade applikationer.

**Hur man undviker det:**  
Komplettera aktivitetsmått med förmågemått: ledtid, ändringsfrekvens, återställningstid, incidentmönster, automatiseringsgrad, användarnöjdhet och minskad manuell samordning.

## Ledningens första 90 dagar

För att göra kapitlet handlingsdrivet kan ledningen börja med en koncentrerad första period. Den behöver inte heta “90 dagar” i praktiken, men tidsramen hjälper organisationen att undvika både fördröjning och överambition.

### Steg 1: Samla en gemensam nulägesbild

Ledningen bör samla utveckling, drift, säkerhet, arkitektur och verksamhetsrepresentanter kring samma nuläge.

Frågor att besvara:

- Var uppstår mest friktion i dagens beställningsflöden?
- Vilka typer av fel upprepas i miljöbeställningar?
- Vilka manuella kontroller skapar mest väntetid?
- Vilka risker är verkliga och vilka är historiska arbetssätt?
- Vilka team är redo för större självservice?
- Vilka tjänster är olämpliga som första kandidater?

Målet är inte att hitta syndabockar. Målet är att se systemet.

### Steg 2: Besluta preliminär spelplan

Spelplanen ska vara tillräckligt tydlig för att styra en första pilot och tillräckligt flexibel för att justeras.

Den bör innehålla:

- målbild,
- principer,
- ansvar,
- pilotkriterier,
- miniminivå för säkerhet och driftbarhet,
- forumstruktur,
- undantagshantering,
- mätetal.

### Steg 3: Välj pilot utifrån lärande

En pilot bör väljas för att ge relevant lärande, inte för att vara enklast eller mest synlig.

Bra pilotkandidater har ofta:

- motiverat team,
- tydligt verksamhetsvärde,
- begränsad men verklig komplexitet,
- hanterbar risk,
- behov av integration med befintlig miljö,
- beröring med säkerhets- och driftkrav,
- ledningssponsor.

### Steg 4: Följ upp principer, inte bara leverans

Efter piloten bör ledningen fråga:

- Vilka principer fungerade?
- Vilka var otydliga?
- Vilka beslut saknades?
- Var blev självservice verklig?
- Var uppstod nya manuella flaskhalsar?
- Vilka krav var för svåra att tolka?
- Vad måste ändras innan nästa våg?

### Steg 5: Normalisera eller stoppa

Efter en pilot finns tre möjliga beslut:

1. **Skala vidare** – om förmågan fungerar tillräckligt bra.
2. **Justera och pröva igen** – om riktningen är rätt men förmågor saknas.
3. **Stoppa eller avgränsa** – om modellen inte är lämplig för aktuellt behov.

Det sämsta beslutet är ofta inget beslut alls. Då fortsätter piloten som undantag, samtidigt som resten av organisationen inte vet vilken modell som gäller.

## Beslut att fatta

- Vilka gemensamma principer ska gälla för utveckling, drift, säkerhet och verksamhet när målkonflikter uppstår?
- Vilket ledningsforum ska äga den gemensamma spelplanen och följa upp efterlevnad?
- Vilka förändringar ska genomföras först för att skapa synlig effekt inom 3–6 månader?

## Snabb sammanfattning

- En gemensam spelplan håller ihop riktning, beslut och förmåga.
- Agilare leverans i en reglerad organisation kräver bättre styrning, inte frånvaro av styrning.
- Självservice måste kopplas till guardrails, driftbarhet, säkerhet och tydligt ansvar.
- Plattformen behöver styras som intern produkt med långsiktig finansiering och kapacitet.
- Greenfield och brownfield är strategiska val som kräver beslut om integration, normalisering och ansvar.
- En förmågekarta hjälper ledningen se vad som behöver byggas utöver tekniken.
- Undantag ska vara synliga, ägda och tidsbegränsade.
- Mätning ska visa om organisationen fått bättre leveransförmåga, inte bara om fler tekniska komponenter införts.
- Bokens rekommendationer blir användbara först när de omsätts i återkommande ledningsbeslut.

## Kontrollfrågor

1. Vilka tre målkonflikter är mest synliga i er organisation: snabbhet, säkerhet, robusthet, kostnad, standardisering, självbestämmande eller något annat?
2. Finns det i dag en beslutad målbild för plattformsförmåga, eller finns flera informella mål samtidigt?
3. Vilka beslut försöker ni i dag lösa operativt som egentligen kräver ledningsmandat?
4. Vilka kontroller skulle kunna byggas in i plattform eller pipeline i stället för att hanteras manuellt?
5. Vilka undantag har blivit så vanliga att de i praktiken är en dold normalmodell?
6. Vilka fem förmågor i förmågekartan är starkast hos er? Vilka tre är svagast?
7. Hur vet ni om självservice faktiskt minskar ledtid utan att öka risk?
8. Vilket forum äger frågan om plattformens långsiktiga finansiering?
9. Vilken första pilot skulle ge mest lärande utan att skapa oacceptabel risk?
10. Vad behöver ledningen besluta innan nästa steg tas?

## Nästa steg

Det här kapitlet avslutar bokens huvudresa. Nästa praktiska steg är inte att skriva ännu en plan, utan att använda bokens struktur som ledningsunderlag.

En lämplig fortsättning är att genomföra en workshop med chefer från utveckling, drift, säkerhet, arkitektur, förvaltning och verksamhet där ni:

1. formulerar er gemensamma målbild,
2. väljer styrande principer,
3. beskriver ansvar och mandat,
4. ritar er första förmågekarta,
5. identifierar nödvändiga ledningsbeslut,
6. väljer första pilot eller nästa införandevåg,
7. beslutar hur spelplanen ska följas upp.

Bokens kärnfråga kan sammanfattas så här:

**Vilken organisatorisk förmåga måste vi bygga för att modern teknik ska ge verklig effekt utan att vi förlorar den kontroll som vårt uppdrag kräver?**

Den viktigaste rekommendationen är därför tydlig: behandla inte containerplattformen som ett teknikinförande som kan delegeras nedåt i organisationen. Behandla den som ett ledningsbeslut om hur organisationen ska leverera, styra risk, finansiera gemensamma förmågor och ge team större handlingsutrymme inom tydliga ramar.

Ledningen behöver inte fatta varje tekniskt beslut. Men ledningen måste äga spelplanen. Utan den kommer utveckling, drift, säkerhet och arkitektur fortsätta optimera sina egna delar. Med den kan organisationen börja göra det svårare att göra fel, lättare att göra rätt och möjligt att förändra oftare utan att tappa kontroll.

När ledningen kan svara gemensamt på kärnfrågan har organisationen tagit det viktigaste steget från plattformar till plattformsförmåga.
