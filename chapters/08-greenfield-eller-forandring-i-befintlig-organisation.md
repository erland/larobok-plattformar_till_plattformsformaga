# Kapitel 8: Greenfield eller förändring i befintlig organisation?

## Varför detta kapitel finns

När en stor reglerad organisation står inför en containerplattform uppstår ofta en frestande fråga: ska vi bygga något helt nytt vid sidan av den befintliga organisationen, eller ska vi förändra den organisation vi redan har?

Frågan är större än teknik. Den handlar om mandat, tempo, kultur, risk, finansiering och förmågan att få olika delar av organisationen att röra sig åt samma håll. En greenfield-satsning kan skapa fart, tydlighet och frihet från gamla arbetssätt. Samtidigt kan den skapa en ny silo, en parallell verklighet och en integrationsskuld som senare blir dyr att hantera. En förändring i befintlig organisation kan ge bred förankring och långsiktig effekt, men riskerar att gå långsamt om gamla styrmodeller, köer och ansvarsfördelningar följer med in i den nya plattformen.

För ledningen är därför frågan inte: *vilken väg är modernast?* Frågan är: *vilken väg bygger rätt förmåga, med acceptabel risk, i just vår organisation?*

I det här kapitlet får du en beslutsmodell för att bedöma när greenfield är lämpligt, när förändring i befintlig organisation är bättre och när en kombinerad väg behövs.

## Lärandemål

Efter kapitlet ska läsaren kunna:

- skilja mellan greenfield, brownfield och parallell organisation som strategiska förändringsalternativ,
- bedöma när en separat ny lösning kan vara motiverad,
- identifiera risker med att skapa en ny plattform eller organisation vid sidan av den befintliga,
- värdera när stegvis förändring i befintlig organisation är mer hållbar,
- formulera ledningsfrågor som behöver besvaras innan vägvalet görs.

## Innan vi börjar

Tidigare kapitel har etablerat att en containerplattform inte bara är en teknisk komponent. Den blir strategisk först när den kopplas till en operativ modell, tydliga mandat, inbyggda kontroller, självservice och operativa minimikrav.

Det betyder att vägvalet i detta kapitel inte kan avgöras genom att fråga om OpenShift, Kubernetes eller någon annan plattform är tekniskt lämplig. Den frågan är viktig, men otillräcklig. Ledningen behöver också fråga:

- Vilka arbetssätt måste ändras?
- Vilka beslut måste flyttas närmare teamen?
- Vilka kontroller måste byggas in i plattform och pipeline?
- Vilka befintliga beroenden går inte att önska bort?
- Vilken organisation har faktiskt mandat att göra förändringen?

## Tre huvudbegrepp

### Greenfield

Med **greenfield** menas att organisationen skapar en ny lösning, plattform eller organisatorisk modell med få direkta beroenden till det befintliga arvet. I praktiken kan det innebära ett nytt plattformsteam, en ny containerplattform, nya processer, nya mallar, ny finansiering och ett begränsat antal utvalda team som får börja arbeta på ett nytt sätt.

Greenfield ger frihet. Men frihet från gamla begränsningar betyder också att ledningen måste vara tydlig med hur den nya lösningen senare ska kopplas till resten av organisationen.

### Brownfield

Med **brownfield** menas att förändringen görs i eller nära den befintliga organisationen, med befintliga system, beroenden, roller, arbetssätt och styrmodeller som utgångspunkt. Det kan handla om att stegvis förändra driftens uppdrag, säkerhetsteamets arbetssätt, utvecklingsteamens ansvar och plattformens leveransmodell utan att skapa en helt separat värld.

Brownfield är ofta mindre glamoröst men mer realistiskt. Det tvingar organisationen att hantera de beroenden som redan finns.

### Parallell organisation

En **parallell organisation** uppstår när en ny satsning byggs bredvid den befintliga, men utan tydlig plan för hur de två världarna ska kopplas ihop. Det kan börja som ett legitimt greenfield-initiativ men med tiden bli ett eget stuprör.

Risken är att organisationen får två regelverk, två kulturer, två leveransmodeller, två finansieringslogiker och två olika svar på frågan “hur gör vi här?”. Då har man inte löst fragmenteringen. Man har skapat en ny variant av den.

## Scenariot: Myndigheten för Samhällstjänst står inför vägvalet

