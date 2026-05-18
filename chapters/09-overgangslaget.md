# Kapitel 9: Övergångsläget: att leva med både gammalt och nytt

## Varför detta kapitel finns

Det är lätt att beskriva målbilden som om organisationen snart ska lämna det gamla bakom sig. I praktiken kommer en stor reglerad organisation ofta att leva länge med både befintliga plattformar och nya containerbaserade arbetssätt.

Det innebär att JBoss EAP, IBM MQ, Oracle, Elasticsearch, Ceph och andra etablerade plattformar inte försvinner bara för att en OpenShift-liknande containerplattform införs. De fortsätter att bära verksamhetskritiska tjänster, integrationer, dataflöden, historik, kompetens och operativa rutiner. Samtidigt ska nya arbetssätt växa fram: mer självservice, mer automatisering, tydligare guardrails, kortare ledtider och bättre gemensam styrning.

Det här mellanläget är ofta mer krävande än både nuläge och målbild. Det är här organisationens verkliga förändringsförmåga prövas. Om ledningen behandlar övergången som ett tillfälligt tekniskt undantag riskerar den att bli ett permanent tillstånd av dubbel komplexitet. Om ledningen däremot styr övergången aktivt kan den bli en kontrollerad väg mot bättre plattformsförmåga.

Kapitlets huvudbudskap är enkelt: **övergångsläget måste designas, finansieras och styras. Det får inte bara hända.**

## Lärandemål

Efter kapitlet ska läsaren kunna:

- förklara varför övergångsläget är en strategisk ledningsfråga och inte bara ett tekniskt migreringsproblem,
- skilja mellan samexistens, migration och avveckling som olika ledningsuppgifter,
- identifiera risker med att ha gamla och nya plattformar, arbetssätt och ansvar samtidigt,
- formulera principer för vilka tjänster som bör flyttas, vilka som bör stanna och vilka som bör avvecklas,
- beskriva hur integrationer, data, driftansvar och support behöver hanteras under en längre övergångsperiod.

## Innan vi börjar

Föregående kapitel behandlade vägvalet mellan greenfield och förändring i befintlig organisation. Oavsett vägval hamnar de flesta organisationer i ett övergångsläge.

Även en tydlig greenfield-satsning behöver kopplas till befintliga identitetslösningar, nätverk, loggning, övervakning, databaser, meddelandeflöden och incidentprocesser. Även en brownfield-förändring behöver skapa nya arbetssätt utan att bryta det som redan fungerar. Det finns alltså sällan en ren väg där den nya plattformen kan byggas helt frikopplad från organisationens arv.

I det här kapitlet använder vi tre huvudbegrepp:

- **övergångsarkitektur**,
- **samexistens**,
- **migreringsprincip**.

## Tre huvudbegrepp

### Övergångsarkitektur

**Övergångsarkitektur** är den medvetna designen av hur gammalt och nytt ska fungera tillsammans under en begränsad, men ofta lång, period.

Det handlar inte bara om teknisk arkitektur. Det handlar också om ansvar, beslut, finansiering, operativa krav, supportvägar, riskhantering och avvecklingsplaner.

En övergångsarkitektur svarar på frågor som:

- Vilka plattformar ska finnas parallellt?
- Vilka integrationer måste fungera mellan dem?
- Vilka krav gäller oavsett plattform?
- Vilka krav skiljer sig mellan gammalt och nytt?
- Vem äger incidenter som går över flera plattformar?
- Hur länge är mellanläget acceptabelt?
- Vilka delar ska avvecklas, moderniseras eller lämnas oförändrade?

Utan övergångsarkitektur får organisationen ofta en oplanerad blandning av undantag, speciallösningar och beroenden som ingen riktigt äger.

### Samexistens

**Samexistens** betyder att gamla och nya lösningar används samtidigt, med avsiktliga kopplingar och tydliga regler.

