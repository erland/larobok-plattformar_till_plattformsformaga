# Kapitel 4: Från miljöbeställningar till plattformsprodukter

## Varför detta kapitel finns

I många större organisationer har miljöer länge hanterats som beställningar. Ett utvecklingsteam behöver en ny testmiljö, en ändring i en integrationsmiljö, en justering av kapacitet eller en ny koppling till en gemensam tjänst. Teamet formulerar ett ärende. Driftorganisationen tolkar, kompletterar, koordinerar, kvalitetssäkrar och utför. Säkerhet och arkitektur kan behöva ge synpunkter. Vid större förändringar tillkommer ofta särskilda koordineringsforum.

Det här arbetssättet har vuxit fram av goda skäl. Det ger kontroll. Det skapar ansvarspunkter. Det minskar risken att enskilda team gör förändringar som påverkar gemensamma miljöer negativt.

Men när organisationen vill öka sin förändringskapacitet blir beställningsflödet ofta en begränsning. Inte för att någon gör fel, utan för att modellen bygger på att återkommande behov behandlas som individuella ärenden. Varje beställning behöver tolkas. Varje undantag kräver dialog. Varje missförstånd skapar omtag. Varje oklarhet hamnar hos människor som redan ansvarar för stabil drift.

Om containerplattformen ska ge verklig effekt behöver ledningen därför ställa en ny fråga:

**Vilka återkommande behov ska inte längre vara beställningar, utan erbjudas som interna plattformsprodukter?**

Det här kapitlet visar hur organisationen kan gå från ärendestyrda miljöbeställningar till produktifierade plattformstjänster. Fokus ligger inte på att avskaffa all beställning eller all manuell kontroll. Fokus ligger på att avgöra vad som bör standardiseras, vem som ska äga erbjudandet och hur självservice kan införas utan att säkerhet, robusthet och kvalitet blir frivilliga tillval.

## Lärandemål

Efter kapitlet ska du kunna:

- förklara skillnaden mellan ett beställningsflöde och en intern plattformsprodukt,
- beskriva vad *platform engineering* betyder i en ledningskontext,
- avgöra vilka behov som lämpar sig för självservice och vilka som fortfarande kräver manuell prövning,
- identifiera vilka ansvar som krävs för att en plattformstjänst ska fungera som produkt,
- formulera ledningsbeslut som minskar spretiga beställningar utan att centralisera all förändring.

## Innan vi börjar

I kapitel 3 såg vi att en containerplattform inte bara är teknik. Den behöver en **operativ modell**: ett tydligt sätt att beskriva ansvar, prioritering, kontroller och vardagligt arbete runt plattformen.

Det här kapitlet gör den operativa modellen mer konkret. Om plattformen ska användas strategiskt behöver den erbjuda tjänster som utvecklingsteam faktiskt kan använda, förstå och lita på. Det räcker inte att plattformen finns tekniskt. Den måste paketeras som ett internt erbjudande.

## Tre begrepp: platform engineering, självservice och intern produkt

Det här kapitlet introducerar tre huvudbegrepp: **platform engineering**, **självservice** och **intern produkt**.

### Platform engineering

*Platform engineering* är ett arbetssätt där organisationen bygger och förvaltar en intern plattform som en produkt för utvecklingsteam och andra interna användare.

Det betyder inte att driftorganisationen bara byter namn. Det betyder att plattformsförmågan får ett tydligt produktperspektiv:

- vilka användare plattformen finns till för,
- vilka återkommande behov den ska lösa,
- vilka tjänster som erbjuds,
- vilka krav som är inbyggda,
- hur användarna beställer, konfigurerar eller använder tjänsterna,
- hur förbättringar prioriteras,
- hur kvalitet och användbarhet följs upp.

I en ledningskontext är *platform engineering* framför allt ett sätt att styra bort från otydliga engångsbeställningar. Målet är inte att göra utvecklingsteam helt oberoende av drift, säkerhet och arkitektur. Målet är att göra rätt väg så tydlig, snabb och säker att den blir den naturliga vägen.

### Självservice

Självservice betyder att team kan utföra standardiserade åtgärder själva inom definierade ramar, utan manuell handpåläggning från varje stödfunktion.

Det kan till exempel vara att:

- skapa ett nytt namespace eller projektområde,
- välja en godkänd applikationsmall,
- ansluta till loggning och övervakning,
- beställa en standardiserad testmiljö,
- driftsätta via en godkänd pipeline,
- konfigurera vissa resurser inom fastställda gränser,
- hämta godkända byggblock för säkerhet, certifikat, hemligheter eller nätverksåtkomst.

