# Kapitel 5: Ledningens ansvar: mandat, målkonflikter och beslut som inte kan delegeras

## Varför detta kapitel finns

När en organisation börjar röra sig från miljöbeställningar till plattformsprodukter uppstår snabbt en fråga som inte kan lösas av teknikteam, driftspecialister eller enskilda produktägare:

**Vem har mandat att ändra spelreglerna?**

Det är lätt att underskatta den frågan. Många förändringsinitiativ startar med god energi i tekniknära grupper. Ett plattformsteam vill erbjuda självservice. Utvecklingsteamen vill kunna skapa och förändra miljöer snabbare. Driftorganisationen vill minska mängden felaktiga beställningar och repetitivt arbete. Säkerhetsteamet vill att kraven ska efterlevas mer konsekvent. Alla ser förbättringsmöjligheter.

Men när förbättringarna påverkar ansvar, risk, finansiering, prioritering och kontrollnivå räcker det inte med lokal initiativkraft. Då krävs ledningsbeslut.

Det här kapitlet handlar om de beslut som **inte bör delegeras nedåt**, även om de senare ska genomföras nära tekniken. Det handlar inte om att ledningen ska detaljstyra pipelines, behörighetsmodeller eller plattformskonfiguration. Det handlar om att ledningen måste sätta de ramar som gör att utveckling, drift, säkerhet och plattform kan agera samordnat.

I scenariot **Myndigheten för Samhällstjänst** märks detta när containerplattformen börjar beskrivas som en möjlighet till självservice. Utvecklingsteamen frågar vad de själva får göra. Driftorganisationen frågar vem som ansvarar om något går fel. Säkerhetsteamet frågar hur kraven ska följas upp. Ekonomifunktionen frågar hur plattformen ska finansieras. Verksamhetsansvariga frågar när de får nytta av investeringen.

Alla frågor är legitima. Men de kan inte besvaras var för sig. De kräver gemensam ledning.

## Lärandemål

Efter kapitlet ska du kunna:

- skilja mellan beslut som kan delegeras och beslut som måste tas på ledningsnivå,
- beskriva varför mandat är avgörande för plattformsförmåga,
- identifiera målkonflikter som behöver hanteras öppet i stället för att döljas i ärendeflöden,
- förklara vad riskacceptans innebär i en ledningskontext,
- formulera styrningsprinciper som ger riktning utan att låsa fast detaljer.

## Innan vi börjar

I kapitel 4 introducerades **intern produkt**, **självservice** och **platform engineering**. Där såg vi att återkommande behov inte alltid bör hanteras som unika beställningar. Vissa behov bör paketeras som standardiserade plattformstjänster.

Men en intern produkt kan inte bära mer ansvar än organisationen har gett den mandat för. Ett plattformsteam kan inte ensamt bestämma risknivå. Ett säkerhetsteam kan inte ensamt avgöra leveransmodell. En driftorganisation kan inte ensamt bära konsekvensen av självservice om andra får större frihet. Ett utvecklingsteam kan inte ensamt definiera vad som är acceptabel produktionsrisk.

Därför behöver vi tre nya huvudbegrepp: **mandat**, **riskacceptans** och **styrningsprincip**.

## Tre begrepp: mandat, riskacceptans och styrningsprincip

### Mandat

**Mandat** betyder att en person, grupp eller funktion har rätt att fatta vissa beslut och förväntas ta ansvar för konsekvenserna.

I en traditionell beställningsmodell är mandat ofta otydligt. Utvecklingsteamet beställer. Driftorganisationen utför. Säkerhetsteamet tolkar riktlinjer. Driftskoordineringen kvalitetssäkrar större förändringar. Om något blir fel kan varje funktion peka på att den gjorde sin del.

När plattformsförmåga införs behöver mandat bli tydligare. Om ett team ska få skapa en miljö via självservice måste det vara tydligt:

- vem som har beslutat att teamet får göra det,
- vilka ramar teamet måste hålla sig inom,
- vilka kontroller som är automatiserade,
- vem som äger plattformstjänsten,
- vem som ansvarar för applikationens beteende,
- när ett undantag kräver manuell prövning.

