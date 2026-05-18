# Kapitel 6: Säkerhet som inbyggd styrning

## Varför detta kapitel finns

När ledningen vill öka självservice och automatisering dyker ofta en oro upp direkt:

**Kommer säkerheten att försämras när fler får göra mer själva?**

Frågan är rimlig. I en stor reglerad organisation är säkerhet inte ett tillval. Den är en del av leveransförmågan. Om organisationen inför en containerplattform, ger utvecklingsteam större handlingsutrymme och automatiserar fler steg utan att samtidigt förändra säkerhetsstyrningen, finns en tydlig risk: gamla manuella kontroller ersätts av snabbare flöden utan tillräckliga spärrar.

Men alternativet är inte att behålla alla manuella grindar. Om säkerhet endast fungerar genom riktlinjedokument, separata granskningar och personberoende bedömningar kommer den att bli en flaskhals när förändringstakten ökar. Då uppstår ett mönster där utveckling ser säkerhet som hinder, säkerhet ser utveckling som risk och drift hamnar i mitten när produktionen ska skyddas.

Det här kapitlet visar hur säkerhet kan bli **inbyggd styrning**. Det innebär att viktiga säkerhetskrav byggs in i plattform, pipelines, mallar, behörigheter, loggning och automatiserade kontroller. Säkerhetsteamets roll försvinner inte. Den förändras från att enbart vara granskare i slutet av flödet till att vara kravägare, rådgivare och designer av de ramar som gör självservice möjlig.

I scenariot **Myndigheten för Samhällstjänst** blir frågan konkret när utvecklingsteamen vill kunna skapa applikationsmiljöer och driftsätta oftare via en OpenShift-liknande plattform. Säkerhetsteamet vill inte godkänna varje ändring manuellt, men de kan inte heller släppa kontrollen. Driftorganisationen vill veta att plattformen inte öppnar för oöverblickbara variationer. Ledningen behöver därför besluta vilken säkerhetsstyrning som ska vara automatisk, vilken som ska vara manuell och vilka undantag som kräver särskild prövning.

## Lärandemål

Efter kapitlet ska du kunna:

- förklara varför säkerhet behöver byggas in i plattform och leveransflöden,
- skilja mellan riktlinjer, automatiserade kontroller och manuella godkännanden,
- beskriva begreppen **guardrails**, **policy-as-code** och **inbyggd kontroll**,
- identifiera vilka säkerhetsbeslut som kräver ledningsmandat,
- formulera principer för säker självservice i en stor reglerad organisation.

## Innan vi börjar

I kapitel 5 behandlades **mandat**, **riskacceptans** och **styrningsprinciper**. De begreppen är centrala även här. Säkerhet som inbyggd styrning fungerar bara om ledningen har bestämt:

- vilken risknivå som är acceptabel,
- vilka kontroller som ska vara obligatoriska,
- vilka avsteg som kräver godkännande,
- vem som äger säkerhetskraven,
- vem som ansvarar för att kontrollerna fungerar över tid.

Utan sådana beslut blir automatiserad säkerhet lätt en samling lokala initiativ. Några team bygger egna kontroller. Några följer gamla checklistor. Några inväntar säkerhetsteamets bedömning. Några gör undantag för att komma framåt. Resultatet blir varken snabbhet eller kontroll.

## Tre begrepp: guardrails, policy-as-code och inbyggd kontroll

### Guardrails

**Guardrails** är fördefinierade ramar som gör det möjligt att agera fritt inom säkra gränser.

En bra liknelse är en väg med mitträcke, vägmärken och hastighetsgränser. Föraren behöver inte be om tillstånd för varje meter, men vägen är utformad så att risken minskar och avvikelser blir synliga.

I en containerplattform kan guardrails exempelvis handla om:

- vilka basavbildningar som får användas,
- vilka nätverksvägar som är tillåtna,
- hur hemligheter och certifikat får hanteras,
- vilka resurser en applikation får använda,
- vilken loggning och övervakning som är obligatorisk,
- vilka säkerhetsskanningar som måste vara godkända före driftsättning,
- vilka behörigheter ett team får administrera själv.