Självservice ska inte förväxlas med frihet utan ansvar. I en reglerad organisation bör självservice snarare betyda: **frihet inom fördefinierade, spårbara och godkända ramar**.

Det är därför självservice måste byggas tillsammans med säkerhet, drift och arkitektur. Om självservice bara blir ett sätt att gå runt etablerade kontroller skapas ny risk. Om självservice däremot bygger in kontrollerna i mallar, pipelines och plattformstjänster kan organisationen både öka tempo och förbättra efterlevnad.

### Intern produkt

En intern produkt är en tjänst eller förmåga som erbjuds inom organisationen med tydlig målgrupp, ansvarig ägare, definierat värde, livscykel och prioriterad utveckling.

Skillnaden mot en teknisk komponent är viktig. En komponent kan finnas utan att någon aktivt ansvarar för användarupplevelse, roadmap, dokumentation, support och mätning. En produkt behöver däremot förvaltas med användarnas behov i centrum.

En intern plattformsprodukt kan till exempel vara:

- “standardiserad utvecklingsmiljö för containerbaserade applikationer”,
- “godkänd pipeline för produktionssättning”,
- “mall för Java-baserad tjänst med loggning, övervakning och säkerhetskontroller”,
- “självservice för testmiljö med fördefinierade resursnivåer”,
- “anslutning till meddelandekö enligt godkända mönster”,
- “standardiserad väg för applikationer som behöver Oracle-koppling”.

Ledningspoängen är att en intern produkt behöver mandat och finansiering. Den kan inte bara vara ett sidouppdrag för personer som samtidigt förväntas hantera alla akuta driftfrågor.


## Exempel: en intern plattformsprodukt

En intern plattformsprodukt behöver vara konkret nog för att utvecklingsteam ska förstå vad de får, och tydlig nog för att drift, säkerhet och ledning ska förstå vilket ansvar som följer med erbjudandet.

Ett exempel hos **Myndigheten för Samhällstjänst** kan vara:

**Standardiserad applikationsyta för containerbaserade tjänster**

Produkten riktar sig till utvecklingsteam som vill köra en ny eller moderniserad tjänst på containerplattformen. Den erbjuder:

- en godkänd grundmall för applikationsyta,
- standardiserad pipeline för bygg, test och driftsättning,
- fördefinierade resursgränser,
- obligatorisk loggning och övervakning,
- säker hantering av hemligheter,
- godkända basavbildningar,
- koppling till incident- och supportmodell,
- dokumenterad väg för undantag.

Det viktiga är inte att alla detaljer är automatiserade från första dagen. Det viktiga är att erbjudandet har ett tydligt löfte: **om teamet håller sig inom dessa ramar kan det gå snabbare, med mindre manuell koordinering och med bibehållen kontroll**.

Samma produkt behöver också ha gränser. Den kanske inte gäller för system med särskilt höga skyddsvärden, komplexa integrationer mot äldre databaser eller tjänster med särskilda krav på tillgänglighet. Då krävs en annan nivå av prövning.

Ledningens poäng med en sådan produkt är att göra standardvägen attraktiv. Utveckling får en snabbare väg framåt. Drift får färre spretiga beställningar. Säkerhet får inbyggda kontroller. Ledningen får bättre spårbarhet över vad som faktiskt används.

## Beställningsflödets styrkor och begränsningar

Det är lätt att beskriva beställningsflödet som gammaldags. Det vore fel. Beställningsflödet har flera styrkor, särskilt i organisationer med höga krav på säkerhet och tillgänglighet.

Det skapar kontrollpunkter. Det gör det möjligt att granska större förändringar. Det ger driftorganisationen insyn i vad som är på väg in. Det kan minska risken för att utvecklingsteam gör lokala lösningar som påverkar gemensam stabilitet. Det ger också säkerhet och arkitektur möjlighet att agera innan förändringar når produktion.

Problemet uppstår när nästan allt behandlas som om det vore unikt.

När återkommande behov hanteras som enskilda beställningar får organisationen flera typiska symptom:

- beställningar blir spretiga eftersom teamen beskriver behov på olika sätt,
- driftorganisationen behöver tolka och komplettera ärenden,
- kvalitetssäkring sker sent och ofta manuellt,
- utvecklingsteam upplever väntan även för standardbehov,
- säkerhetsteamet får granska variationer i stället för att definiera återanvändbara krav,
- ledningen får svårt att se vilka behov som egentligen är återkommande,
- förbättringar sker lokalt i skript och rutiner snarare än i ett gemensamt erbjudande.

Ett beställningsflöde är alltså inte dåligt i sig. Det är dåligt lämpat för sådant som borde vara standardiserat.

## Från ärende till erbjudande

Skiftet från miljöbeställningar till plattformsprodukter kan beskrivas som ett skifte från ärende till erbjudande.

I ett ärendeflöde börjar arbetet ofta med frågan:

**“Vad vill teamet beställa?”**

I en produktmodell börjar arbetet med en annan fråga:

**“Vilka återkommande behov ska plattformen lösa på ett standardiserat sätt?”**

Det förändrar ledningens fokus. I stället för att bara förbättra handläggningstiden för beställningar behöver ledningen skapa förutsättningar för att färre saker behöver handläggas manuellt.

Det betyder att organisationen behöver identifiera sina vanligaste behov. Vilka typer av miljöer beställs ofta? Vilka ändringar återkommer? Vilka krav behöver alltid kontrolleras? Vilka integrationsmönster återkommer? Vilka applikationstyper är vanligast? Vilka steg i kvalitetssäkringen görs gång på gång?

När dessa mönster blir synliga kan de paketeras.

En återkommande miljöbeställning kan bli en självservicemall. En återkommande säkerhetskontroll kan bli en pipelinekontroll. En återkommande driftstandard kan bli en plattformspolicy. En återkommande dokumentationsfråga kan bli en del av onboardingflödet. En återkommande arkitekturprincip kan bli ett godkänt byggblock.

Det är här plattformsprodukten börjar skapa effekt.

## Scenario: Myndigheten för Samhällstjänst

På Myndigheten för Samhällstjänst har utvecklingsteamen länge beställt miljöförändringar via etablerade ärendeflöden. Vissa beställningar är enkla, andra kräver koordinering mellan drift, säkerhet, nätverk, databasteam och applikationsförvaltning.

Driftorganisationen upplever att många beställningar är ofullständiga. Ibland saknas resursbehov. Ibland är beroenden oklara. Ibland har teamen utgått från att en lösning är standard trots att den kräver undantag. Driften lägger därför mycket tid på att tolka, komplettera och kvalitetssäkra.

Utvecklingsteamen upplever samma situation på ett annat sätt. De tycker att de ofta beställer liknande saker. De ser att vissa moment redan automatiseras med skript. De har pipelines för applikationsleveranser när miljön väl är på plats. De frågar sig varför de inte kan få mer självservice.

Säkerhetsteamet har ytterligare ett perspektiv. De ser risker i ökad självservice om det innebär att team själva kan skapa osäkra konfigurationer. Samtidigt ser de att manuell granskning av varje variation inte skalar.

Ledningen inser att konflikten inte handlar om att någon funktion är ovillig. Problemet är att organisationen saknar ett gemensamt erbjudande för återkommande behov.

Ledningens strategiska fråga blir därför:

**Vilka miljö- och plattformstjänster ska Myndigheten för Samhällstjänst produktifiera först?**

Ett möjligt första svar är att börja med de vanligaste och minst riskfyllda behoven:

- standardiserade utvecklings- och testmiljöer,
- godkända applikationsmallar,
- grundläggande loggning och övervakning,
- resursnivåer med tydliga gränser,
- standardiserad pipeline för icke-produktionsmiljöer,
- tydlig onboarding för team som ska använda containerplattformen.

Detta löser inte alla problem. Men det skapar en ny riktning. I stället för att försöka automatisera varje individuell beställning börjar organisationen bygga ett återanvändbart erbjudande.

## Vad ska bli självservice?

Alla behov ska inte bli självservice. Ett vanligt ledningsmisstag är att göra självservice till en ideologisk fråga: antingen ska team få göra allt själva, eller så ska nästan inget förändras.

En mer användbar fråga är:

**Vilka beslut kan standardiseras så väl att de kan delegeras till plattformen?**

Självservice passar bäst när behovet är återkommande, väl förstått, lågrisk eller medelrisk, möjligt att begränsa tekniskt och möjligt att följa upp automatiskt.

Självservice passar sämre när behovet är ovanligt, påverkar kritiska beroenden, kräver ny riskbedömning, förändrar gemensam arkitektur eller innebär undantag från etablerade krav.

