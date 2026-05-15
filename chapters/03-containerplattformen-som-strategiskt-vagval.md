# Kapitel 3: Containerplattformen som strategiskt vägval

## Varför detta kapitel finns

När en organisation börjar tala om OpenShift, Kubernetes eller containerplattformar hamnar samtalet lätt i teknikspåret. Diskussionen kan snabbt handla om kluster, noder, namespaces, images, nätverk, lagring, certifikat, pipelines och verktygsval.

Allt detta är viktigt. Men för ledningen är den avgörande frågan en annan:

**Vilket strategiskt vägval gör vi när vi inför en containerplattform?**

En containerplattform är inte bara en ny plats att köra applikationer på. Den förändrar gränsen mellan utveckling och drift. Den påverkar hur säkerhet byggs in. Den skapar nya krav på standardisering. Den kräver nya kompetenser. Den gör vissa beslut mer decentraliserade och andra mer centrala. Den kan ge snabbare leveranser, men bara om organisationen samtidigt förändrar arbetssätt, ansvar och styrning.

Det här kapitlet hjälper dig som chef att se containerplattformen som ett ledningsbeslut, inte bara som ett teknikprojekt. Poängen är inte att du ska kunna administrera plattformen. Poängen är att du ska förstå vilka organisatoriska konsekvenser plattformen får, vilka beslut som inte bör delegeras för långt ner och vilka risker som uppstår om tekniken införs utan en tydlig operativ modell.

## Lärandemål

Efter kapitlet ska du kunna:

- beskriva varför en containerplattform är ett strategiskt vägval och inte enbart en teknisk komponent,
- skilja mellan containerplattform som infrastruktur, som intern produkt och som förändringsmotor,
- identifiera vilka chefsbeslut som krävs innan plattformen kan skapa verklig nytta,
- känna igen vanliga missförstånd vid införande av OpenShift-liknande plattformar,
- formulera de viktigaste frågorna ledningen behöver besvara innan organisationen skalar upp användningen.

## Innan vi börjar

I kapitel 2 definierade vi målbilden som **agil förmåga på organisationsnivå**. Vi introducerade också begreppen **organisationsagilitet**, **förändringskapacitet** och **styrbar snabbhet**.

Detta kapitel tar nästa steg: om containerplattformen ska bidra till den målbilden behöver den förstås som mer än teknik. Annars riskerar organisationen att köpa eller bygga en modern plattform, men använda den med samma gamla beställningsflöden, samma oklara mandat och samma sena kontrollpunkter.

## Tre begrepp för det strategiska vägvalet

Det här kapitlet introducerar tre huvudbegrepp: **containerplattform**, **strategisk plattform** och **operativ modell**.

### Containerplattform

En containerplattform är en teknisk plattform för att köra, hantera och drifta containerbaserade applikationer.

I praktiken kan det handla om en OpenShift-liknande miljö där applikationer paketeras som containrar och körs på en gemensam plattform. Plattformen kan erbjuda funktioner för driftsättning, skalning, nätverk, åtkomst, loggning, övervakning, säkerhetskontroller och integration med CI/CD.

För en teknisk målgrupp är detta en ganska naturlig definition. För ledningen räcker den inte.

Ledningsfrågan är inte bara: “Kan vi köra containrar?”

Ledningsfrågan är: “Vilken typ av leveransförmåga vill vi bygga med hjälp av containerplattformen?”

Det är skillnaden mellan att se plattformen som en teknisk resurs och att se den som en organisatorisk förmåga.

### Strategisk plattform

En strategisk plattform är en plattform som organisationen medvetet använder för att förändra hur leverans, styrning, säkerhet och drift fungerar.

Den är strategisk därför att den påverkar flera delar av organisationen samtidigt. Den är inte bara ett tekniskt alternativ bland andra. Den blir en del av organisationens sätt att styra förändring.

En containerplattform blir strategisk när ledningen använder den för att:

- standardisera återkommande tekniska mönster,
- minska behovet av specialbeställningar,
- flytta kontroller tidigare i leveransflödet,
- skapa mer självservice inom tydliga ramar,
- göra driftsättning mer förutsägbar,
- öka spårbarhet och återanvändning,
- skapa gemensamma spelregler mellan utveckling, drift och säkerhet.