Hos Myndigheten för Samhällstjänst har ledningen enats om att den nuvarande modellen med miljöbeställningar inte räcker för framtida behov. Utvecklingsteamen vill kunna skapa och förändra miljöer snabbare. Driften vill minska felaktiga och spretiga beställningar. Säkerhetsteamet vill se bättre efterlevnad, inte fler manuella undantag. Verksamheten vill ha kortare ledtider utan fler incidenter.

Ett förslag växer fram: skapa en ny OpenShift-baserad plattform med ett separat team, egna processer och utvalda pilotapplikationer. Förespråkarna argumenterar för att befintlig organisation är för långsam och för belastad av förvaltning. Motståndarna oroar sig för att plattformen ska bli ännu en speciallösning som driften senare förväntas ta över, utan att krav på robusthet, övervakning, backup, incidenthantering och säkerhet är tillräckligt mogna.

Båda sidor har rätt i något viktigt.

Greenfield kan skapa tempo. Men om den nya plattformen inte från början designas för myndighetens verkliga krav blir den svår att skala. Brownfield kan skapa långsiktig förankring. Men om allt måste gå genom befintliga köer och godkännanden kommer plattformen inte förändra leveransförmågan.

Ledningens uppgift är därför inte att välja sida. Uppgiften är att välja väg, villkor och styrning.

## När greenfield är rätt väg

Greenfield kan vara en klok strategi när organisationen behöver skapa lärande och rörelse som inte är möjlig i den befintliga modellen. Det är särskilt relevant när de nuvarande arbetssätten är så tunga att en ny förmåga aldrig får syre om den måste börja inom samma struktur.

Greenfield är ofta lämpligt när flera av följande villkor är uppfyllda:

- det finns tydligt ledningsmandat för att skapa en ny operativ modell,
- det finns ett avgränsat verksamhetsbehov där risk och beroenden kan hanteras,
- befintliga processer är för långsamma för att ge plattformen en rimlig start,
- organisationen behöver bevisa ett nytt arbetssätt innan det går att få bred acceptans,
- kompetensen finns eller kan byggas i ett fokuserat team,
- säkerhet, driftbarhet och robusthet kan designas in från början,
- det finns en plan för hur lärdomar ska återföras till huvudorganisationen.

Ett bra greenfield-initiativ är alltså inte ett frikort från styrning. Det är en kontrollerad lärmiljö med tydliga ramar.

### Greenfield kräver hårdare ledningsdisciplin än man tror

Många greenfield-satsningar startar med argumentet att man vill slippa byråkrati. Det kan vara rimligt. Men i en reglerad organisation får “slippa byråkrati” aldrig betyda “slippa ansvar”.

Ledningen behöver därför definiera:

- vilka krav som är absoluta och inte kan väljas bort,
- vilka krav som kan uppfyllas på nya sätt,
- vem som äger risker under piloten,
- hur incidenter och avvikelser hanteras,
- när lösningen får användas för produktionsnära eller produktionskritiska tjänster,
- hur erfarenheter dokumenteras,
- när greenfield-satsningen ska skalas, avslutas eller integreras.

En greenfield-satsning utan sådana beslut blir ofta beroende av eldsjälar. Det kan skapa snabb början men svag uthållighet.

## När förändring i befintlig organisation är bättre

Att förändra befintlig organisation är ofta rätt väg när den nya plattformen måste fungera tätt ihop med befintliga system och ansvar från början. I organisationer som redan har JBoss EAP, IBM MQ, Oracle Database, Elasticsearch och Ceph som viktiga plattformar är det sällan möjligt att bygga en helt isolerad framtid.

Brownfield är ofta lämpligt när flera av följande villkor är uppfyllda:

- den nya plattformen är starkt beroende av befintlig infrastruktur, nät, identitet, loggning, databaser eller integrationsmönster,
- befintlig driftorganisation även fortsättningsvis kommer bära ansvar för tillgänglighet och incidenter,
- säkerhetsteamets krav måste gälla brett och konsekvent,
- många applikationer kommer vara hybrida under lång tid,
- organisationen behöver minska fragmentering snarare än skapa ännu ett arbetssätt,
- det finns tillräckligt ledningsmandat att ändra befintliga processer,
- målet är långsiktig normalisering snarare än snabb isolerad pilot.

Den stora fördelen med brownfield är att förändringen sker där den långsiktiga leveransförmågan faktiskt behöver bo. Den stora nackdelen är att förändringen måste konkurrera med daglig förvaltning, incidenter, skuld och etablerade vanor.

