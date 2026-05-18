# Kapitel 1: Nuläget: när varje funktion optimerar sin egen vardag

## Varför detta kapitel finns

De flesta stora IT-organisationer har inte blivit långsamma, komplexa eller svårstyrda av en slump. De har blivit så genom en lång rad rationella beslut.

Driftorganisationen har byggt arbetssätt för stabilitet. Säkerhetsteamet har skapat riktlinjer för att skydda organisationen. Utvecklingsteamen har automatiserat det de kan påverka. Ledningen har infört forum, processer och kontrollpunkter för att hantera risk och koordinering.

Problemet är inte att någon grupp har agerat oansvarigt. Problemet är ofta att varje funktion har optimerat sin egen vardag inom de mandat och incitament den fått. Resultatet kan bli ett system där alla gör sitt bästa, men där helheten ändå inte fungerar tillräckligt bra.

Det här kapitlet hjälper dig som chef att se nuläget som ett system, inte som en samling person- eller funktionsproblem.

## Lärandemål

Efter kapitlet ska du kunna:

- förklara varför utveckling, drift och säkerhet kan uppleva samma flöde på helt olika sätt,
- känna igen lokal optimering i en IT-organisation,
- beskriva hur ett beställningsflöde kan skapa friktion även när varje del fungerar enligt sin logik,
- identifiera målkonflikter som behöver hanteras av ledningen, inte lösas genom mer detaljstyrning.

## Innan vi börjar

Boken använder begreppet **plattformsförmåga** för att beskriva mer än bara teknik. En plattformsförmåga består av teknik, arbetssätt, ansvar, finansiering, kompetens och styrning som tillsammans gör det möjligt att leverera säkert och effektivt.

I det här kapitlet börjar vi före lösningen. Vi tittar på varför en organisation som redan har automatisering, CI/CD och etablerade driftprocesser ändå kan uppleva att leveransförmågan inte räcker.

## Tre begrepp för att förstå nuläget

Det här kapitlet introducerar tre huvudbegrepp: **lokal optimering**, **beställningsflöde** och **målkonflikt**.

### Lokal optimering

Lokal optimering betyder att en grupp förbättrar sin egen situation utan att helheten nödvändigtvis förbättras.

Det behöver inte vara fel. En driftorganisation måste till exempel minska risken för incidenter. Ett säkerhetsteam måste skydda organisationen mot oacceptabla risker. Ett utvecklingsteam måste korta ledtider och minska onödigt manuellt arbete.

Men om varje funktion bara optimerar utifrån sina egna mål kan helheten bli trög, svårbegriplig och full av överlämningar.

### Beställningsflöde

Ett beställningsflöde är ett arbetssätt där ett team begär en miljö, en ändring, en anslutning eller en teknisk förutsättning som en annan funktion tolkar, koordinerar, kvalitetssäkrar och utför.

Beställningsflöden är vanliga i stora organisationer. De ger spårbarhet och kontroll, men kan också skapa väntetider, omtag och missförstånd. Ju mer varje beställning kräver tolkning, desto mer beroende blir organisationen av enskilda personer, informella kontakter och lokal kunskap.

### Målkonflikt

En målkonflikt uppstår när två legitima mål drar åt olika håll.

Snabbare leverans och starkare kontroll kan hamna i konflikt. Självservice och standardisering kan hamna i konflikt. Hög tillgänglighet och snabb förändringstakt kan hamna i konflikt. Lokal autonomi och gemensam arkitektur kan hamna i konflikt.

Ledningens uppgift är inte att låtsas att målkonflikterna inte finns. Ledningens uppgift är att göra dem synliga, prioritera mellan dem och skapa spelregler som organisationen kan agera inom.

## Scenariot: Myndigheten för Samhällstjänst

Myndigheten för Samhällstjänst har under lång tid byggt en stabil IT-verksamhet. Organisationen har flera etablerade plattformar. Vissa applikationer körs på applikationsservrar. Meddelandeflöden hanteras via köteknik. Databaser, sökplattformar och lagring finns som viktiga delar av den befintliga miljön.