Men en plattform blir inte strategisk bara för att den är tekniskt avancerad. Den blir strategisk när organisationen fattar beslut om hur den ska användas, finansieras, styras och vidareutvecklas.

### Operativ modell

En operativ modell beskriver hur organisationen ska arbeta runt plattformen i vardagen.

Den svarar på frågor som:

- Vem äger plattformens riktning?
- Vem prioriterar plattformens backlog?
- Vem ansvarar för säkerhetskrav i plattformen?
- Vem får skapa eller ändra miljöer?
- Vilka val får utvecklingsteam göra själva?
- Vilka val är standardiserade?
- Vilka kontroller är automatiserade?
- Vilka ärenden måste fortfarande hanteras manuellt?
- Hur följs kostnad, kapacitet, incidenter och risk upp?
- Hur hanteras undantag?

Utan en operativ modell blir containerplattformen lätt ännu en teknisk miljö som organisationen måste beställa, samordna och tolka. Då kan den skapa mer komplexitet istället för mindre.

## Scenariot: beslutet hos Myndigheten för Samhällstjänst

Hos Myndigheten för Samhällstjänst har ledningen beslutat att organisationen ska börja använda en OpenShift-liknande containerplattform. Argumenten är välkända: snabbare leveranser, modernare applikationsdrift, bättre stöd för automatisering, enklare standardisering och bättre möjlighet att ge utvecklingsteamen självservice.

Utvecklingscheferna ser plattformen som en möjlighet att minska väntetider. De vill att teamen ska kunna skapa fler tekniska förutsättningar själva, särskilt i utvecklings- och testmiljöer.

Driftcheferna ser både möjligheter och risker. De förstår att plattformen kan minska manuella moment, men de är också oroliga för att ansvaret för produktion, incidenter, kapacitet och robusthet blir otydligare.

Säkerhetschefen välkomnar möjligheten att bygga in kontroller tidigare, men vill inte att plattformen blir ett sätt att kringgå etablerade krav. Säkerhetsteamet vill veta hur behörigheter, spårbarhet, sårbarhetshantering, nätverksregler och undantag ska fungera.

Förvaltningsledningen frågar hur plattformen passar ihop med befintliga system på JBoss EAP, integrationer via IBM MQ, data i Oracle, sökfunktioner i Elasticsearch och lagring i Ceph. Alla nya tjänster kan inte flytta samtidigt. Under flera år kommer gammalt och nytt att behöva samexistera.

Alla är positiva till någon del av förändringen. Samtidigt är ingen helt trygg med helheten.

Det är just här containerplattformen blir ett strategiskt vägval. Tekniken är bara en del av beslutet. Det verkliga beslutet handlar om vilken typ av organisation Myndigheten för Samhällstjänst vill bli.

## Tre sätt att se på containerplattformen

Ledningen behöver vara medveten om att samma plattform kan förstås på minst tre olika sätt.

### 1. Plattformen som ny infrastruktur

Det första synsättet är att plattformen är ny infrastruktur. Då blir huvudfrågorna tekniska:

- Hur designas klustren?
- Hur kopplas nätverk och lagring?
- Hur hanteras åtkomst?
- Hur övervakas plattformen?
- Hur säkras driften?
- Hur integreras den med befintliga verktyg?

Detta synsätt är nödvändigt. Utan stabil teknisk grund kommer plattformen inte att fungera.

Men det är otillräckligt. Om plattformen bara behandlas som ny infrastruktur riskerar organisationen att behålla samma ärendeflöden som tidigare. Utvecklingsteamen beställer fortfarande. Drift tolkar och genomför. Säkerhet granskar i efterhand. Ledningen undrar varför nyttan inte kommer.

Då har organisationen moderniserat teknikytan, men inte leveransmodellen.

### 2. Plattformen som intern produkt

Det andra synsättet är att plattformen är en intern produkt.

Då blir frågorna annorlunda:

- Vilka användare har plattformen?
- Vilka problem ska den lösa för dem?
- Vilka tjänster ska erbjudas som standard?
- Vad ingår och vad ingår inte?
- Hur ser plattformens roadmap ut?
- Hur prioriteras nya förmågor?
- Hur mäts användbarhet, kvalitet och nytta?
- Hur samlas feedback från utveckling, drift och säkerhet?

Detta synsätt är kraftfullt därför att det flyttar fokus från teknikdrift till värdeskapande. Plattformsteamet blir inte bara en mottagare av beställningar. Det blir en produktorganisation som utvecklar en intern tjänst.