### Brownfield får inte betyda “allt ska vara som förut”

Ett vanligt misstag är att välja förändring i befintlig organisation men behålla samma beställningslogik. Då införs en ny plattform, men den gamla leveransmodellen överlever.

Det kan se ut så här:

- utvecklingsteam beställer fortfarande miljöer via fria textfält,
- driften tolkar fortfarande behov manuellt,
- säkerhetsteamet granskar fortfarande sent i flödet,
- undantag hanteras fortfarande personberoende,
- plattformsteamet blir ännu en utförandegrupp i kön,
- ledningen tror att teknikbytet i sig ska skapa agilitet.

Detta är inte transformation. Det är teknisk modernisering med gammal styrning.

För att brownfield ska fungera behöver ledningen besluta vilka delar av befintlig organisation som faktiskt ska ändras: mandat, processer, standarder, finansiering, mätetal och ansvar.

## Den farliga mellanformen: greenfield utan integrationsplan

Den vanligaste risken är inte att organisationen väljer greenfield eller brownfield. Den vanligaste risken är att man säger greenfield, men inte leder det som ett strategiskt experiment.

Då händer ofta följande:

1. Ett nytt team får bygga en modern plattform.
2. Några utvalda team får arbeta snabbare än andra.
3. Undantag accepteras eftersom satsningen är viktig.
4. Befintlig drift och säkerhet involveras sent eller otydligt.
5. Plattformen börjar användas för mer kritiska tjänster.
6. Frågan om långsiktigt ansvar blir akut.
7. Huvudorganisationen upplever att den får ärva en lösning den inte varit med och format.
8. Den nya plattformen blir ett nytt stuprör.

Detta är inte ett argument mot greenfield. Det är ett argument mot greenfield utan exitkriterier, integrationsprinciper och ledningsägda beslut.

## En kombinerad väg: skyddad start, planerad integration

För många stora reglerade organisationer är den bästa vägen varken ren greenfield eller ren brownfield. Den är en kombination:

- starta med ett skyddat område där nya arbetssätt kan prövas,
- välj applikationer med hanterbar risk men verkliga behov,
- bygg plattformstjänster som produkter från början,
- involvera drift, säkerhet och arkitektur i design av guardrails och operativa minimikrav,
- dokumentera vad som ska bli standard,
- skapa en plan för hur ansvar, finansiering och support ska normaliseras,
- ändra befintlig organisation stegvis baserat på lärdomar.

Den kombinerade vägen ger utrymme att lära utan att låtsas att arvet inte finns. Den kräver dock tydliga beslut om när piloten slutar vara pilot.

### Tre horisonter för den kombinerade vägen

Ledningen kan tänka i tre horisonter.

**Horisont 1: Skyddad etablering**  
Plattformen byggs och prövas med ett fåtal team. Fokus ligger på lärande, grundläggande guardrails, operativa minimikrav och fungerande samarbete mellan plattform, utveckling, drift och säkerhet.

**Horisont 2: Kontrollerad breddning**  
Fler team ansluts, men bara inom definierade tjänsteklasser och risknivåer. Självservice utökas där kontroller är automatiserade och driftbarhet är bevisad. Undantag hanteras synligt.

**Horisont 3: Normaliserad förmåga**  
Plattformen är inte längre ett särskilt initiativ. Den är en del av organisationens normala leveransmodell, med finansiering, ägarskap, roadmap, support, incidentprocesser och styrning som håller över tid.

## Beslutsmodell: fem frågor före vägvalet

Innan ledningen väljer väg bör fem frågor besvaras.

### 1. Vad är det verkliga problemet vi försöker lösa?

Om problemet främst är teknisk föråldring kan en plattformsförnyelse vara central. Om problemet är långa ledtider, otydliga mandat och sena kontroller räcker inte teknik. Då måste operativ modell och styrning ändras.

Formulera problemet som en förmågebrist, inte som ett teknikbehov.

Svagt formulerat problem:  
“Vi behöver OpenShift.”

Starkare formulerat problem:  
“Vi behöver kunna ge utvecklingsteam standardiserad, säker och spårbar självservice för vanliga miljöbehov, utan att drift och säkerhet blir manuella flaskhalsar.”

### 2. Vilka beroenden kan inte väljas bort?