Mandat är inte detsamma som frihet utan ansvar. Tvärtom är mandat en förutsättning för ansvar.

### Riskacceptans

**Riskacceptans** innebär att ledningen medvetet accepterar en viss risknivå eftersom nyttan, kontrollen och alternativen har bedömts.

I stora reglerade organisationer finns ofta en stark önskan att undvika risk. Det är förståeligt. Men i praktiken finns risk i alla alternativ. Det finns risk i att ge team större självservice. Det finns också risk i att behålla långsamma, manuella och svåröverblickbara beställningsflöden. Det finns risk i att förändra snabbt. Det finns risk i att förändra för långsamt.

Ledningens uppgift är inte att kräva noll risk. Uppgiften är att avgöra vilken risk som är acceptabel, under vilka villkor och med vilken uppföljning.

Exempel:

- Det kan vara acceptabelt att utvecklingsteam själva skapar standardiserade testmiljöer om miljöerna följer godkända mallar, loggas, märks upp och rensas automatiskt.
- Det kan vara oacceptabelt att team själva exponerar produktionsnära tjänster utan kontrollerad nätverksmodell, godkänd autentisering och tydlig incidentkontakt.
- Det kan vara acceptabelt att vissa kontroller flyttas från manuell granskning till automatiserad policy, om säkerhetsteamet äger kraven och resultatet följs upp.

Riskacceptans ska inte gömmas i tekniska detaljer. Den ska vara ett medvetet ledningsbeslut.

### Styrningsprincip

En **styrningsprincip** är en gemensam regel eller riktning som hjälper organisationen att fatta många vardagsbeslut konsekvent.

En bra styrningsprincip är tillräckligt tydlig för att styra, men inte så detaljerad att den blir en teknisk instruktion.

Exempel på styrningsprinciper:

- Standardiserade behov ska lösas med självservice innan de löses med manuella beställningar.
- Säkerhetskrav ska så långt som möjligt byggas in i plattform och pipeline.
- Undantag ska vara synliga, tidsbegränsade och aktivt ägda.
- Team får större frihet när kontrollerna är tydliga, automatiserade och spårbara.
- Produktionsnära förändringar ska kunna kopplas till ägare, beslut, risk och återställningsplan.

Styrningsprinciper är särskilt viktiga när organisationen går från ett ärendestyrt arbetssätt till en mer produkt- och plattformsorienterad modell. De gör att många beslut kan fattas snabbare utan att varje fråga behöver lyftas till ledningen.

## Varför ledningen inte kan delegera målkonflikten

Ett vanligt misstag är att ledningen ber organisationen “hitta en bra balans” mellan snabbhet och kontroll, men utan att tydliggöra vad balansen betyder.

Då hamnar målkonflikten längre ned i organisationen.

Utvecklingsteamet tolkar uppdraget som att de ska leverera snabbare. Driftorganisationen tolkar uppdraget som att stabiliteten inte får äventyras. Säkerhetsteamet tolkar uppdraget som att kraven inte får försvagas. Plattformsteamet tolkar uppdraget som att självservice ska införas. Driftskoordineringen tolkar uppdraget som att större förändringar fortfarande behöver kvalitetssäkras.

Alla gör rimliga tolkningar. Ändå uppstår friktion.

Det är ledningens ansvar att ange vilken målkonflikt organisationen ska lösa och vilka avvägningar som är acceptabla. Ledningen behöver inte besluta varje detalj, men den behöver ge tydliga svar på frågor som:

- Ska självservice vara ett strategiskt mål eller bara ett tekniskt experiment?
- Vilka typer av miljöer och förändringar ska kunna hanteras utan manuell beställning?
- Vilken risknivå accepteras i utvecklings-, test-, integrations- och produktionsnära miljöer?
- Vilka kontroller måste vara automatiserade innan frihetsgraden ökar?
- Vilka beslut får plattformsteamet fatta själv?
- Vilka beslut måste säkerhet, drift och utveckling fatta tillsammans?
- När ska befintliga arbetssätt anpassas till plattformen, och när ska plattformen anpassas till befintliga arbetssätt?