Poängen är inte att ta bort ansvar från utvecklingsteamet. Poängen är att göra det lättare att göra rätt och svårare att oavsiktligt göra fel.

### Policy-as-code

**Policy-as-code** innebär att regler uttrycks i en form som kan kontrolleras automatiskt.

En riktlinje kan säga: “Produktionsnära applikationer ska inte exponera administrativa gränssnitt mot öppna nät.” Det är en viktig regel, men den kräver tolkning. Om regeln i stället omsätts till en automatisk kontroll kan plattformen eller leveransflödet upptäcka otillåtna konfigurationer innan de når produktion.

Policy-as-code är inte bara en teknisk fråga. Det är ett styrningsval. Ledningen behöver förstå att policy-as-code innebär att organisationen måste översätta säkerhetskrav från dokument och mötesbeslut till testbara, versionerade och uppföljningsbara regler.

Det ger flera fördelar:

- regler kan tillämpas konsekvent,
- avvikelser kan upptäckas tidigare,
- kontroller kan spåras över tid,
- säkerhetsteamet kan lägga mer tid på krav, risk och undantag,
- utvecklingsteam får snabbare återkoppling.

Men det skapar också krav. Någon måste äga reglerna. Någon måste prioritera förbättringar. Någon måste hantera falska positiva utslag, undantag och förändrade hotbilder.

### Inbyggd kontroll

**Inbyggd kontroll** betyder att kontrollen är en del av det normala arbetssättet, inte ett separat moment efteråt.

I en traditionell modell kan säkerhet ofta upplevas som något som händer sent: en granskning, ett godkännande, en kontrollpunkt eller en avvikelselista inför driftsättning. I en inbyggd modell sker delar av kontrollen löpande:

- när kod checkas in,
- när en containeravbildning byggs,
- när en miljö skapas,
- när en konfiguration ändras,
- när en applikation driftsätts,
- när driftdata visar avvikande beteende.

Inbyggd kontroll betyder inte att all mänsklig bedömning försvinner. Vissa beslut kräver fortfarande analys, dialog och riskacceptans. Men standardfallen ska inte behöva vänta på manuell tolkning varje gång.

## Varför riktlinjer inte räcker i högre förändringstakt

Riktlinjer är viktiga. De beskriver vad organisationen vill uppnå och vilka krav som gäller. Problemet uppstår när riktlinjer är det enda styrmedlet.

I en miljö med många utvecklingsteam, många tekniska beroenden och ökande automatisering får riktlinjer tre vanliga svagheter:

1. **De tolkas olika.**  
   Ett utvecklingsteam, en driftgrupp och en säkerhetsspecialist kan läsa samma formulering och dra olika slutsatser.

2. **De kontrolleras sent.**  
   Om kravet upptäcks först i driftskoordinering eller inför produktionssättning blir kostnaden för att ändra högre.

3. **De blir personberoende.**  
   Om efterlevnaden beror på vem som råkar granska ärendet blir flödet svårt att skala och svårt att förutse.

För ledningen innebär detta en viktig insikt: säkerhetsstyrning som fungerar i ett långsammare, mer ärendestyrt arbetssätt fungerar inte automatiskt i en plattformsmodell. När organisationen ökar självservice behöver även säkerhetsmodellen moderniseras.

Det betyder inte att alla riktlinjer ska ersättas av kod. Det betyder att ledningen behöver skilja mellan fyra typer av styrning:

| Typ av styrning | När den passar | Exempel |
|---|---|---|
| Princip | När organisationen behöver gemensam riktning | “Säkerhet ska byggas in tidigt i leveransflödet.” |
| Riktlinje | När krav behöver beskrivas och tolkas | “System ska ha spårbar åtkomsthantering.” |
| Automatiserad kontroll | När kravet kan testas återkommande | “Otillåtna containerprivilegier blockeras.” |
| Manuell bedömning | När kontext, risk eller undantag kräver analys | “Ny extern integration riskbedöms innan produktionssättning.” |