Utvecklingsteamen har kommit olika långt. Vissa har fungerande CI/CD och kan leverera automatiskt när deras miljöer väl är på plats. Andra är mer beroende av manuella moment. Driftorganisationen tar emot miljöbeställningar, gör vissa delar via skript och koordinerar större förändringar genom en driftskoordinerande funktion. Säkerhetsteamet styr genom riktlinjer, krav och bedömningar.

På ytan är detta en rimlig uppdelning. Varje funktion har ett tydligt uppdrag. Ändå växer missnöjet.

Utvecklingsteamen tycker att de väntar för länge. De upplever att de måste förklara samma behov flera gånger och att beställningsvägen inte passar modern automatiserad utveckling.

Driftorganisationen tycker att beställningarna är spretiga. De saknar ofta rätt information, kommer sent eller kräver speciallösningar. Drift ser risk att stabiliteten försämras om team får göra mer själva utan tydliga ramar.

Säkerhetsteamet ser att riktlinjer inte alltid omsätts korrekt i praktiken. De oroar sig för att ökad frihet ska skapa svårgranskade lösningar, otydliga ansvar och förhöjd risk.

Ledningen ser en organisation som pratar om modern teknik men fortfarande har svårt att röra sig tillräckligt snabbt.

Alla perspektiv är begripliga.

## Varför nuläget består

Nuläget består ofta därför att det fungerar tillräckligt bra för varje funktion var för sig.

Driftorganisationen kan visa att den skyddar stabiliteten. Säkerhetsteamet kan visa att det har riktlinjer och krav. Utvecklingsteamen kan visa att de har automatiserat inom sitt område. Ledningen kan visa att det finns processer, forum och beslutspunkter.

Men helheten kan ändå ha flera svagheter:

- mycket arbete kräver manuell koordinering,
- kvaliteten på beställningar varierar,
- krav tolkas olika mellan funktioner,
- ansvar för helheten är otydligt,
- automatisering finns i delar men inte genom hela flödet,
- förändringstakten styrs av överlämningar snarare än av värdeflöde,
- beslut om risk och frihetsgrader skjuts neråt i organisationen.

Det här är inte bara ett processproblem. Det är ett ledningsproblem.

## Den dolda kostnaden i beställningsflödet

Beställningsflöden har synliga kostnader: ärenden, väntetider, möten och omtag. Men de största kostnaderna är ofta mindre synliga.

### 1. Tolkning ersätter standardisering

När varje beställning behöver tolkas blir organisationen beroende av mänsklig bedömning i varje enskilt fall. Det kan ge flexibilitet, men det gör också leveransen svår att förutsäga.

En modern plattformsförmåga kräver att återkommande behov blir standardiserade tjänster. Då behöver frågan ändras från “vem kan lösa detta ärende?” till “vilken tjänst borde finnas så att ärendet inte behöver uppstå?”.

### 2. Kontroll sker sent

I många beställningsflöden sker kontrollen efter att behovet redan är formulerat, designat eller delvis byggt. Då blir säkerhet, driftbarhet och robusthet något som granskas sent.

Sen kontroll skapar irritation. Utveckling upplever stopp. Drift och säkerhet upplever att de får ta ansvar för risker de inte varit med och format från början.

### 3. Ansvar blir otydligt

När flera funktioner är inblandade i varje förändring kan det bli oklart vem som faktiskt äger resultatet.

Utveckling kanske äger applikationen. Drift äger miljön. Säkerhet äger kraven. Arkitektur äger principerna. Men vem äger att helheten fungerar som leveransförmåga?

Om svaret är “alla” blir det i praktiken ofta “ingen med tillräckligt mandat”.

### 4. Automatisering fastnar i stuprör