Samexistens är inte ett misslyckande. För stora reglerade organisationer är det ofta det enda realistiska sättet att förändra utan att ta oacceptabel risk. Problemet uppstår när samexistensen saknar styrning. Då blir den nya plattformen beroende av gamla flöden, samtidigt som gamla plattformar behöver anpassas till nya krav utan att ha fått resurser, mandat eller prioritet.

Bra samexistens kräver därför principer för hur plattformarna får bero på varandra.

### Migreringsprincip

En **migreringsprincip** är en ledningsregel för hur organisationen avgör vad som ska flyttas, när det ska flyttas och varför.

Det är viktigt att skilja på migrering som teknisk flytt och migrering som förmågeförflyttning. Att flytta en applikation till en containerplattform utan att förändra ansvar, driftbarhet, leveransflöde eller säkerhetskontroller kan ge ny teknik men samma gamla problem.

En bra migreringsprincip kan exempelvis säga:

- Nya tjänster ska i första hand byggas på den nya plattformen om kraven passar.
- Befintliga tjänster ska inte flyttas bara för att de finns.
- Tjänster med hög förändringstakt prioriteras före stabila system med låg förändringstakt.
- Tjänster med stora operativa brister ska förbättras innan de migreras.
- Tjänster som är nära avveckling ska normalt inte moderniseras.
- Verksamhetskritiska tjänster får migreras först när operativa minimikrav, support och återställningsförmåga är bevisade.

## Scenariot: Myndigheten för Samhällstjänst

På Myndigheten för Samhällstjänst har ledningen beslutat att en ny containerplattform ska etableras. Beslutet är inte att allt ska flyttas direkt. Beslutet är att organisationen ska bygga plattformsförmåga stegvis.

Samtidigt finns ett stort arv:

- flera verksamhetskritiska applikationer körs på JBoss EAP,
- meddelandeflöden går via IBM MQ,
- centrala datalager ligger i Oracle,
- sök- och loggnära funktioner använder Elasticsearch,
- lagrings- och objektbehov hanteras delvis med Ceph,
- utvecklingsteam levererar redan automatiskt till vissa befintliga miljöer,
- driftorganisationen har etablerade rutiner för miljöer, övervakning, patchning och incidenter,
- säkerhetsteamet styr genom riktlinjer, granskningar och kravtolkningar.

När containerplattformen införs blir frågan inte bara vilka applikationer som kan containeriseras. Den större frågan blir hur organisationen ska fungera när vissa tjänster ligger kvar, vissa moderniseras, vissa nyutvecklas och vissa kopplas ihop över plattformsgränser.

## Målkonflikten i övergångsläget

Övergångsläget skapar flera legitima målkonflikter.

Utvecklingsteamen vill ofta komma igång snabbt. De vill använda standardiserade pipelines, skapa miljöer själva och minska beroendet av manuella beställningar.

Driftorganisationen vill undvika otydliga ansvar, oförutsedda beroenden och produktionslösningar som inte går att övervaka, felsöka eller återställa.

Säkerhetsteamet vill säkerställa att nya arbetssätt inte skapar okända risker, kringgår etablerade kontroller eller flyttar beslut till team som ännu saknar rätt stöd.

Ledningen vill se effekt av investeringen, men behöver samtidigt undvika att organisationen får två parallella produktionsmodeller som båda kräver full bemanning och full styrning.

Alla dessa perspektiv är rimliga. Ledningens uppgift är att göra målkonflikten synlig och beslutsbar.

## Övergångslägets vanligaste fallgropar

### Fallgrop 1: Allt ska flyttas

Den första fallgropen är att migrering blir ett självändamål. Om ledningen mäter framgång i antal flyttade applikationer kan organisationen börja flytta sådant som inte borde flyttas.

Det kan leda till att stabila system med låg förändringstakt läggs på en ny plattform utan tydligt värde, medan mer förändringsintensiva områden fortfarande fastnar i gamla flöden.

Ledningsfrågan bör därför vara: **vilka flyttar bygger faktisk förmåga?**