Identifiera vilka beroenden som måste finnas från början. Det kan vara nät, identitet, certifikat, loggning, övervakning, meddelandeköer, databaser, lagring, backup, incidentprocesser, säkerhetsklassning och integrationsmönster.

Om många beroenden är kritiska från dag ett talar det för brownfield eller en starkt integrerad greenfield-modell. Om beroendena kan avgränsas kan greenfield vara mer realistiskt.

### 3. Vem ska äga risken under övergången?

Alla vägval skapar risk. Greenfield skapar risk för separation och framtida integrationsproblem. Brownfield skapar risk för långsamhet och utspädning av förändringen.

Ledningen behöver besluta vem som äger dessa risker. Det kan inte lämnas till projektledare, plattformsteam eller enskilda arkitekter.

### 4. Vilka delar av den nya modellen ska bli standard?

En pilot som inte definierar framtida standarder skapar bara lokal erfarenhet. Ledningen behöver tidigt ange vilka delar som ska kunna återanvändas: mallar, säkerhetskrav, driftkrav, självservicenivåer, tjänsteklasser, ansvarsfördelning och beslutsforum.

### 5. När vet vi att vägvalet behöver ändras?

En mogen strategi innehåller omprövningspunkter. Greenfield kan behöva integreras tidigare än planerat. Brownfield kan behöva skyddade undantag för att inte fastna. Den kombinerade vägen kan behöva smalnas av om organisationen försöker skala för fort.

Definiera därför beslutspunkter, inte bara milstolpar.

## Ledningsrekommendationer

### Rekommendation 1: Välj inte greenfield för att undvika svåra samtal

Om ledningen väljer greenfield för att slippa hantera ansvarsfördelning, finansiering, säkerhetskrav eller driftansvar kommer de frågorna tillbaka senare. Då är de ofta mer akuta.

Greenfield är rätt när den används för fokuserat lärande och snabb etablering av ny förmåga. Den är fel när den används för att skjuta upp nödvändiga ledningsbeslut.

### Rekommendation 2: Välj inte brownfield om organisationen saknar mandat att förändra sig

Brownfield kräver förändringsmandat. Om befintliga funktioner förväntas behålla sina köer, mätetal och beslutsrättigheter oförändrade kommer plattformen att formas efter gamla arbetssätt.

Då är det bättre att skapa ett skyddat område för lärande än att låtsas att organisationen förändras genom att införa ny teknik.

### Rekommendation 3: Kräv en integrationsplan från första dagen

Även om satsningen startar separat behöver det finnas en plan för hur den kopplas till befintlig organisation. Planen behöver inte vara detaljerad i allt, men den måste svara på:

- vilka förmågor som ska tas över av linjen,
- vilka som ska ligga kvar i ett plattformsteam,
- vilka krav som gäller för produktionssättning,
- hur support och incidenthantering fungerar,
- hur kostnader och prioriteringar styrs,
- hur lärdomar blir standard.

### Rekommendation 4: Behandla befintligt arv som fakta, inte som motstånd

Befintliga plattformar, integrationer och processer finns ofta av goda skäl. De kan vara gamla, tunga eller svåra att förändra, men de bär också ansvar, stabilitet och verksamhetskritiska tjänster.

Ledningen bör därför undvika språk som ställer “det nya” mot “det gamla”. En bättre fråga är: vilka delar av arvet ska avvecklas, vilka ska moderniseras, vilka ska integreras och vilka ska skyddas under övergången?

### Rekommendation 5: Mät förmågeförflyttning, inte bara teknikleverans

Det räcker inte att mäta om plattformen är installerad eller om en pilot fungerar. Mät om organisationen faktiskt får ny förmåga:

- kortare ledtid för standardiserade miljöbehov,
- färre felaktiga beställningar,
- högre grad av automatiserade kontroller,
- tydligare ansvar mellan team och plattform,
- bättre driftbarhet vid produktionssättning,
- färre manuella undantag,
- snabbare återkoppling på säkerhets- och kvalitetskrav.

## Vanliga misstag

### Misstag: Att kalla allt nytt för greenfield

**Varför det händer:**  
Organisationen vill signalera nystart och handlingskraft.

**Hur man undviker det:**  
Definiera vad som faktiskt är nytt: teknik, organisation, process, finansiering, ansvar eller målgrupp. Om gamla beroenden och ansvar fortfarande styr är det inte ren greenfield.