För ledningen innebär det att plattformen behöver produktägarskap, finansiering, prioriteringsprinciper och tydliga mål. En intern produkt utan mandat och finansiering blir lätt en teknisk ö utan utvecklingskraft.

### 3. Plattformen som förändringsmotor

Det tredje synsättet är att plattformen är en förändringsmotor.

Då är plattformens viktigaste effekt inte bara att applikationer körs på ett nytt sätt. Effekten är att organisationen tvingas bli tydligare med ansvar, standarder, automatisering och styrning.

Plattformen kan göra det svårare att gömma gamla otydligheter. Den synliggör frågor som tidigare kunde lösas informellt:

- Vad är ett godkänt sätt att driftsätta?
- Vilka säkerhetskrav gäller alltid?
- Vem äger produktionsincidenten när teamet själv har driftsatt?
- Vilka standarder får team avvika från?
- Vem betalar för kapacitet?
- Vem prioriterar plattformsförbättringar framför enskilda teambehov?
- Hur hanteras system som inte passar plattformens standardmönster?

Detta kan upplevas obekvämt. Men det är också värdet. En strategisk plattform gör ledningens målkonflikter synliga tidigare.

## Det vanligaste ledningsmisstaget: att tro att teknikvalet är beslutet

Ett vanligt misstag är att ledningen tror att det stora beslutet är att välja plattform. När valet väl är gjort tänker man att förändringen främst är en fråga för teknikorganisationen.

Det är sällan tillräckligt.

Teknikvalet är bara ett av flera beslut. Minst lika viktiga är besluten om operativ modell, ansvar, finansiering och styrning.

Om dessa beslut saknas kan plattformen leda till nya målkonflikter:

- Utvecklingsteam får nya verktyg men inte mandat att använda dem fullt ut.
- Drift får ansvar för stabilitet men inte tillräcklig kontroll över hur tjänster byggs och driftsätts.
- Säkerhet får ansvar för risk men kommer in för sent för att påverka standarder.
- Plattformsteamet får förväntningar på snabb leverans men ingen tydlig produktprioritering.
- Ledningen förväntar sig agilare arbetssätt men behåller styrsignaler som premierar manuell kontroll och sena godkännanden.

Då kan containerplattformen bli en symbol för modernisering utan att organisationens faktiska förändringskapacitet ökar.

## Vad förändras när plattformen införs?

För ledningen är det viktigt att förstå vilka organisatoriska områden som påverkas. Här är fem förändringar som ofta underskattas.

### 1. Ansvar flyttas närmare teamen

Containerplattformar och CI/CD gör det möjligt för utvecklingsteam att ta större ansvar för paketering, konfiguration och driftsättning. Det kan vara positivt, men bara om ansvarsförändringen är avsiktlig.

Om team får större frihet utan tydliga ramar kan riskerna öka. Om teamen däremot inte får mer handlingsutrymme blir plattformen långsammare än den behöver vara.

Ledningsfrågan blir därför:

**Vilket ansvar ska flyttas närmare teamen, och vilka krav måste vara uppfyllda för att det ska vara acceptabelt?**

Svaret behöver vara olika för olika miljöer. Det som är rimligt i utveckling är inte alltid rimligt i produktion. Det som är rimligt för ett moget team är inte alltid rimligt för ett nytt team. Men utan principer blir varje fall en ny förhandling.

### 2. Driftens roll förändras

Driftorganisationen försvinner inte för att en containerplattform införs. Däremot förändras driftens roll.

I ett traditionellt beställningsflöde kan drift ofta vara den funktion som genomför många förändringar. I en mer automatiserad plattformsmodell behöver drift i större utsträckning designa, standardisera, övervaka, förbättra och säkra den operativa helheten.

Det kan innebära mindre manuell handpåläggning, men mer ansvar för:

- plattformens stabilitet,
- standardiserade driftsmönster,
- incidentförmåga,
- kapacitet,
- övervakning,
- återställning,
- operativa minimikrav,
- kontinuerlig förbättring av plattformstjänster.

Detta är inte en nedgradering av driftens roll. Det är en förflyttning från utförare av enskilda beställningar till medskapare av organisationens leveransförmåga.

### 3. Säkerhet behöver byggas in tidigare