Om dessa frågor inte besvaras blir resultatet ofta att gamla arbetssätt lever vidare under nya tekniska begrepp. Organisationen får containerplattform, men fortsätter styra som om varje miljö vore ett specialärende.

## Scenario: Myndigheten för Samhällstjänst fastnar i delegerad osäkerhet

Hos Myndigheten för Samhällstjänst har ett antal utvecklingsteam börjat använda den nya containerplattformen i tidiga miljöer. Plattformsteamet har skapat några standardmallar. Det finns en pipeline som kan bygga och leverera applikationer. Säkerhetsteamet har tagit fram riktlinjer för containeranvändning. Driftorganisationen har börjat dokumentera hur övervakning och incidenthantering ska fungera.

På ytan ser förändringen positiv ut.

Men efter några månader uppstår flera frågor:

- Ett utvecklingsteam vill själva skapa en ny integrationsmiljö. Driftorganisationen menar att det fortfarande kräver beställning.
- Säkerhetsteamet vill granska vissa containerkonfigurationer innan de används i produktionsnära miljöer. Plattformsteamet vill i stället automatisera kontrollen.
- Driftskoordineringen vill fortsätta godkänna större förändringar eftersom beroenden till IBM MQ och Oracle kan påverka stabiliteten.
- Verksamhetsledningen undrar varför självservice inte redan gett kortare ledtider.
- Plattformsteamet upplever att de förväntas leverera modern förmåga, men utan mandat att ändra gamla processer.

Problemet är inte att någon grupp gör fel. Problemet är att ledningen har delegerat en målkonflikt utan att ge tillräckliga beslut.

En handlingsdriven ledning skulle i detta läge inte börja med att fråga varför teamen inte “samarbetar bättre”. Den skulle samla ansvariga chefer och fatta ett antal ramsättande beslut:

1. Vilka självserviceflöden ska vara strategiskt prioriterade första året?
2. Vilka kontroller måste vara inbyggda innan dessa flöden får användas brett?
3. Vilka miljötyper omfattas av självservice, och vilka gör det inte ännu?
4. Vilka undantag kräver manuell prövning?
5. Vem äger plattformstjänsternas backlog och prioritering?
6. Hur ska effekten mätas: ledtid, kvalitet, minskade omtag, färre felaktiga beställningar, bättre spårbarhet eller något annat?

Först när dessa beslut är fattade kan organisationen designa fungerande processer, pipelines, mallar och kontroller.

## Fem beslut ledningen behöver ta tidigt

### 1. Beslut om riktning

Ledningen behöver uttrycka vad plattformsförmågan ska åstadkomma.

En svag riktning låter så här:

> “Vi ska införa OpenShift och öka automatiseringen.”

En starkare riktning låter så här:

> “Vi ska minska återkommande manuella miljöbeställningar genom standardiserade plattformstjänster, öka självservice inom godkända ramar och bygga in säkerhets- och driftkrav i plattform och pipeline.”

Den andra formuleringen gör det tydligare vad som ska förändras organisatoriskt.

### 2. Beslut om ansvar

Ledningen behöver klargöra ansvarsfördelningen mellan utvecklingsteam, plattformsteam, drift, säkerhet, arkitektur och verksamhetsansvar.

En användbar tumregel är:

- Plattformsteamet ansvarar för plattformstjänstens användbarhet, standardisering och livscykel.
- Utvecklingsteamet ansvarar för applikationens funktion, konfiguration inom givna ramar och efterlevnad av definierade krav.
- Driftorganisationen ansvarar för operativ stabilitet, övervakningsförmåga, incidentprocesser och driftkrav.
- Säkerhetsteamet ansvarar för säkerhetskrav, riskprinciper och uppföljning av kontroller.
- Ledningen ansvarar för prioritering, mandat, riskacceptans och hantering av målkonflikter.

Detta är inte en färdig organisationsmodell. Det är ett sätt att synliggöra vilka ansvar som måste vara tydliga.