En mogen säkerhetsmodell använder alla fyra. Misstaget är att använda manuell bedömning för allt, eller automatiserad kontroll för sådant som ännu kräver mänsklig riskförståelse.

## Säkerhetsteamets roll förändras

När säkerhet byggs in i plattformen kan säkerhetsteamet uppleva att de förlorar kontroll. I praktiken kan det bli tvärtom, om förändringen leds rätt.

I en traditionell modell får säkerhetsteamet ofta många ärenden där de ska tolka riktlinjer, svara på frågor, granska lösningar och hantera undantag. De blir en flaskhals trots att de inte vill vara det. Samtidigt kan de sakna insyn i många vardagsbeslut som sker innan ärendet når dem.

I en inbyggd modell flyttas säkerhetsteamets tyngdpunkt:

- från upprepad manuell granskning till tydliga krav,
- från sena kontroller till tidig design,
- från dokument som läses olika till automatiserade standardkontroller,
- från allmän rådgivning till prioriterade riskområden,
- från personberoende godkännanden till spårbar undantagshantering.

Det kräver dock att säkerhetsteamet får rätt mandat och kapacitet. Det går inte att be säkerhetsteamet “automatisera sina krav” utan att ge dem tid, kompetensstöd och en fungerande relation till plattformsteamet.

En praktisk ledningsfråga är därför:

**Vilken del av säkerhetsarbetet ska säkerhetsteamet utföra själv, och vilken del ska de äga som krav men realisera tillsammans med plattform, drift och utveckling?**

Den frågan är strategisk. Om den lämnas obesvarad skapas lätt nya konflikter. Säkerhetsteamet vill ha kontroll men saknar teknisk förmåga att bygga kontroller. Plattformsteamet bygger kontroller men är osäkert på kravens innebörd. Utvecklingsteamen får olika besked beroende på vem de frågar.

## Självservice kräver tydliga säkerhetsnivåer

All självservice bör inte vara lika fri. En vanlig ledningsmiss är att diskutera självservice som om det vore ett enda beslut: antingen får team göra saker själva, eller så får de inte.

I en reglerad organisation är det bättre att definiera nivåer.

Exempel på nivåer kan vara:

| Nivå | Beskrivning | Typisk kontroll |
|---|---|---|
| Nivå 1: Fördefinierad självservice | Team väljer bland godkända standardalternativ | Automatiska kontroller och loggning |
| Nivå 2: Självservice med villkor | Team får göra mer om vissa krav uppfylls | Automatiska kontroller plus spårbar uppföljning |
| Nivå 3: Undantag med godkännande | Team behöver avvika från standard | Manuell riskbedömning och tidsbegränsat beslut |
| Nivå 4: Särskilt skyddsvärd lösning | Hög risk, särskilda krav eller känslig information | Separat säkerhetsarkitektur och ledningsbeslut |

Med en sådan modell kan ledningen undvika två ytterligheter. Den ena är att allt blir manuellt eftersom vissa fall är riskfyllda. Den andra är att allt automatiseras eftersom vissa fall är enkla.

Myndigheten för Samhällstjänst kan till exempel besluta att utvecklingsteam själva får skapa standardiserade test- och integrationsmiljöer inom godkända mallar. Produktionsnära miljöer får också skapas via självservice, men endast om applikationen följer fastställda krav på loggning, nätverk, sårbarhetsskanning, resursbegränsningar och ansvarig förvaltning. Avvikelser kräver riskbedömning.

Det är ett ledningsbeslut, inte en teknisk detalj.

## Från säkerhetskrav till plattformsförmåga

För att säkerhet ska bli inbyggd styrning behöver organisationen översätta krav till plattformsförmågor. Det kan göras i fem steg.