I ett beställningsorienterat arbetssätt kan säkerhet ofta hamna i riktlinjer, granskningar och kontrollpunkter. I en containerplattform behöver fler säkerhetskrav översättas till standarder, automatiserade kontroller och godkända mönster.

Det innebär inte att säkerhetsteamet tappar ansvar. Tvärtom behöver säkerhetsfunktionen bli tydligare med vilka krav som är absoluta, vilka som kan hanteras genom riskacceptans och vilka som kan byggas in i plattform och pipeline.

Ledningens uppgift är att säkerställa att säkerhetsteamet får mandat och tid att arbeta med plattformsdesign, inte bara med granskning av enskilda initiativ.

### 4. Finansieringsmodellen blir viktigare

En containerplattform kräver långsiktig produktutveckling. Den behöver inte bara byggas. Den behöver förvaltas, förbättras, säkras, dokumenteras, supporteras och anpassas efter användarnas behov.

Om plattformen finansieras som ett införandeprojekt men förväntas fungera som en långsiktig intern produkt uppstår ett glapp. Plattformsteamet kan få ansvar utan kapacitet. Utvecklingsteamen kan få förväntningar utan fungerande självservice. Ledningen kan få kostnader utan tydlig prioritering.

Ledningsfrågan är därför:

**Är plattformen finansierad som en varaktig förmåga eller som ett tidsbegränsat projekt?**

### 5. Standardisering blir en ledningsfråga

Självservice kräver standardisering. Det går inte att automatisera allt om varje team, system och miljö ska hanteras som ett specialfall.

Det betyder inte att alla applikationer måste bli likadana. Men organisationen behöver besluta vilka delar som ska vara gemensamma:

- miljötyper,
- säkerhetsnivåer,
- loggning,
- övervakning,
- nätverksmönster,
- bygg- och deploymönster,
- incidentkrav,
- backup och återställning,
- namngivning och spårbarhet,
- godkända integrationsmönster.

Standardisering kan upplevas som begränsande. Men rätt standardisering minskar onödiga beslut och frigör energi till det som verkligen behöver vara unikt.

## Ledningens minsta beslutspaket

Innan en organisation skalar upp användningen av containerplattformen bör ledningen ha ett minsta beslutspaket. Det behöver inte vara perfekt, men det behöver vara tydligt nog för att undvika att varje fråga löses lokalt.

### Beslut 1: Varför inför vi plattformen?

Ledningen behöver kunna uttrycka plattformens syfte på ett sätt som är bredare än teknik.

Exempel på en svag formulering:

> Vi ska införa OpenShift för att modernisera vår applikationsplattform.

Exempel på en starkare formulering:

> Vi ska bygga en containerbaserad plattformsförmåga som gör det möjligt att leverera förändringar oftare, med högre grad av standardisering, inbyggda kontroller och tydligare ansvar mellan utveckling, drift och säkerhet.

Den andra formuleringen gör det tydligt att plattformen är kopplad till arbetssätt och ansvar.

### Beslut 2: Vilka användare ska plattformen först optimera för?

Alla behov kan inte lösas samtidigt. Ledningen behöver bestämma vilka användargrupper och användningsfall som kommer först.

Det kan vara:

- nya digitala tjänster med hög förändringstakt,
- utvecklings- och testmiljöer,
- applikationer med tydlig containerpassning,
- team med hög teknisk mognad,
- tjänster där nuvarande beställningsflöde skapar stora ledtider,
- system där säkerhets- och driftkrav kan standardiseras tidigt.

Utan prioritering riskerar plattformen att försöka vara allt för alla och bli otydlig för de viktigaste användarna.

### Beslut 3: Vilken grad av självservice är acceptabel?

Självservice är inte ett ja eller nej. Det är en skala.

Ledningen behöver besluta vad team får göra själva i olika miljöer och under vilka villkor. Exempel:

- skapa utvecklingsmiljöer,
- driftsätta till test,
- begära standardiserade integrationer,
- ändra konfiguration inom godkända ramar,
- skala resurser,
- läsa loggar och mätdata,
- initiera återställning i icke-produktionsmiljö,
- driftsätta till produktion efter automatiserade kontroller.

Beslutet behöver kopplas till krav på spårbarhet, behörighet, testning, godkända mallar och incidentansvar.

### Beslut 4: Vilka kontroller ska byggas in?