### 3. Beslut om frihetsgrader

Självservice behöver olika frihetsgrader i olika miljöer. Det är sällan klokt att ge samma frihet i en utvecklingsmiljö som i en produktionsnära miljö.

Ledningen bör därför besluta om principer för stegvis frihet:

- I utvecklingsmiljöer kan självservice vara bredare och mer experimentell.
- I test- och integrationsmiljöer krävs mer standardisering och tydligare beroendehantering.
- I produktionsnära miljöer krävs högre krav på spårbarhet, robusthet, övervakning och återställning.
- I produktionsmiljöer kan vissa moment vara automatiserade, men fortfarande kräva tydliga beslutspunkter och kontroller.

Poängen är inte att skapa byråkrati. Poängen är att göra frihet möjlig där den är lämplig och kontrollerad där risken är högre.

### 4. Beslut om undantag

Ingen plattformsmodell klarar alla behov från början. Därför behöver undantag hanteras öppet.

Ett dåligt undantag är informellt, permanent och osynligt.

Ett bra undantag är:

- dokumenterat,
- tidsbegränsat,
- riskbedömt,
- ägt av en ansvarig,
- kopplat till en plan för avveckling eller normalisering.

Ledningen behöver besluta att undantag inte ska användas som ett sätt att slippa välja. Om alla svåra fall blir undantag kommer den nya plattformen aldrig att bli normal arbetssätt. Då skapas en parallell värld där vissa team arbetar modernt, medan resten av organisationen sitter kvar i gamla flöden.

### 5. Beslut om uppföljning

Det som inte följs upp tenderar att bli otydligt.

Ledningen bör därför besluta vilka effekter som ska mätas. Exempel:

- ledtid från behov till användbar miljö,
- andel standardiserade miljöbehov som löses via självservice,
- antal omtag på grund av ofullständiga eller felaktiga beställningar,
- andel kontroller som är automatiserade,
- antal undantag och deras ålder,
- incidenter kopplade till plattformstjänster,
- användarnöjdhet hos utvecklingsteam,
- driftens upplevelse av förutsägbarhet och kvalitet.

Mätetalen ska inte användas för att skuldbelägga en funktion. De ska visa om organisationen faktiskt bygger plattformsförmåga.

## Vanliga misstag

### Misstag: Ledningen beslutar om teknik men inte om operativ modell

**Varför det händer:**  
Teknikbeslut är konkreta. Det är lättare att fatta beslut om plattformsval, licenser eller införandeprojekt än om ansvar, mandat och förändrade arbetssätt.

**Hur man undviker det:**  
Koppla varje större teknikbeslut till en operativ modell. Fråga alltid: vem äger tjänsten, vem får använda den, vilka kontroller gäller, hur finansieras den och hur följs effekten upp?

### Misstag: Självservice införs utan tydlig riskacceptans

**Varför det händer:**  
Självservice uppfattas som effektivisering. Organisationen underskattar att större frihet också ändrar riskbilden.

**Hur man undviker det:**  
Definiera vilka typer av självservice som är acceptabla i olika miljöer och vilka villkor som måste vara uppfyllda. Låt säkerhet, drift och utveckling bidra, men låt ledningen fatta riskbeslutet.

### Misstag: Säkerhet och drift får ansvar utan påverkan

**Varför det händer:**  
Ledningen vill öka hastigheten och ger utvecklingsteamen mer frihet, men lämnar drift och säkerhet med ansvar för konsekvenserna.

**Hur man undviker det:**  
Ge säkerhet och drift mandat att formulera krav som byggs in i plattformen. Gör dem till kravägare och medskapare av guardrails, inte bara granskare i efterhand.

### Misstag: Alla svåra frågor blir “senare”

**Varför det händer:**  
Organisationen vill komma igång. Svåra frågor om finansiering, ansvar, produktionssättning och undantag skjuts framåt.

**Hur man undviker det:**  
Identifiera tidigt vilka beslut som kan vänta och vilka som blockerar målbilden. Allt behöver inte vara färdigt, men de styrande principerna måste finnas.

