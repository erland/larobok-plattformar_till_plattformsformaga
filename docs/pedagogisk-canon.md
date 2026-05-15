# Pedagogisk canon

## Bokens interna sanning

Boken handlar om att bygga ledningsförmåga för modern plattformsleverans i stora reglerade organisationer. Containerplattformen är en katalysator, inte huvudpersonen.

## Pedagogisk profil
- Språk: Svenska.
- Svårighetsgrad: Erfaren.
- Läsarprofil: Chef eller ledare med ansvar för produktion, utveckling, säkerhet, arkitektur, förvaltning eller plattform.
- Ton: Rådgivande, handlingsdriven och professionell.
- Repetitionstakt: Begrepp repeteras när de används i nya målkonflikter.

## Återkommande scenario
- Namn: Myndigheten för Samhällstjänst.
- Syfte: Illustrera realistiska målkonflikter utan att peka ut en faktisk organisation.
- Regler: Scenariot ska visa flera perspektiv rättvist. Ingen funktion ska beskrivas som ensam orsak till problemen.
- Hittills använda delar: Säkerhetsteam, driftorganisation, utvecklingsteam, ledning, miljöbeställningar, containerinitiativ, ledningens målbildsarbete, beslut om OpenShift-liknande plattform, produktifiering av återkommande miljöbehov samt ledningsbeslut om mandat och riskacceptans, samt inbyggd säkerhetsstyrning med guardrails, policy-as-code och automatiserade kontroller, samt operativa minimikrav för driftbarhet, robusthet och produktionsnära självservice, samt vägval mellan greenfield, brownfield och risken för parallell organisation, samt övergångsarkitektur, samexistens och migreringsprinciper för gammalt och nytt, samt styrning, finansiering, plattformsekonomi, produktägarskap och kapacitetsstyrning, samt införandestrategi med pilot, förmågetrappa och normalisering.
- Metodstil: Beskriv situation, synliggör målkonflikt, ge ledningsrekommendation, avsluta med reflektionsfrågor.

## Introducerade begrepp
- Plattformsförmåga: Organisationens samlade förmåga att erbjuda standardiserade, säkra och användbara plattformstjänster.
- Lokal optimering: När en funktion förbättrar sin egen vardag på ett sätt som kan försämra helheten.
- Beställningsflöde: Ett arbetssätt där team begär miljöer eller förändringar som andra funktioner tolkar, koordinerar, kvalitetssäkrar och utför.
- Målkonflikt: En situation där två legitima mål drar åt olika håll, till exempel snabbhet och kontroll.
- Organisationsagilitet: Organisationens förmåga att snabbt och säkert anpassa sig över funktionsgränser.
- Förändringskapacitet: Hur mycket säker och värdeskapande förändring organisationen klarar över tid.
- Styrbar snabbhet: Förmågan att öka leveranshastigheten inom tydliga ramar.
- Containerplattform: Teknisk plattform för att köra, hantera och drifta containerbaserade applikationer.
- Strategisk plattform: Plattform som organisationen medvetet använder för att förändra leverans, styrning, säkerhet och drift.
- Operativ modell: Beskrivning av hur organisationen arbetar runt plattformen i vardagen, inklusive ansvar, prioritering, kontroller och undantag.
- Platform engineering: Arbetssätt där en intern plattform byggs och förvaltas som produkt för interna användare.
- Självservice: Team kan utföra standardiserade åtgärder själva inom definierade, spårbara och godkända ramar.
- Intern produkt: Intern tjänst eller förmåga med målgrupp, ägare, värde, livscykel och prioriterad utveckling.

- Mandat: Rätten att fatta vissa beslut och förväntan att ta ansvar för konsekvenserna.
- Riskacceptans: Ett medvetet ledningsbeslut om vilken risknivå som accepteras, under vilka villkor och med vilken uppföljning.
- Styrningsprincip: En gemensam regel eller riktning som hjälper organisationen att fatta många vardagsbeslut konsekvent.
- Guardrails: Fördefinierade ramar som gör det möjligt för team att agera fritt inom säkra och accepterade gränser.
- Policy-as-code: Säkerhets- eller styrningsregler uttryckta så att de kan versionshanteras och kontrolleras automatiskt.
- Inbyggd kontroll: Kontroll som är en del av det normala arbetssättet, exempelvis i plattform, pipeline, mall eller övervakning.
- Driftbarhet: Förmågan att förstå, övervaka, felsöka, återställa och förvalta en tjänst i produktion.
- Robusthet: Förmågan att tåla störningar, fel och förändringar utan att helheten blir instabil.
- Operativa minimikrav: Miniminivå av drift- och kvalitetskrav som måste uppfyllas för en viss miljö eller risknivå.
- Produktionsskuld: Operativa svagheter som gör tjänster svåra att äga, förstå, övervaka och förändra över tid.
- Greenfield: Att skapa en ny lösning, plattform eller organisation med få direkta beroenden till befintligt arv.
- Brownfield: Att förändra befintlig organisation, befintliga system och befintliga beroenden stegvis.
- Parallell organisation: När en ny satsning byggs bredvid den befintliga utan tydlig plan för integration, normalisering och gemensamt ansvar.


- Gemensam spelplan: Överenskommen ledningsmodell för hur organisationen utvecklar och använder sin plattformsförmåga.
- Beslutsramverk: Praktisk struktur för vilka beslut som ska fattas, vem som ska fatta dem och vilka kriterier som ska användas.
- Förmågekarta: Översikt över organisatoriska förmågor som behövs för att målbilden ska fungera i praktiken.

## Versions- och faktaval
Exempel på tekniker: OpenShift, JBoss EAP, IBM MQ, Oracle Database, Elasticsearch och Ceph. Boken anger inte versionsspecifika rekommendationer utan markerar tekniska detaljer som behöver verifieras mot officiell dokumentation om de används i operativa beslut.

## Kontinuitetsregler
- Myndigheten för Samhällstjänst används konsekvent som scenario.
- Boken ska undvika att skuldbelägga utveckling, drift eller säkerhet.
- Varje kapitel ska tydligt koppla till ledningens ansvar.
- Kapitel ska introducera få huvudbegrepp och använda dem i praktiska chefsbeslut.

- Övergångsarkitektur: Den medvetna designen av hur gamla och nya plattformar, arbetssätt, ansvar och kontroller ska fungera tillsammans under en övergångsperiod.
- Samexistens: När gamla och nya lösningar används samtidigt, med avsiktliga kopplingar, tydliga regler och känt ansvar.
- Migreringsprincip: Ledningsregel för hur organisationen avgör vad som ska flyttas, när det ska flyttas och varför.

- Plattformsekonomi: Hur organisationen förstår, finansierar och följer upp kostnader och nytta för en intern plattformsförmåga.
- Produktägarskap: Ansvar för plattformens värde, användare, prioriteringar, utveckling och livscykel som intern produkt.
- Kapacitetsstyrning: Medveten styrning av hur plattformsorganisationens kapacitet fördelas mellan utveckling, stabilitet, support, riskreducering och avveckling.

- Pilot: Avgränsat införandesteg där organisationen prövar teknik, arbetssätt, ansvar och styrning i en verklig men kontrollerad situation.
- Förmågetrappa: Stegvis plan för hur organisationen ökar sin plattformsförmåga över tid.
- Normalisering: När ett nytt arbetssätt slutar vara experiment, undantag eller projekt och blir del av ordinarie leveransmodell.