Utvecklingsteam kan automatisera bygg, test och deployment. Drift kan automatisera provisionering med skript. Säkerhet kan automatisera vissa kontroller. Men om automatiseringen inte hänger ihop över funktionsgränserna blir helheten fortfarande manuell.

Det räcker alltså inte att flera delar är automatiserade. Frågan är om organisationens värdeflöde är automatiserat och styrbart från idé till säker drift.

## Lokal optimering i fyra funktioner

För att förstå nuläget behöver ledningen se hur varje funktion agerar rationellt utifrån sin verklighet.

### Utvecklingens logik

Utvecklingsteamen mäts ofta på leverans av funktionalitet, förändringstakt och förmåga att möta verksamhetens behov. De vill minska väntetider och beroenden. De vill kunna skapa, ändra, testa och driftsätta utan att varje steg kräver ett nytt ärende.

När de möter tröga beställningsflöden försöker de automatisera runt problemen. I bästa fall leder det till effektivare leverans. I sämsta fall leder det till lokala speciallösningar som andra funktioner inte kan förvalta eller granska.

Utvecklingens risk är att underskatta vad som krävs för stabil och säker produktion.

### Driftens logik

Driftorganisationen mäts ofta på stabilitet, tillgänglighet, incidentminimering och kontrollerad förändring. Den ser konsekvenserna när krav är otydliga, när lösningar inte är driftbara eller när förändringar införs utan tillräcklig hänsyn till övervakning, backup, kapacitet och återställning.

När drift möter spretiga beställningar skapar den checklistor, koordinering och kvalitetssäkring. Det är rationellt. Men om varje avvikelse hanteras som ett separat ärende växer komplexiteten.

Driftens risk är att skydda stabiliteten genom kontrollformer som gör förändring för långsam.

### Säkerhetens logik

Säkerhetsteamet ansvarar för risker som ofta blir synliga först när något går fel. Det är därför naturligt att säkerhet vill ha riktlinjer, granskning, spårbarhet och efterlevnad.

När säkerhet inte kan lita på att kraven är inbyggda i arbetssätten behöver teamet styra genom dokument, kontroller och godkännanden. Det kan vara nödvändigt, men det skalar dåligt.

Säkerhetens risk är att bli en sen kontrollpunkt i stället för en möjliggörare av säkra standardflöden.

### Ledningens logik

Ledningen vill ofta både öka förändringstakten och minska risk. Den vill använda modern teknik men undvika störningar i samhällsviktiga eller affärskritiska tjänster. Den vill ge team mandat men samtidigt kunna visa kontroll.

När målbilden är oklar tenderar ledningen att efterfråga mer samverkan, fler forum eller bättre beställningar. Det kan hjälpa, men det löser inte grundfrågan om ansvar, mandat och styrmodell.

Ledningens risk är att be organisationen bli mer agil utan att ändra de beslutssystem som gör organisationen trög.

## Frågan chefer bör ställa

När nuläget skaver är det frestande att fråga:

“Varför fungerar inte beställningarna bättre?”

Det är inte fel, men det är för smalt.

En bättre ledningsfråga är:

**Vilka återkommande behov ska inte längre hanteras som individuella beställningar, utan som standardiserade plattformstjänster med inbyggd kontroll?**

Den frågan flyttar fokus från ärendekvalitet till organisationsdesign.

Den gör också målkonflikten tydligare. Om utvecklingsteam ska få mer självservice måste drift och säkerhet få något tillbaka: standardisering, spårbarhet, automatiserade kontroller, tydliga driftkrav och mandat att definiera ramarna.

Självservice utan ramar blir risk. Ramar utan självservice blir flaskhals. Ledningens uppgift är att besluta hur balansen ska se ut.

## Ledningsrekommendationer

### 1. Beskriv nuläget som ett flöde, inte som en organisationskarta

En organisationskarta visar vem som rapporterar till vem. Ett flöde visar hur arbete faktiskt rör sig från behov till drift.