### 1. Identifiera återkommande säkerhetskrav

Börja inte med verktyg. Börja med de krav som ofta återkommer och ofta skapar friktion.

Exempel:

- åtkomst och behörighet,
- hantering av hemligheter,
- nätverkssegmentering,
- loggning och spårbarhet,
- sårbarhetsskanning,
- containeravbildningar,
- kryptering,
- backup och återställning,
- separation mellan miljöer,
- hantering av externa beroenden.

Ledningens roll är att kräva prioritering. Allt kan inte byggas in samtidigt. De mest riskreducerande och flödesförbättrande kraven bör komma först.

### 2. Avgör vad som kan standardiseras

Vissa krav kan omsättas till standardmallar. Andra kan bli automatiska kontroller. Några kräver dokumenterade beslut.

Frågan bör inte vara: “Kan vi automatisera säkerhet?” Frågan bör vara:

**Vilka säkerhetskrav är så återkommande att de bör bli standard i plattformen?**

Det kan handla om att endast tillåta godkända basavbildningar, att alla applikationer måste skicka loggar till en central lösning eller att alla produktionsnära tjänster måste ha definierad ägare och återställningskrav.

### 3. Bygg in kraven där de gör mest nytta

Alla kontroller ska inte ligga i samma steg. Vissa bör ligga i utvecklingsflödet, andra i plattformen och andra i driftuppföljningen.

Exempel:

- kod- och beroendeskanning i CI/CD,
- avbildningsskanning i byggflödet,
- behörighetskontroller i plattformen,
- nätverkspolicy i körmiljön,
- logguppföljning i drift,
- avvikelselarm i övervakningen,
- riskacceptans i beslutsforum.

Ledningens ansvar är att se till att kontrollerna bildar en helhet. Annars riskerar varje funktion att bygga sin egen kontrollpunkt, vilket återskapar gamla flaskhalsar i ny form.

### 4. Skapa en tydlig undantagsprocess

Inbyggd styrning fungerar bara om det finns ett seriöst sätt att hantera undantag.

Undantag ska inte vara informella genvägar. De ska vara spårbara beslut. Ett bra undantag beskriver:

- vad som avviker från standard,
- varför avvikelsen behövs,
- vilken risk den skapar,
- vem som accepterar risken,
- hur länge undantaget gäller,
- vilken åtgärd som ska minska eller ta bort behovet av undantaget.

Utan en sådan process kommer organisationen antingen att stoppa nödvändiga förändringar eller skapa informella vägar runt kontrollen.

### 5. Följ upp både risk och flöde

Säkerhet som inbyggd styrning ska inte bara mätas i antal blockerade avvikelser. Då kan modellen uppfattas som lyckad trots att leveransflödet har blivit långsammare och mer frustrerande.

Ledningen bör följa upp både säkerhet och leveransförmåga, till exempel:

- hur många avvikelser som upptäcks tidigt respektive sent,
- hur ofta team behöver undantag,
- vilka krav som skapar mest friktion,
- hur lång tid säkerhetsrelaterade beslut tar,
- vilka kontroller som är automatiserade,
- vilka risker som fortfarande hanteras manuellt,
- om incidenter och driftproblem minskar eller ökar.

Det viktiga är inte att ha många mätetal. Det viktiga är att mätetalen visar om säkerheten faktiskt blivit mer inbyggd och om organisationen kan leverera snabbare utan att riskerna blir otydliga.

## Exempel: Myndigheten för Samhällstjänst

Ledningen för Myndigheten för Samhällstjänst har beslutat att containerplattformen ska ge utvecklingsteamen mer självservice. Men efter de första workshopparna blir det tydligt att säkerhetsteamet och utvecklingsteamen menar olika saker med “godkänd lösning”.

Utvecklingsteamen vill ha tydliga mallar. De vill veta: “Om vi följer den här vägen, kan vi då leverera utan ytterligare väntan?”