### Fallgrop 2: Inget får flyttas förrän allt är perfekt

Den andra fallgropen är motsatsen. Organisationen väntar på att alla krav, kontroller, integrationer, roller och processer ska vara helt färdiga innan något får användas på riktigt.

Det låter ansvarsfullt, men kan i praktiken stoppa lärande. Plattformen blir då ett långt tekniskt projekt utan verklig återkoppling från team, drift och säkerhet.

Ledningsfrågan bör vara: **vilka begränsade och kontrollerade användningsfall kan ge säkert lärande?**

### Fallgrop 3: Gamla arbetssätt följer med in i ny plattform

En ny containerplattform kan snabbt bli ett nytt gränssnitt ovanpå samma gamla beställningslogik. Teamen får kanske nya verktyg, men måste fortfarande beställa varje förändring, vänta på tolkning, hantera otydliga krav och eskalera undantag.

Då har organisationen moderniserat tekniken men inte förmågan.

Ledningsfrågan bör vara: **vilka beslut och kontroller ska standardiseras så att de inte behöver hanteras som unika ärenden varje gång?**

### Fallgrop 4: Nya arbetssätt får ignorera gamla beroenden

Den motsatta risken är att den nya plattformen får arbeta som om arvet inte finns. Det kan skapa lösningar som fungerar i pilot men faller när de möter identitet, nätverk, data, meddelandeflöden, loggning, säkerhetskrav och incidentprocesser.

Ledningsfrågan bör vara: **vilka befintliga beroenden måste behandlas som gemensamma designkrav från början?**

### Fallgrop 5: Övergångsläget saknar ägare

Övergångsläget går ofta tvärs över linjeorganisationen. Det berör plattformsteam, drift, säkerhet, arkitektur, utveckling, förvaltning, verksamhet och ekonomi. Om ingen äger helheten blir varje funktion ansvarig för sin del, men ingen ansvarar för att mellanläget faktiskt fungerar.

Ledningsfrågan bör vara: **vem har mandat att prioritera, avgränsa och följa upp övergången som helhet?**

## En ledningsmodell för övergångsläget

Ledningen behöver inte detaljstyra varje tekniskt beslut. Däremot behöver den besluta om spelplanen. En användbar modell är att styra övergångsläget genom fem områden.

### 1. Klassning av tjänster

Alla applikationer och tjänster bör inte behandlas lika. Ledningen bör kräva en enkel klassning som stöd för beslut.

En möjlig klassning är:

| Tjänstetyp | Rekommenderad hantering |
|---|---|
| Ny tjänst med hög förändringstakt | Bygg i första hand på ny plattform om kraven passar. |
| Befintlig tjänst med hög förändringstakt | Bedöm modernisering om värdet motiverar kostnaden. |
| Stabil verksamhetskritisk tjänst | Flytta bara om risk, värde och stöd är tydligt motiverade. |
| Tjänst nära avveckling | Undvik modernisering om den inte krävs för riskreduktion. |
| Tjänst med stora driftbrister | Åtgärda driftbarhet innan eventuell migrering. |
| Gemensam infrastruktur- eller integrationstjänst | Hantera som strategiskt beroende, inte som en vanlig applikation. |

Syftet är inte att skapa en tung klassificeringsövning. Syftet är att undvika att migrering styrs av slump, entusiasm eller lokala önskemål.

### 2. Gemensamma krav oavsett plattform

Vissa krav bör gälla oavsett om en tjänst körs på befintlig plattform eller containerplattform. Exempel:

- ägarskap,
- riskklass,
- loggning,
- övervakning,
- incidentväg,
- återställningskrav,
- beroendekarta,
- säkerhetskrav,
- dokumenterade undantag,
- livscykelstatus.

Detta är viktigt eftersom ledningen annars kan få två olika riskbilder: en för det gamla och en för det nya. Målet bör vara en gemensam styrningsvy även om tekniken skiljer sig.

### 3. Tydliga integrationsprinciper