## Övningar

### Övning 1: Sortera besluten

Gå igenom ett pågående eller planerat plattformsinitiativ. Lista tio beslut som diskuteras eller borde diskuteras.

Sortera dem i tre grupper:

1. Beslut som kan tas av ett tekniskt team.
2. Beslut som bör tas gemensamt av flera funktioner.
3. Beslut som kräver ledningsmandat.

Reflektera särskilt över om grupp 3 i praktiken redan har delegerats nedåt utan tydligt mandat.

### Övning 2: Formulera tre styrningsprinciper

Skriv tre styrningsprinciper för självservice i din organisation.

Använd formen:

> “Vi ska ... därför att ... under förutsättning att ...”

Exempel:

> “Vi ska erbjuda självservice för standardiserade testmiljöer därför att återkommande manuella beställningar sänker förändringskapaciteten, under förutsättning att miljöerna skapas från godkända mallar, loggas och har tydlig ägare.”

### Övning 3: Synliggör riskacceptans

Välj ett område där organisationen vill öka automatisering eller självservice.

Besvara:

- Vilken risk finns om vi ökar frihetsgraden?
- Vilken risk finns om vi inte gör det?
- Vilka kontroller måste finnas för att risken ska vara acceptabel?
- Vem kan fatta beslut om att risken är acceptabel?
- Hur ska beslutet följas upp?

### Fördjupning: Ledningsdialog

Använd följande frågor i ett ledningsforum:

1. Vilka målkonflikter har vi hittills låtit organisationen lösa informellt?
2. Vilka mandat saknas för att plattformsförmågan ska kunna växa?
3. Vilka beslut behöver vi fatta innan vi ber teamen automatisera mer?
4. Vilka undantag accepterar vi tillfälligt, och vilka riskerar att bli permanenta?
5. Vilka mätetal visar om vi bygger verklig förmåga eller bara inför ny teknik?

## Beslut att fatta

- Vilka beslut om mandat, risk och standardisering ska ägas av ledningen och inte av enskilda team?
- Vilka frihetsgrader ska utvecklingsteam få direkt, och vilka kräver uppfyllda villkor?
- Hur ska ledningen hantera konflikter mellan lokala behov och gemensam standard?

## Snabb sammanfattning

- Plattformsförmåga kräver tydliga ledningsbeslut om mandat, risk och styrning.
- Mandat innebär rätt att fatta beslut och ansvar för konsekvenserna.
- Riskacceptans är ett medvetet ledningsbeslut, inte en teknisk detalj.
- Styrningsprinciper gör att många vardagsbeslut kan fattas snabbare och mer konsekvent.
- Ledningen ska inte detaljstyra tekniken, men den måste ange ramarna för ansvar, frihetsgrader, undantag och uppföljning.
- Om målkonflikter delegeras utan beslut skapas friktion mellan utveckling, drift, säkerhet och plattform.
- Självservice fungerar bara när frihet kombineras med tydliga guardrails, spårbarhet och ansvar.

## Ledningsfrågor

1. Vad är skillnaden mellan att delegera genomförande och att delegera en olöst målkonflikt?
2. Varför kan inte ett plattformsteam ensamt besluta om risknivån för självservice?
3. Ge två exempel på styrningsprinciper som kan stödja självservice utan att tappa kontroll.
4. Vilka beslut om frihetsgrader behöver tas innan produktionsnära självservice införs?
5. Hur kan ledningen följa upp om plattformsförmågan faktiskt förbättras?

## Nästa steg

I detta kapitel har vi sett att ledningen måste sätta ramar för mandat, riskacceptans och styrningsprinciper. Nästa kapitel går djupare in i ett av de viktigaste områdena där dessa ramar behövs: **säkerhet**.

Frågan blir då inte om säkerhet ska finnas kvar i en mer agil och automatiserad modell. Frågan blir hur säkerhet kan byggas in i arbetssätt, plattform och pipeline så att den blir en möjliggörare i stället för en sen flaskhals.