Säkerhetsteamet vill inte ge generella godkännanden som senare kan användas i fel kontext. De vill kunna bedöma risk utifrån informationens känslighet, integrationer, åtkomstvägar och driftkritikalitet.

Driftorganisationen vill säkerställa att det som sätts i produktion går att övervaka, felsöka, återställa och kapacitetsplanera.

Ledningen ber därför de tre funktionerna ta fram en gemensam modell med fyra beslut:

1. **Standardfall:** Vilka typer av applikationer och miljöer ska kunna gå genom standardiserad självservice?
2. **Obligatoriska kontroller:** Vilka säkerhets- och driftkrav ska alltid kontrolleras automatiskt?
3. **Undantag:** Vilka avvikelser kräver manuell riskbedömning?
4. **Ägarskap:** Vem äger kraven, vem bygger kontrollerna och vem följer upp resultatet?

Efter arbetet beslutar ledningen att plattformsteamet ska erbjuda tre godkända applikationsmallar. Mallarna innehåller standardiserad loggning, resursgränser, grundläggande nätverkspolicy, godkända basavbildningar och koppling till centrala övervakningsflöden. Säkerhetsteamet äger kravbilden för säkerhetskontrollerna. Plattformsteamet ansvarar för teknisk realisering. Driftorganisationen äger driftbarhetskrav. Utvecklingsteamen ansvarar för applikationens kod, konfiguration och informationsklassning.

Beslutet tar inte bort alla konflikter. Men det skapar en gemensam spelplan. Standardfallen blir snabbare. Undantagen blir synliga. Säkerhetsteamet behöver inte granska varje likartat ärende från början. Driftorganisationen får mer förutsägbara produktionsförutsättningar. Utvecklingsteamen får tydligare svar på vad de får göra själva.

## Vanliga misstag

### Misstag: Att automatisera otydliga krav

Om ett krav är otydligt i dokumentform blir det inte tydligt bara för att det läggs in i ett verktyg.

**Varför det händer:**  
Organisationen vill snabbt få kontroll och börjar därför med tekniska spärrar innan kraven är tillräckligt tolkade.

**Hur man undviker det:**  
Låt säkerhet, drift, plattform och utveckling gemensamt översätta krav till konkreta standardfall, kontroller och undantag. Börja med få men viktiga krav.

### Misstag: Att göra säkerhetsteamet till fortsatt flaskhals

Självservice misslyckas om varje automatiserat steg ändå kräver informell avstämning med säkerhetsteamet.

**Varför det händer:**  
Ledningen har inte beslutat vilka standardfall som är godkända och vilken risknivå som accepteras.

**Hur man undviker det:**  
Besluta tydligt vilka fall som får hanteras via standardiserad självservice och vilka som kräver särskild prövning.

### Misstag: Att blanda ihop frihet med avsaknad av kontroll

Vissa tolkar självservice som att teamen ska få göra vad de vill. Andra tolkar kontroll som att teamen nästan inte ska få göra något själva.

**Varför det händer:**  
Organisationen saknar gemensamma guardrails.

**Hur man undviker det:**  
Beskriv självservice som frihet inom ramar: tydliga mallar, automatiska kontroller, spårbarhet och undantagsprocess.

### Misstag: Att behandla undantag som misslyckanden

I komplexa miljöer kommer undantag alltid att behövas.

**Varför det händer:**  
Organisationen vill ha renhet i modellen och blir frustrerad när verkligheten inte passar standarden.

**Hur man undviker det:**  
Gör undantag tidsbegränsade, riskbedömda och spårbara. Använd återkommande undantag som signal om att plattformens standarderbjudande behöver förbättras.

### Misstag: Att bara mäta säkerhetsaktivitet

Antal granskningar, blockerade driftsättningar eller hittade avvikelser säger inte ensamt om säkerheten blivit bättre.

**Varför det händer:**  
Det är lättare att mäta aktivitet än effekt.