Övergångsläget kommer att kräva integrationer mellan gammalt och nytt. Containeriserade tjänster kan behöva prata med Oracle-databaser, IBM MQ-flöden, befintliga identitetslösningar, interna API:er eller lagringslösningar.

Ledningen behöver inte välja tekniska integrationsmönster i detalj, men bör besluta om principer:

- Integrationer ska vara avsiktliga och dokumenterade.
- Tillfälliga kopplingar ska ha ägare och slutdatum.
- Nya beroenden till äldre plattformar ska riskbedömas.
- Gemensamma integrationstjänster ska finansieras och prioriteras.
- Det ska vara tydligt vem som äger incidenter över plattformsgränser.

Det sista är särskilt viktigt. När en tjänst på den nya plattformen är beroende av en kö, databas eller lagringstjänst på befintlig plattform måste incidentansvaret vara känt innan produktion.

### 4. Planerad avveckling och normalisering

Övergångsläget blir farligt när allt läggs till men inget tas bort. Varje ny plattform, integration, pipeline, kontroll och supportmodell ökar den totala komplexiteten.

Därför behöver ledningen styra inte bara införande utan också avveckling och normalisering.

Frågor att besluta:

- Vilka gamla beställningsflöden ska ersättas av självservice?
- Vilka manuella kontroller ska byggas in i pipeline eller plattform?
- Vilka undantagslösningar har ett slutdatum?
- Vilka plattformar ska långsiktigt vara strategiska?
- Vilka kompetenser behöver byggas upp respektive fasas om?
- Vilka kostnader ska minska när ny förmåga införs?

Utan planerad normalisering får organisationen både den gamla kostnaden och den nya kostnaden.

### 5. Mätning av övergångens effekt

Övergången bör mätas på förmåga, inte bara aktivitet.

Exempel på ledningsmått:

| Område | Möjligt mått |
|---|---|
| Ledtid | Tid från godkänt behov till användbar miljö eller tjänst. |
| Självservice | Andel standardåtgärder som team kan utföra själva inom guardrails. |
| Driftbarhet | Andel tjänster som uppfyller operativa minimikrav. |
| Riskkontroll | Andel kontroller som är automatiserade eller tydligt ägda. |
| Incidentförmåga | Tid till upptäckt, diagnos och återställning över plattformsgränser. |
| Avveckling | Antal gamla flöden, speciallösningar eller manuella steg som tagits bort. |
| Lärande | Antal beslutade förbättringar från pilot till standard. |

Mätningen bör hjälpa ledningen att se om organisationen bygger plattformsförmåga eller bara inför ytterligare en teknisk miljö.

## Vad bör inte migreras?

En viktig ledningsfråga är vad som inte ska flyttas. I många transformationer blir det politiskt svårt att säga nej till migrering. Men ett tydligt nej kan vara ett tecken på god styrning.

Tjänster bör normalt inte migreras när:

- nyttan är oklar,
- tjänsten är nära avveckling,
- tjänsten har låg förändringstakt och stabil drift,
- migreringen främst drivs av teknikintresse,
- tjänstens beroenden gör flytten oproportionerligt dyr,
- driftbarheten är för svag för att bära en flytt,
- mottagande plattform saknar bevisad supportmodell,
- ansvar och riskacceptans inte är beslutade.

Detta betyder inte att tjänsten aldrig ska flyttas. Det betyder att flyttbeslutet behöver vara motiverat av värde, riskreduktion eller strategisk förmåga.

## Vad bör prioriteras tidigt?

Tidiga kandidater bör ge lärande utan att skapa oacceptabel risk. De bör också vara tillräckligt verkliga för att testa plattformens operativa modell.

Bra kandidater kan vara:

- nya tjänster med tydlig ägare,
- tjänster med hög förändringstakt men begränsad verksamhetsrisk,
- interna verktyg med verkliga användare,
- tjänster där teamet har vilja och kompetens att ta större ansvar,
- områden där säkerhets- och driftkrav kan automatiseras,
- integrationer som är viktiga nog att testa men inte så kritiska att fel blir oacceptabla.