Om organisationen vill ha snabbare flöden behöver vissa kontroller flyttas från manuella granskningar till inbyggda mekanismer.

Det kan handla om:

- krav på godkända container images,
- sårbarhetsskanning,
- behörighetsstyrning,
- nätverkspolicyer,
- resursgränser,
- loggningskrav,
- godkända deploymönster,
- spårbarhet från kod till produktion,
- policykontroller i pipeline,
- standardiserad konfiguration.

Ledningen behöver inte utforma alla kontroller. Men ledningen behöver besluta att inbyggda kontroller är en strategisk riktning och säkerställa att ansvariga funktioner har mandat att skapa dem.

### Beslut 5: Hur ska plattformen ägas och finansieras?

Plattformen behöver ett tydligt ägarskap. Någon måste prioritera mellan användarnas behov, säkerhetskrav, driftförbättringar, teknisk skuld och framtida förmågor.

Det räcker inte med att säga att “IT äger plattformen”. Ledningen behöver veta:

- vem som är produktägare eller motsvarande,
- vilket forum som prioriterar större vägval,
- hur drift, säkerhet och utveckling representeras,
- hur kostnader fördelas,
- hur kapacitet planeras,
- hur plattformens roadmap beslutas,
- hur plattformens nytta följs upp.

Detta blir särskilt viktigt i stora reglerade organisationer där flera delar av organisationen kan ha legitima men konkurrerande behov.

## Vad ska inte läggas på plattformen för tidigt?

En vanlig risk är att plattformen överlastas med förväntningar. Den förväntas lösa leveranshastighet, standardisering, säkerhet, kostnadskontroll, legacyproblem, kompetensbrist och organisationsfriktion på samma gång.

Det är för mycket.

Ledningen behöver vara tydlig med vad plattformen inte ska lösa i första steget.

Exempel på sådant som kan behöva vänta:

- de mest komplexa legacyapplikationerna,
- verksamhetskritiska system utan tydlig återställningsmodell,
- applikationer med oklara ägarskap,
- system där tekniska beroenden inte är kartlagda,
- specialfall som kräver många undantag från standard,
- migrationer där nyttan är låg men risken hög,
- produktionssjälvservice innan operativa minimikrav är etablerade.

Detta är inte ett argument för att undvika svåra frågor. Det är ett argument för sekvensering. En strategisk plattform byggs genom medvetna steg, inte genom att allt flyttas samtidigt.

## Vanliga misstag

### Misstag: Att införa plattformen som ett isolerat teknikprojekt

**Varför det händer:**  
Teknikval och plattformsuppbyggnad är konkreta, mätbara och ofta lättare att organisera än förändring av ansvar och styrning.

**Hur man undviker det:**  
Koppla plattformsinförandet till en beslutad målbild för leveransförmåga. Sätt upp ett ledningsforum där utveckling, drift, säkerhet, arkitektur och förvaltning hanterar ansvar, prioriteringar och målkonflikter.

### Misstag: Att lova självservice utan att definiera ramar

**Varför det händer:**  
Självservice låter som en enkel lösning på långa beställningsflöden. Men utan tydliga ramar blir självservice lätt otydlig eller riskfylld.

**Hur man undviker det:**  
Beskriv självservice som frihet inom godkända ramar. Definiera vad som får göras, av vem, i vilken miljö, med vilka kontroller och med vilket ansvar.

### Misstag: Att underskatta driftens nya roll

**Varför det händer:**  
Det kan låta som att automatisering minskar behovet av drift. I praktiken förändras driftens arbete från manuell handpåläggning till design av robusta operativa mönster.

**Hur man undviker det:**  
Ge driftorganisationen en central roll i att definiera operativa minimikrav, övervakning, incidentflöden, kapacitetsstyrning och återställningsförmåga.

### Misstag: Att involvera säkerhet för sent

**Varför det händer:**  
Säkerhet behandlas ofta som granskning snarare än designpartner. Då kommer säkerhetskrav in när lösningen redan är formad.

**Hur man undviker det:**  
Låt säkerhetsteamet vara med och definiera standardmönster, kontroller, behörighetsmodeller och undantagshantering från början.

### Misstag: Att försöka migrera för mycket för tidigt

**Varför det händer:**  
När en ny plattform är strategiskt viktig uppstår press att visa snabb nytta. Då kan organisationen välja för många eller för komplexa första användningsfall.