**Hur man undviker det:**  
Mät både riskreducering och flöde. Följ upp hur tidigt problem upptäcks, hur ofta undantag behövs och vilka kontroller som faktiskt minskar osäkerhet.

## Övningar

### Övning 1: Klassificera era säkerhetskrav

Välj fem återkommande säkerhetskrav i er organisation. För varje krav, bedöm om det främst bör hanteras som:

- princip,
- riktlinje,
- automatiserad kontroll,
- manuell bedömning,
- eller kombination.

Diskutera särskilt vilka krav som skapar mest väntetid i dag.

### Övning 2: Rita er första självservicenivå

Beskriv en begränsad självservice som skulle kunna vara säker att införa först. Exempel: skapande av standardiserad testmiljö, ny applikationsyta i icke-produktionsmiljö eller standardiserad pipeline för containerbygge.

Besvara:

- Vilka val får teamet göra själv?
- Vilka val är låsta i mall?
- Vilka kontroller sker automatiskt?
- När måste ett undantag lyftas?

### Fördjupning: Granska ett undantag

Ta ett verkligt eller fiktivt undantag från standard. Skriv ner:

- varför undantaget behövs,
- vilken risk det skapar,
- vem som bör acceptera risken,
- hur länge undantaget ska gälla,
- vilken åtgärd som skulle göra undantaget onödigt.

## Beslut att fatta

- Vilka säkerhetskrav ska vara obligatoriska för alla plattformstjänster?
- Vilka krav ska byggas in i mallar, pipelines, behörigheter, loggning och plattform?
- Vilka kontroller ska vara automatiska, och vilka kräver manuell bedömning?
- Vilka standardfall ska kunna hanteras genom självservice?
- Vilka säkerhetsbeslut kräver spårbar riskacceptans på ledningsnivå?
- Hur ska undantag dokumenteras, tidsbegränsas och följas upp?
- Hur ska säkerhetsteamets roll förändras från granskande funktion till kravägare, rådgivare och möjliggörare?

Ett användbart ledningsbeslut kan formuleras så här:

> Vi ska öka självservice genom att bygga in säkerhetskrav i plattform och leveransflöden. Standardfall ska kunna gå snabbt inom godkända guardrails. Avvikelser ska hanteras genom spårbar riskacceptans, inte genom informella genvägar.

Det beslutet är inte en teknisk lösning. Det är en riktning som gör tekniska lösningar möjliga.

## Snabb sammanfattning

- Säkerhet behöver byggas in i plattform och leveransflöden när förändringstakten ökar.
- Guardrails ger team frihet inom säkra och accepterade ramar.
- Policy-as-code gör vissa krav automatiskt testbara och spårbara.
- Inbyggd kontroll betyder att kontrollen sker i det normala arbetssättet, inte bara som efterhandsgranskning.
- Säkerhetsteamets roll förändras från återkommande manuell granskning till kravägarskap, rådgivning och design av kontroller.
- Självservice kräver nivåer, standardfall och en tydlig undantagsprocess.
- Ledningen måste besluta vilken risknivå som accepteras och vilka säkerhetskrav som ska vara obligatoriska.

## Kontrollfrågor

1. Vilka säkerhetskontroller i er organisation sker sent i flödet i dag?
2. Vilka av dessa kontroller skulle kunna flyttas tidigare eller automatiseras?
3. Vilka krav är för otydliga för att kunna automatiseras just nu?
4. Vilka standardfall skulle ledningen kunna godkänna för självservice?
5. Hur hanteras undantag i dag: som spårbara beslut eller som informella genvägar?
6. Vilka säkerhetsbeslut försöker ni i dag lösa tekniskt, trots att de kräver ledningsmandat?

## Nästa steg

Säkerhet är en central del av kontrollen, men den är inte den enda. En självservicemodell måste också vara driftbar, robust och tillgänglig. I nästa kapitel går vi därför vidare till kvalitet, tillgänglighet och robusthet: vad måste vara standardiserat innan team kan få mer frihet i produktionsnära miljöer?