Då kan organisationen lära sig om självservice, pipelines, guardrails, driftbarhet, incidentvägar och support utan att första steget blir ett högriskprojekt.

## Ansvar i övergångsläget

Ett vanligt misstag är att anta att ansvar kan definieras senare. I övergångsläget behöver ansvar ofta vara tydligare än i både gammal och ny modell.

Minimalt bör följande ansvar vara klara:

| Ansvarsområde | Ledningsfråga |
|---|---|
| Plattform | Vem äger plattformens roadmap, prioritering och livscykel? |
| Applikation | Vem äger tjänstens funktion, risk och förändringar? |
| Drift | Vem ansvarar för övervakning, incidenter, återställning och kapacitet? |
| Säkerhet | Vem tolkar krav, äger guardrails och godkänner undantag? |
| Integration | Vem äger beroenden mellan gammalt och nytt? |
| Ekonomi | Vem finansierar gemensamma förmågor och övergångskostnader? |
| Avveckling | Vem har mandat att ta bort gamla flöden och speciallösningar? |

Ledningen behöver särskilt undvika svaret “det löser teamen tillsammans”. Samarbete är nödvändigt, men utan mandat blir samarbete ofta bara en artig beskrivning av oklara beslut.

## Praktiskt beslutsstöd: fyra frågor före varje större flytt

Innan en tjänst flyttas eller nyutvecklas på containerplattformen bör ledningen eller det utsedda beslutsforumet kräva svar på fyra frågor.

### 1. Varför just denna tjänst?

Vilket värde skapas? Handlar det om snabbare förändring, minskad risk, bättre driftbarhet, avveckling av gammal teknik, kompetensutveckling eller strategiskt lärande?

### 2. Vad måste fungera runt tjänsten?

Vilka beroenden finns till data, meddelandeköer, identitet, nätverk, loggning, övervakning, lagring, backup, support och incidenthantering?

### 3. Vilka krav är inte förhandlingsbara?

Vilka krav på säkerhet, tillgänglighet, robusthet, spårbarhet och återställning måste vara uppfyllda före produktion?

### 4. Vad ska vi lära oss och normalisera?

Vilka lärdomar från flytten ska bli standard för nästa team? Vilka mallar, guardrails, krav, dokumentationsmönster eller beslut ska förbättras?

Den fjärde frågan är avgörande. Utan den blir varje migrering ett separat projekt. Med den kan varje flytt bidra till gemensam plattformsförmåga.

## Vanliga misstag

- **Misstag:** Organisationen beskriver övergångsläget som kort trots att alla vet att det blir flerårigt.  
  **Varför det händer:** Ledningen vill skapa energi runt målbilden och undvika att fastna i komplexitet.  
  **Hur man undviker det:** Erkänn mellanläget som en styrd fas med egen finansiering, egna mått och tydliga beslutspunkter.

- **Misstag:** Nya team får frihet men gamla beroenden får ingen prioritet.  
  **Varför det händer:** Plattformssatsningen finansieras, men integrationer och befintliga stödtjänster betraktas som redan lösta.  
  **Hur man undviker det:** Behandla gemensamma beroenden som strategiska delar av plattformsförmågan.

- **Misstag:** Migrering mäts i antal applikationer.  
  **Varför det händer:** Det är enkelt att rapportera och ger en känsla av framdrift.  
  **Hur man undviker det:** Mät förmågeförflyttning: ledtid, självservice, driftbarhet, automatiserade kontroller och avvecklade manuella steg.

- **Misstag:** Incidentansvar över plattformsgränser är oklart.  
  **Varför det händer:** Varje del har lokalt ansvar, men ingen äger kedjan.  
  **Hur man undviker det:** Definiera support- och eskaleringsmodell för tjänster som korsar gamla och nya plattformar innan produktion.