Det betyder att organisationen kan arbeta med flera nivåer:

1. **Full självservice** för standardiserade, lågrisknära åtgärder.
2. **Självservice med godkännande** när teamet kan initiera arbetet, men vissa trösklar kräver granskning.
3. **Styrd beställning** när behovet är känt men kräver manuell koordinering.
4. **Särskild prövning** när behovet är nytt, riskfyllt eller strategiskt viktigt.

Poängen är att göra skillnad på standard och undantag. När allt går genom samma manuella flöde blir organisationen långsam. När allt blir självservice utan gränser blir organisationen riskfylld. Ledningens uppgift är att skapa en modell där rätt saker kan gå snabbt och rätt saker fortfarande granskas.

## Produktansvar för interna plattformstjänster

En intern plattformsprodukt behöver en ansvarig ägare. Det räcker inte att säga att “driften äger plattformen” om ingen har mandat att prioritera mellan användarbehov, teknisk skuld, säkerhetskrav, robusthet och kapacitetsförbättringar.

Produktansvar för en intern plattformstjänst innebär att någon ansvarar för:

- målgrupp och användningsfall,
- tjänstens syfte och avgränsning,
- krav på säkerhet, driftbarhet och efterlevnad,
- dokumentation och onboarding,
- supportmodell och förväntad servicenivå,
- prioritering av förbättringar,
- livscykel och avveckling,
- mätetal för nytta och kvalitet.

Detta ansvar kan ligga i ett plattformsteam, en plattformsorganisation eller en gemensam funktion. Det viktiga är inte exakt organisationsruta. Det viktiga är att ansvaret är tydligt, finansierat och förankrat hos ledningen.

Utan produktansvar blir plattformen lätt en teknisk samling funktioner. Med produktansvar kan den bli ett styrmedel för bättre leveransförmåga.

## Ledningsbeslut som krävs

För att gå från miljöbeställningar till plattformsprodukter behöver ledningen fatta ett antal beslut som inte bör lämnas till enbart operativa grupper.

### 1. Vilka behov ska produktifieras först?

Börja inte med allt. Välj några återkommande behov där nyttan är tydlig och risken hanterbar. Ett bra första område är ofta icke-produktionsmiljöer, teamonboarding eller standardiserade pipelines.

### 2. Vem äger den interna produkten?

Det måste finnas en ansvarig funktion eller roll med mandat att prioritera. Annars blir plattformen beroende av eldsjälar och tillfälliga förbättringsinitiativ.

### 3. Vilka krav är obligatoriska?

Säkerhet, loggning, övervakning, spårbarhet, backup, resursgränser och åtkomst bör inte vara frivilliga val som varje team tolkar. Kraven behöver byggas in i erbjudandet.

### 4. Var går gränsen för självservice?

Ledningen behöver besluta vilka ramar som gäller. Vilka åtgärder får team göra själva? Vilka kräver godkännande? Vilka är inte tillåtna utan särskild prövning?

### 5. Hur ska undantag hanteras?

Undantag kommer alltid att finnas. Det viktiga är att de inte blir den normala vägen. Undantag ska vara synliga, motiverade, tidsbegränsade där det är möjligt och lärande för produktutvecklingen.

### 6. Hur mäter vi om modellen fungerar?

Mät inte bara antal automatiseringar. Mät om ledtider minskar, kvaliteten ökar, beställningar blir färre eller tydligare, incidentrisk inte ökar, användare förstår erbjudandet och driftorganisationens manuella tolkningsarbete minskar.

## Vanliga misstag

### Misstag: Att automatisera det gamla beställningsflödet utan att förändra modellen

Det kan vara lockande att bara lägga mer skript och formulär ovanpå dagens flöde. Det kan ge viss förbättring, men riskerar att cementera grundproblemet: varje behov behandlas fortfarande som ett ärende.

**Hur man undviker det:** Identifiera återkommande behov och gör dem till standardiserade erbjudanden, inte bara snabbare ärenden.

### Misstag: Att kalla något självservice utan att bygga in kontroller

Om team får större handlingsutrymme utan inbyggda krav kan organisationen skapa ny risk och nya variationer.

**Hur man undviker det:** Bygg självservice på godkända mallar, automatiserade kontroller, tydliga gränser och spårbarhet.

### Misstag: Att skapa en plattformsprodukt utan produktägarskap