**Hur man undviker det:**  
Välj användningsfall som både ger synlig nytta och är rimligt standardiserbara. Spara de svåraste legacyfallen tills operativ modell, kompetens och grundförmågor är stabilare.

## Övningar

### Övning 1: Formulera plattformens strategiska syfte

Skriv först organisationens nuvarande tekniska formulering av plattformsinitiativet. Den kan till exempel börja med:

> Vi inför en containerplattform för att ...

Skriv sedan om formuleringen så att den beskriver organisatorisk förmåga. Använd gärna orden:

- förändringskapacitet,
- styrbar snabbhet,
- standardisering,
- inbyggda kontroller,
- ansvar,
- självservice,
- robusthet.

Jämför de två formuleringarna. Vilken hjälper ledningen att fatta beslut?

### Övning 2: Identifiera beslut som saknas

Gå igenom följande frågor och markera dem som:

- beslutad,
- delvis beslutad,
- otydlig,
- inte beslutad.

Frågor:

1. Vem äger plattformens riktning?
2. Vem prioriterar plattformens backlog?
3. Vilka team är första målgrupp?
4. Vilka tjänster ska erbjudas som självservice?
5. Vilka kontroller ska vara automatiserade?
6. Vilka miljöer omfattas av självservice i första steget?
7. Vilka operativa minimikrav gäller?
8. Hur finansieras plattformens vidareutveckling?
9. Hur hanteras undantag?
10. Vilka mätetal visar att plattformen skapar nytta?

Välj de tre mest kritiska otydligheterna och lyft dem till ledningsdiskussion.

### Övning 3: Bedöm första användningsfallen

Välj tre möjliga användningsfall för containerplattformen.

För varje användningsfall, bedöm:

- verksamhetsnytta,
- teknisk lämplighet,
- säkerhetsrisk,
- driftkomplexitet,
- beroenden till befintliga plattformar,
- teamets mognad,
- möjlighet att standardisera,
- synlighet för ledningen.

Välj inte automatiskt det mest synliga användningsfallet. Välj det användningsfall som bäst hjälper organisationen att lära sig rätt saker.

## Beslut att fatta

- Ska containerplattformen behandlas som ett teknikinförande eller som en strategisk förändring av leveransmodellen?
- Vilka ansvar flyttas när plattformen införs, och vilka ansvar ska uttryckligen ligga kvar?
- Vilka förmågor måste finansieras långsiktigt för att plattformen inte ska bli ännu en teknisk ö utan organisatorisk effekt?

## Snabb sammanfattning

- En containerplattform är inte bara ny teknik. Den är ett strategiskt vägval som påverkar ansvar, styrning, kompetens och finansiering.
- Plattformen kan ses som infrastruktur, intern produkt och förändringsmotor. Ledningen behöver förstå alla tre perspektiven.
- Teknikvalet är inte det viktigaste beslutet. Den operativa modellen avgör om plattformen skapar verklig leveransförmåga.
- Självservice kräver tydliga ramar, automatiserade kontroller och standardiserade mönster.
- Driftens och säkerhetens roller försvinner inte. De förändras och behöver komma in tidigare i designen av plattformsförmågan.
- Plattformen bör finansieras och styras som en långsiktig intern produkt, inte bara som ett införandeprojekt.
- Ledningen behöver välja första användningsfall med omsorg. Fel första fall kan skapa motstånd, risk och felaktiga slutsatser.

## Ledningsfrågor

1. På vilket sätt är en containerplattform ett strategiskt vägval i er organisation?
2. Ser ni i dag plattformen främst som infrastruktur, intern produkt eller förändringsmotor?
3. Vilka beslut om ansvar och styrning är fortfarande otydliga?
4. Vilken grad av självservice är rimlig i utveckling, test och produktion?
5. Vilka säkerhets- och driftkontroller behöver byggas in innan självservice kan skalas?
6. Vilka användningsfall bör inte flyttas till plattformen i första steget?
7. Hur ska ledningen veta att plattformen faktiskt ökar förändringskapaciteten?

## Nästa steg

Nästa kapitel går från plattformen som strategiskt vägval till plattformen som intern produkt. Vi kommer att titta på hur organisationen kan gå från miljöbeställningar till plattformsprodukter, och varför det förändrar relationen mellan utvecklingsteam, drift, säkerhet och plattformsteam.