Ledningen bör kartlägga ett fåtal vanliga förändringstyper: en ny miljö, en förändrad integration, en ny applikationsversion, en ändrad säkerhetskonfiguration eller en produktionssättning. Följ arbetet över funktionsgränserna. Notera väntetider, omtag, beslut, tolkningar och manuella kontroller.

Målet är inte att hitta skyldiga. Målet är att se systemet.

### 2. Skilj på variation som behövs och variation som bara är dyr

All variation är inte dålig. Vissa system har särskilda krav. Vissa miljöer kräver extra säkerhet eller tillgänglighet. Men mycket variation finns för att organisationen saknar standardiserade erbjudanden.

Ledningen bör fråga vilka miljötyper, säkerhetsnivåer, driftkrav och integrationsmönster som kan standardiseras. Ju mer som kan standardiseras, desto mer kan självservice införas utan att kontrollen tappas.

### 3. Gör målkonflikter explicita

Målkonflikter ska inte döljas i processer. De ska upp på bordet.

Exempel på målkonflikter som ledningen behöver formulera:

- Hur mycket frihet ska utvecklingsteam ha i produktionsnära miljöer?
- Vilka säkerhetskrav får aldrig kringgås?
- Vilka driftkrav måste vara uppfyllda innan en tjänst får självservice?
- När är snabb leverans viktigare än full standardisering?
- När är standardisering viktigare än lokala önskemål?

När målkonflikter inte hanteras på rätt nivå hamnar de hos specialister, koordinatorer och teamledare utan tillräckligt mandat.

### 4. Byt språk från “beställare och utförare” till “förmågor och ansvar”

Beställar- och utförarspråk kan vara användbart för tydliga tjänster. Men när organisationen ska bygga plattformsförmåga räcker det inte.

Frågan är inte bara vem som beställer och vem som levererar. Frågan är vilka förmågor organisationen behöver: självservice, säkerhetsstyrning, driftbarhet, automatiserad provisionering, observability, incidentförmåga, kapacitetsstyrning och gemensam prioritering.

När språket ändras blir också ledningsansvaret tydligare. Förmågor behöver ägarskap, finansiering och utveckling över tid.

## Exempel: samma ärende ur fyra perspektiv

Ett utvecklingsteam hos Myndigheten för Samhällstjänst behöver en ny testmiljö för en tjänst som på sikt ska kunna köras containerbaserat. Teamet skickar en beställning.

Utvecklingsteamet tycker att behovet är enkelt. De vill ha en miljö snabbt för att kunna testa sin leverans.

Driftorganisationen ser flera obesvarade frågor. Hur ska miljön övervakas? Vilken kapacitet krävs? Ska den anslutas till befintliga köer eller databaser? Vem ansvarar för incidenter? Hur ska livscykeln hanteras?

Säkerhetsteamet undrar vilken data som ska användas, vilka åtkomster som krävs och om lösningen följer gällande riktlinjer.

Ledningen ser ännu ett exempel på att modernisering tar längre tid än väntat.

Alla fyra perspektiv är rimliga. Problemet är att organisationen saknar en standardiserad väg för återkommande behov. Därför måste varje beställning bära hela tyngden av teknik, risk, ansvar och tolkning.

En plattformsförmåga skulle inte ta bort alla frågor. Men den skulle göra många av svaren fördefinierade.

## Vanliga misstag

### Misstag: Att tro att problemet är dåliga beställningar

**Varför det händer:** Driftorganisationen ser ofta beställningar som saknar information eller innehåller fel antaganden.

**Hur man undviker det:** Se dåliga beställningar som symptom. Fråga vilka behov som borde standardiseras, vilka mallar som saknas och vilka beslut som utvecklingsteam inte rimligen kan förväntas känna till.

### Misstag: Att tro att mer självservice automatiskt löser problemet

**Varför det händer:** Utvecklingsteamens väntetider är tydliga och självservice låter som en direkt lösning.

**Hur man undviker det:** Koppla självservice till guardrails, standardiserade tjänster, behörighetsmodeller, driftkrav och automatiserade kontroller. Självservice utan styrning skapar ny risk.