### Misstag: Att skapa pilot utan exitkriterier

**Varför det händer:**  
Fokus ligger på att komma igång, inte på vad som händer efter första framgången.

**Hur man undviker det:**  
Bestäm redan från början vilka kriterier som avgör om piloten ska skalas, ändras, integreras eller stoppas.

### Misstag: Att låta tekniker välja organisationsmodell indirekt

**Varför det händer:**  
Teknikbeslut känns konkreta, medan ansvar och styrning känns svårare.

**Hur man undviker det:**  
Separera teknikval från operativ modell. Låt ledningen fatta beslut om ansvar, mandat, risk och finansiering innan tekniken får definiera arbetssättet.

### Misstag: Att underskatta befintlig driftkunskap

**Varför det händer:**  
Driftorganisationen kan uppfattas som långsam eftersom den skyddar stabilitet och hanterar konsekvenserna av bristande kvalitet.

**Hur man undviker det:**  
Involvera drift tidigt i definitionen av operativa minimikrav, tjänsteklasser, incidentmodell och övervakning. Se driftkunskap som designinput, inte som slutgranskning.

### Misstag: Att tro att greenfield automatiskt skapar agilitet

**Varför det händer:**  
Nya verktyg, nya team och nya processer skapar en känsla av snabbhet.

**Hur man undviker det:**  
Pröva om snabbheten håller när säkerhetskrav, robusthetskrav, förvaltning, support och beroenden läggs till. Agilitet som bara fungerar i undantag är inte organisationsagilitet.

## Praktiskt beslutsstöd: beslutsmatris för vägvalet

Använd matrisen i ledningsgruppen innan vägvalet formuleras som projektbeslut. Den ska inte ge ett mekaniskt svar. Den ska synliggöra vilka villkor som behöver vara uppfyllda och vilka risker som måste ägas av ledningen.

| Kriterium | Greenfield talar starkast när... | Förändring i befintlig organisation talar starkast när... | Hybrid talar starkast när... | Ledningsrisk att hantera |
|---|---|---|---|---|
| Mandat | En ny satsning kan få tydligt mandat, egen prioritet och beslutskraft. | Befintliga funktioner redan har mandat att ändra arbetssätt. | Ett skyddat område behövs först, men normalisering är målet. | Oklart mandat skapar parallella beslut och ansvarsglapp. |
| Beroenden | Beroenden till befintliga system kan avgränsas i början. | Kritiska beroenden till exempelvis identitet, nät, MQ, databaser, loggning och incidentprocesser finns från dag ett. | Vissa beroenden kan avgränsas medan andra måste integreras tidigt. | Underskattade beroenden skapar integrationsskuld. |
| Risknivå | Piloten kan hållas inom låg eller kontrollerbar verksamhetsrisk. | Förändringen berör samhällskritiska flöden där avvikande modell vore riskabel. | Risk kan begränsas genom tydliga startvillkor och exitkriterier. | Risk flyttas från projektet till drift, säkerhet eller verksamhet utan beslut. |
| Kultur och arbetssätt | Gamla arbetssätt blockerar lärande och behöver tillfälligt rundas. | Organisationen behöver gemensam förändring mer än isolerad snabbhet. | Ett nytt arbetssätt behöver visas upp innan det breddas. | Greenfield blir “de nya” mot “de gamla”. |
| Kompetens | Det finns ett kärnteam med tillräcklig kompetens och kapacitet. | Kompetensen finns spridd i befintliga funktioner och behöver byggas gemensamt. | Kärnteamet kan bygga första versionen och samtidigt träna andra. | Nyckelpersonberoende gör satsningen svår att skala. |
| Finansiering | Det finns finansiering för både uppbyggnad och senare integration. | Långsiktig finansiering kräver att befintliga strukturer förändras. | Finansiering kan delas mellan lärande, produktifiering och normalisering. | Greenfield finansieras som projekt men behöver leva som produkt. |
| Styrning och säkerhet | Guardrails och inbyggda kontroller kan definieras från början. | Befintliga krav och kontrollmodeller måste moderniseras stegvis. | Nya kontroller provas i avgränsad miljö och görs sedan till standard. | Undantag blir praxis utan spårbar riskacceptans. |
| Tid till effekt | Snabbt lärande och synlig effekt är viktigare än bred täckning direkt. | Målet är bred effekt i ordinarie leveransflöde från början. | Snabb effekt behövs, men bara som första steg mot gemensam modell. | Ledningen misstar pilotframgång för organisationsförmåga. |