En plattformstjänst utan ansvarig ägare blir ofta tekniskt fungerande men svår att använda, svår att prioritera och svår att förbättra.

**Hur man undviker det:** Ge varje central plattformstjänst en tydlig ägare, målgrupp, roadmap och finansierad förvaltning.

### Misstag: Att låta alla behov bli undantag

När standarderbjudandet inte matchar verkliga behov hittar team andra vägar. Då ökar variationen igen.

**Hur man undviker det:** Följ upp undantag som produktfeedback. Om samma undantag återkommer bör erbjudandet utvecklas.

### Misstag: Att tro att produktmodellen bara berör plattformsteamet

Plattformsprodukter påverkar utveckling, drift, säkerhet, arkitektur, ekonomi och ledning.

**Hur man undviker det:** Beskriv ansvar och beslutsgränser gemensamt. En intern produkt är en organisationsmodell, inte bara en teknisk leverans.

## Övningar

### Övning 1: Identifiera kandidater för produktifiering

Välj tre återkommande beställningar i din organisation. För varje beställning, besvara:

1. Hur ofta uppstår behovet?
2. Vilka funktioner behöver vanligtvis involveras?
3. Vilka delar är nästan alltid likadana?
4. Vilka delar kräver verklig bedömning?
5. Skulle behovet kunna bli självservice, självservice med godkännande, styrd beställning eller särskild prövning?

Målet är inte att hitta perfekta svar. Målet är att börja skilja mellan standard och undantag.

### Övning 2: Formulera en intern plattformsprodukt

Välj ett område, till exempel “standardiserad testmiljö” eller “godkänd pipeline för containerapplikationer”. Beskriv produkten med följande rubriker:

- Målgrupp
- Problem den löser
- Vad som ingår
- Vad som inte ingår
- Obligatoriska säkerhets- och driftkrav
- Gränser för självservice
- Vem som äger produkten
- Hur förbättringar prioriteras

### Fördjupning: Ledningsdialog

Diskutera i en ledningsgrupp:

- Vilka beställningar borde egentligen inte längre vara beställningar?
- Vilka risker är vi beredda att hantera genom automatiserade kontroller?
- Vilka risker kräver fortfarande manuell prövning?
- Vilken funktion har mandat att säga nej till speciallösningar som bryter mot standard?
- Hur säkerställer vi att standarderbjudandet utvecklas när verksamhetens behov förändras?

## Beslut att fatta

- Vilka plattformstjänster ska erbjudas som produkter med tydliga löften, livscykel och ansvar?
- Vilka behov ska fortfarande hanteras som individuella beställningar?
- Vem ska äga backlog, prioritering och kvalitet för interna plattformsprodukter?

## Snabb sammanfattning

- Beställningsflöden har legitima styrkor, men de blir långsamma när återkommande behov behandlas som unika ärenden.
- *Platform engineering* innebär att den interna plattformen byggs och förvaltas som en produkt för interna användare.
- Självservice betyder frihet inom definierade, spårbara och godkända ramar.
- En intern produkt behöver målgrupp, ägare, roadmap, supportmodell, dokumentation, krav och finansiering.
- Alla behov ska inte bli självservice. Ledningen behöver skilja mellan standard, godkännande, styrd beställning och särskild prövning.
- Den viktigaste förflyttningen är från “vad vill teamet beställa?” till “vilka återkommande behov ska plattformen lösa på ett standardiserat sätt?”

## Kontrollfrågor

1. Vad är den viktigaste skillnaden mellan ett beställningsflöde och en intern plattformsprodukt?
2. Varför är självservice inte samma sak som frihet utan kontroll?
3. Vilka risker uppstår om en organisation automatiserar ett gammalt beställningsflöde utan att produktifiera återkommande behov?
4. Vilka tre egenskaper bör ett behov ha för att vara en bra kandidat för självservice?
5. Vilka beslut behöver ledningen fatta innan utvecklingsteam får större handlingsutrymme på plattformen?
6. Vilka återkommande undantag i din organisation skulle kunna vara signaler om att standarderbjudandet är för svagt?

## Nästa steg

I nästa kapitel går vi vidare till ledningens ansvar. När organisationen börjar produktifiera plattformstjänster och införa självservice blir vissa beslut mer kritiska, inte mindre. Mandat, målkonflikter, riskacceptans och styrningsprinciper kan inte helt delegeras till plattformsteam, utvecklingsteam eller driftorganisation. De behöver ägas av ledningen.