- **Misstag:** Övergången saknar avvecklingslogik.  
  **Varför det händer:** Införande upplevs mer akut än borttagning.  
  **Hur man undviker det:** Koppla varje ny förmåga till ett beslut om vilka gamla steg, flöden eller undantag som på sikt ska bort.

## Övningar

### Övning 1: Rita övergångskartan

Välj ett större systemområde i er organisation. Beskriv på en sida:

- vilka delar som körs på befintliga plattformar,
- vilka delar som skulle kunna köras på containerplattform,
- vilka beroenden som finns till databaser, köer, lagring, nätverk och identitet,
- vilka team eller funktioner som äger respektive del,
- var incidentansvaret är tydligt och var det är oklart.

Avsluta med att markera de tre beroenden som ledningen behöver förstå innan någon större flytt beslutas.

### Övning 2: Skapa migreringsprinciper

Formulera fem principer för vad som ska flyttas, vad som ska stanna och vad som ska avvecklas.

Börja med meningar som:

- “Nya tjänster ska ...”
- “Befintliga tjänster ska bara flyttas när ...”
- “Tjänster nära avveckling ska ...”
- “Verksamhetskritiska tjänster får migreras först när ...”
- “Varje migrering ska bidra till ...”

Jämför principerna med organisationens nuvarande styrning. Skulle de ändra faktiska beslut?

### Fördjupning: Designa ett övergångsforum

Beskriv ett beslutsforum för övergångsläget. Ange:

- vilka roller som måste ingå,
- vilka beslut forumet får fatta,
- vilka frågor som ska eskaleras till högre ledning,
- vilka mått forumet följer,
- hur ofta vägval och prioriteringar ska omprövas,
- hur lärdomar från pilot och migreringar blir standard.

## Beslut att fatta

- Vilka gamla plattformar ska moderniseras, kapslas in, integreras med eller avvecklas?
- Vilka integrationsmönster ska vara tillåtna under övergångsperioden?
- Hur ska ledningen styra kostnad och risk när gamla och nya arbetssätt behöver leva parallellt?

## Snabb sammanfattning

- Övergångsläget mellan gamla och nya plattformar är en strategisk ledningsfråga.
- Befintliga plattformar, integrationer och arbetssätt försvinner inte när containerplattformen införs.
- Övergångsarkitektur beskriver hur gammalt och nytt ska fungera tillsammans under en kontrollerad period.
- Samexistens är ofta nödvändig, men måste ha tydliga regler, ansvar och finansiering.
- Migrering bör styras av värde, riskreduktion och förmågeförflyttning, inte av antal flyttade applikationer.
- Ledningen behöver besluta vad som ska flyttas, vad som ska stanna, vad som ska avvecklas och hur lärdomar ska normaliseras.
- Varje migrering bör bidra till bättre plattformsförmåga, inte bara till ny teknisk placering.

## Kontrollfrågor

1. Varför är övergångsläget ofta svårare att styra än både nuläge och målbild?
2. Vad är skillnaden mellan samexistens och oplanerad parallellitet?
3. Vilka befintliga beroenden måste alltid beaktas innan en tjänst flyttas till containerplattform?
4. När bör en tjänst inte migreras, även om det är tekniskt möjligt?
5. Vilka mått skulle visa att er organisation bygger plattformsförmåga under övergången?
6. Hur tydligt är incidentansvaret i dag för tjänster som går över flera plattformar?
7. Vilka gamla flöden eller manuella steg borde avvecklas när nya självserviceförmågor införs?

## Nästa steg

När övergångsläget är synligt blir nästa fråga hur plattformsförmågan ska styras och finansieras långsiktigt. En containerplattform kan inte behandlas som ett engångsprojekt om den ska bli en strategisk förmåga. Den behöver ägarskap, prioritering, roadmap, kapacitetsstyrning och finansiering över tid.

Nästa kapitel handlar därför om **styrning, finansiering och prioritering av plattformsförmågan**.