### Tre rekommenderade beslutstyper

Efter matrisen bör ledningen formulera vägvalet som ett av tre beslut.

**1. Greenfield med integrationsåtagande**  
Används när organisationen behöver fart och lärande, men bara om beslutet samtidigt anger hur lösningen ska kopplas tillbaka till ordinarie styrning, säkerhet, drift och finansiering.

**2. Brownfield med förändringsmandat**  
Används när beroenden och risker kräver att befintlig organisation förändras. Beslutet måste då ge mandat att ändra arbetssätt, inte bara införa ny teknik i gamla köer.

**3. Hybrid med tydliga grindar**  
Används när en skyddad start behövs, men där varje steg har villkor för breddning: vilka kontroller ska vara inbyggda, vilka team får ansluta, vilken supportmodell gäller och när ledningen omprövar beslutet.

Det sämsta alternativet är inte att välja fel modell. Det sämsta alternativet är att låta modellen uppstå av sig själv genom lokala initiativ, tillfälliga undantag och otydliga kompromisser.


## Övningar

### Övning 1: Bedöm ert vägval

Välj ett aktuellt eller tänkt plattformsinitiativ i din organisation. Besvara frågorna:

1. Vilka delar av initiativet är greenfield?
2. Vilka delar är brownfield?
3. Vilka befintliga beroenden kan inte väljas bort?
4. Finns det en integrationsplan?
5. Vilka beslut riskerar att skjutas upp genom vägvalet?

### Övning 2: Identifiera risken för parallell organisation

Tänk dig att en ny containerplattform byggs av ett separat team. Lista fem tecken på att satsningen håller på att bli en parallell organisation snarare än en kontrollerad väg mot gemensam plattformsförmåga.

Exempel på tecken kan vara egna undantagsregler, oklar finansiering, otydligt driftansvar eller att lärdomar inte återförs till huvudorganisationen.

### Fördjupning: Skriv ett ledningsbeslut

Formulera ett kort ledningsbeslut för en kombinerad väg. Beslutet bör innehålla:

- varför organisationen startar med ett skyddat område,
- vilka krav som är absoluta,
- vilka team eller tjänster som ingår först,
- vem som äger risk under piloten,
- när beslutet ska omprövas,
- hur lärdomar ska bli standard.

## Beslut att fatta

- Ska organisationen använda greenfield, stegvis förändring i befintlig organisation eller en kontrollerad hybrid?
- Vilket mandat får den nya lösningen, och hur undviks att den blir en isolerad sidostruktur?
- Vilka beroenden till befintliga system, dataflöden, säkerhetskrav och driftprocesser måste lösas innan vägvalet kan genomföras?

## Snabb sammanfattning

- Greenfield kan skapa tempo och lärande, men kräver tydliga ramar och integrationsplan.
- Brownfield ger bättre koppling till befintlig verklighet, men kräver mandat att faktiskt ändra arbetssätt.
- Den största risken är inte vägvalet i sig, utan att ledningen undviker svåra beslut om ansvar, risk, finansiering och normalisering.
- En parallell organisation uppstår när en ny satsning saknar plan för hur den ska kopplas till resten av organisationen.
- För många stora reglerade organisationer är en kombinerad väg bäst: skyddad start, kontrollerad breddning och planerad normalisering.
- Ledningen bör mäta förmågeförflyttning, inte bara teknikleverans.

## Ledningsfrågor

1. Vilken är den viktigaste skillnaden mellan greenfield och en parallell organisation?
2. Varför kan brownfield misslyckas även om det är mer förankrat?
3. Vilka beroenden i en stor reglerad organisation gör ren greenfield svår?
4. Vilka beslut måste ledningen fatta innan en pilot får växa?
5. Hur kan man mäta att ett vägval faktiskt bygger plattformsförmåga?

## Nästa steg

När vägvalet är gjort återstår en minst lika viktig fråga: hur hanterar organisationen det långa övergångsläget? De flesta stora organisationer kommer under flera år leva med både gamla och nya plattformar, både traditionella beställningsflöden och mer självservice, både etablerade driftkrav och nya automatiserade arbetssätt.

Nästa kapitel handlar därför om **övergångsläget: att leva med både gammalt och nytt**.