### Misstag: Att placera alla målkonflikter i samverkansforum

**Varför det händer:** Samverkan uppfattas som mindre konfliktfylld än tydliga beslut.

**Hur man undviker det:** Använd forum för beredning och lärande, men låt ledningen fatta beslut om mandat, risknivå, standardisering och prioritering.

### Misstag: Att införa ny teknik utan att ändra ansvar

**Varför det händer:** Teknikprojekt är lättare att starta än organisationsförändring.

**Hur man undviker det:** Behandla containerplattformen som ett strategiskt vägval. Definiera tidigt vem som äger plattformen som produkt, vem som finansierar den, vem som sätter ramarna och vilka team som får göra vad.

## Övningar

### Övning 1: Kartlägg ett återkommande beställningsflöde

Välj ett vanligt flöde i din organisation, till exempel beställning av en ny miljö, ändring av en integration eller produktionssättning av en ny version.

Besvara följande frågor:

1. Vilka funktioner är inblandade?
2. Var sker väntan?
3. Var sker omtolkning?
4. Vilka beslut tas om och om igen?
5. Vilka krav kontrolleras sent?
6. Vilka delar skulle kunna bli standardiserade plattformstjänster?

### Övning 2: Identifiera lokal optimering

Skriv ner tre saker som din egen funktion har gjort för att förbättra sin vardag. För varje punkt, fråga:

1. Hjälper detta helheten eller främst vår funktion?
2. Skapar det mer eller mindre arbete för andra?
3. Bygger det långsiktig förmåga eller hanterar det bara ett symptom?

### Fördjupning: Ledningsdialog

Samla chefer eller representanter från utveckling, drift, säkerhet och arkitektur. Låt varje grupp beskriva samma återkommande flöde utifrån sitt perspektiv.

Regel: ingen grupp får argumentera emot de andra i första rundan. Målet är att förstå varför nuläget är rationellt för varje funktion.

Avsluta med frågan:

**Vilket beslut saknar vi på ledningsnivå för att detta flöde ska bli enklare, säkrare och mer förutsägbart?**

## Beslut att fatta

- Vilka återkommande beställningar ska sluta hanteras som unika ärenden och i stället bli standardiserade erbjudanden?
- Vilka målkonflikter mellan utveckling, drift och säkerhet behöver lyftas till gemensamt ledningsbeslut?
- Vilka lokala optimeringar är acceptabla, och vilka skadar organisationens samlade leveransförmåga?

## Snabb sammanfattning

- Nuläget är ofta resultatet av rationella beslut i varje funktion.
- Lokal optimering kan göra helheten långsammare även när varje grupp förbättrar sin egen situation.
- Beställningsflöden ger kontroll men kan skapa väntan, tolkning och otydligt ansvar.
- Målkonflikter mellan snabbhet, säkerhet, robusthet och standardisering måste hanteras av ledningen.
- Den centrala frågan är vilka återkommande behov som ska bli standardiserade plattformstjänster i stället för individuella beställningar.

## Kontrollfrågor

1. Vilken lokal optimering i din organisation skapar störst negativ effekt för helheten?
2. Vilka återkommande beställningar borde inte längre vara beställningar?
3. Var sker säkerhets- eller driftkontroll för sent i dagens flöde?
4. Vilka målkonflikter har delegerats för långt ner i organisationen?
5. Vad skulle drift och säkerhet behöva få tillbaka för att utvecklingsteam ska kunna få mer självservice?

## Nästa steg

I nästa kapitel går vi från nuläge till målbild. Vi ska definiera vad bättre agil förmåga faktiskt betyder i en stor reglerad organisation. Det räcker inte att säga att organisationen ska bli snabbare. Ledningen behöver veta vad som ska bli snabbare, vilka risker som fortfarande ska kontrolleras och vilka förmågor som måste byggas för att snabbhet och kontroll ska kunna samexistera.
