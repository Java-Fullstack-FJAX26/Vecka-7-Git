# Boilerroom v.7 – Projektbeskrivning och Task-hierarki (BorrowBook)

Detta dokument utgör specifikationen för **Boilerroom v.7**.

I denna sprint lanseras **inga nya funktionsfeatures**. Istället har kunden lagt en beställning på fokuserad **minskning av teknisk skuld, höjning av kodkvaliteten, utökad testtäckning samt arkitektonisk och strukturell upprensning** i projektet.

Arbetet organiseras i **en övergripande Refaktoreringsstory** innehållande **tre öppna features**. Till skillnad från tidigare versioner är dessa tre features definierade på featurenivå utan spikade undertasks. Det ger teamen full frihet och eget ansvar att själva identifiera svagheter i sin källkod, planera förbättringarna och bryta ned arbetet i konkreta tasks i sin egen Kanban-tavla och i tillhörande Pull Requests.

Dokumentet inleds i **Del 1** med ett komplett index över alla tidigare genomförda stories, features och tasks (v.1–v.6) som referens och baslinje, följt av **Del 2** som specificerar de tre öppna refaktoreringsfeaturesen för Boilerroom v.7.

---

## 📋 Del 1: Index över alla tidigare Stories, Features & Tasks (v.1 – v.6)

### 🔹 Story A1: Som en administratör vill jag kunna lägga till nya ledare...
* **Feature A1.1 – Hantera ledare** (Task A1.1.1, Task A1.1.2, Task A1.1.3)

### 🔹 Story A2: Som en administratör vill jag kunna lägga till nya föremål...
* **Feature A2.1 – Hantera utrustning** (Task A2.1.1, Task A2.1.2, Task A2.1.3)
* **Feature A2.2 – Utrustningskategorier** (Task A2.2.1, Task A2.2.2)
* **Feature A2.3 – Utökad resursinformation** (Task A2.3.1, Task A2.3.2, Task A2.3.3)
* **Feature A2.4 – Hantera resursstatus** (Task A2.4.1, Task A2.4.2, Task A2.4.3)
* **Feature A2.5 – Leverantörs- eller tillverkarinformation** (Task A2.5.1, Task A2.5.2)
* **Feature A2.6 – Refaktorering: Modernisering av Resurs- och Ledarhantering (v.5)** (Task A2.6.1)
* **Feature A2.7 – Expansionsfeature: Dynamisk Resursutskrotning & Garantispårning (v.5)** (Task A2.7.1)

### 🔹 Story L1: Som en ledare vill jag kunna se vilka resurser som finns tillgängliga...
* **Feature L1.1 – Översikt över resurser** (Task L1.1.1, Task L1.1.2, Task L1.1.3)
* **Feature L1.2 – Förbättrad resursöversikt** (Task L1.2.1, Task L1.2.2, Task L1.2.3)
* **Feature L1.3 – Mest använda resurser** (Task L1.3.1, Task L1.3.2, Task L1.3.3)
* **Feature L1.4 – Streams-baserad statistik och nyttjanderapportering (v.4)** (Task L1.4.1, Task L1.4.2, Task L1.4.3)
* **Feature L1.5 – Refaktorering: Förenkling av Rapport- och Analyslogiken (v.5)** (Task L1.5.1)
* **Feature L1.6 – Expansionsfeature: Interaktiv Exporthantering & CSV-rapporter (v.5)** (Task L1.6.1)

### 🔹 Story M1: Som en medlem vill jag kunna se vilka resurser som går att låna...
* **Feature M1.1 – Söka resurser** (Task M1.1.1, Task M1.1.2, Task M1.1.3)
* **Feature M1.2 – Förbättrad sökning** (Task M1.2.1, Task M1.2.2, Task M1.2.3)
* **Feature M1.3 – Kombinerad filtrering** (Task M1.3.1, Task M1.3.2, Task M1.3.3)
* **Feature M1.4 – Favoriter** (Task M1.4.1, Task M1.4.2, Task M1.4.3)
* **Feature M1.5 – Flexibel sortering av resurser (v.3)** (Task M1.5.1, Task M1.5.2, Task M1.5.3)
* **Feature M1.6 – Funktionell filtrering och sökmotor (v.3)** (Task M1.6.1, Task M1.6.2)
* **Feature M1.7 – Refaktorering: Sök- och Sorteringsarkitektur (v.5)** (Task M1.7.1)
* **Feature M1.8 – Expansionsfeature: Smarta Resursrekommendationer (v.5)** (Task M1.8.1)

### 🔹 Story ML1: Som medlem eller ledare vill jag kunna se information om en bokning...
* **Feature ML1.1 – Bokningsöversikt** (Task ML1.1.1, Task ML1.1.2, Task ML1.1.3)
* **Feature ML1.2 – Hantera bokningshistorik** (Task ML1.2.1, Task ML1.2.2)
* **Feature ML1.3 – Mina bokningar** (Task ML1.3.1, Task ML1.3.2, Task ML1.3.3)
* **Feature ML1.4 – Bokningshistorik per medlem** (Task ML1.4.1, Task ML1.4.2, Task ML1.4.3)
* **Feature ML1.5 – Avancerad händelseanalys och säker sökning med Optional (v.4)** (Task ML1.5.1, Task ML1.5.2)
* **Feature ML1.6 – Refaktorering: Kraschfri Bokningshantering & Immutabilitet (v.5)** (Task ML1.6.1)
* **Feature ML1.7 – Expansionsfeature: Bokningsförlängning & Om-bokning (v.5)** (Task ML1.7.1)

### 🔹 Story A3: Som administratör vill jag kunna följa aktiviteter i systemet...
* **Feature A3.1 – Aktivitetshistorik** (Task A3.1.1, Task A3.1.2, Task A3.1.3)
* **Feature A3.2 – Senaste aktiviteter** (Task A3.2.1, Task A3.2.2)
* **Feature A3.3 – Refaktorering: Strukturering av Logg- och Auditsystemet (v.5)** (Task A3.3.1)

### 🔹 Story A4: Som administratör vill jag kunna styra bokningsregler...
* **Feature A4.1 – Begränsa antal aktiva bokningar** (Task A4.1.1, Task A4.1.2, Task A4.1.3)
* **Feature A4.2 – Förhindra dubbelbokningar** (Task A4.2.1, Task A4.2.2, Task A4.2.3)
* **Feature A4.3 – Hantera resurser som inte är tillgängliga** (Task A4.3.1, Task A4.3.2, Task A4.3.3)
* **Feature A4.4 – Funktionell regelvalidering för bokningar (v.3)** (Task A4.4.1, Task A4.4.2)
* **Feature A4.5 – Anpassad domänfelhantering och valideringsinfrastruktur (v.4)** (Task A4.5.1, Task A4.5.2)
* **Feature A4.6 – Refaktorering: Eliminering av Arrow Anti-Pattern i Regelmotorn (v.5)** (Task A4.6.1)

### 🔹 Story A5: Som administratör vill jag ha automatisk notifiering och händelseloggning (v.4)
* **Feature A5.1 – Händelsedriven notifiering / Observer Pattern (v.4)** (Task A5.1.1, Task A5.1.2)
* **Feature A5.2 – Refaktorering: Felisolering i Händelsepubliceraren Pub/Sub (v.5)** (Task A5.2.1)

### 🔹 Infrastruktur (v.1 – v.6)
* **Infrastruktur 1 – Repository** (Task I1.1, Task I1.2, Task I1.3, Task I1.4.1, Task I1.4.2, Task I1.5.1)
* **Infrastruktur 2 – Projektstruktur** (Task I2.1, Task I2.2, Task I2.3, Task I2.4.1, Task I2.4.2)
* **Infrastruktur 3 – Tester** (Task I3.1, Task I3.2, Task I3.3)
* **Infrastruktur 4 – Kodkvalitet & Mönster** (Task I4.1, Task I4.2, Task I4.3, Task I4.5.1, Task I4.6.1, Task I4.7.1, Task I4.7.2)

---

## 🚀 Del 2: Kundbeställd Refaktorering & Kvalitetshöjning – Boilerroom v.7

*I Boilerroom v.7 har kunden beställt tre övergripande refaktoreringsfeatures under en samlad kvalitetssatsning. Inga nya funktionsfeatures läggs till. Teamen har full frihet att identifiera brister i sin kodbas och självständigt bryta ned dessa tre features till tasks i sin Kanban-tavla.*

---

### 🏛️ Story R1 (Refaktoreringsstory): Som beställare vill jag minska den tekniska skulden och stärka systemets underhållbarhet

#### Feature R1.1 – Kundbeställd minskning av teknisk skuld (Technical Debt Reduction)
* **Syfte:** Identifiera, eliminera och dokumentera strukturella kodlukter (*Code Smells*) i källkoden för att sänka den framtida underhållskostnaden.
* **Beskrivning:** Kunden kräver en genomgripande sanering av kodbasen. Teamet identifierar områden drabbade av t.ex. *Arrow Anti-Pattern* (djupa nästlade -satser), *Long Method*, *Duplicate Code*, *Magic Numbers*, *Primitive Obsession* eller sväljda exceptions.
* **Krav:**
  * Teamet identifierar själva minst 2–3 betydande kodlukter i sin källkod.
  * Koden refaktoreras till renare uttryck (t.ex. linjära Guard Clauses, bruthna hjälpmetoder, enums eller immutabla Records).
  * Teamet äger nedbrytningen till konkreta tasks (t.ex. , ) i sin egen backlog.

#### Feature R1.2 – Förbättring av testtäckning och regressionsskydd (Test Suite & Regression Enhancement)
* **Syfte:** Bygga ett heltäckande och pålitligt säkerhetsnät av automatiserade JUnit 5-tester som garanterar att systemets yttre funktion förblir oförändrad vid refaktorering.
* **Beskrivning:** Kunden vill säkerställa att inga buggar introduceras. Teamet kompletterar med enhetstester, gränsvärdestester, integrationstester (t.ex. med  för filinläsning/persistering) och verifierar täckning på refaktorerade moduler.
* **Krav:**
  * Alla tester följer principen *"Never refactor without green tests"*.
  * Täckningen höjs på kritiska domän- och servicelager.
  * Teamet bryter fritt ned arbetet till enskilda test-tasks i teamets Kanban-tavla.

#### Feature R1.3 – Arkitektonisk upprensning, modulmönster och dokumentation (Architectural Cleanup & Refactoring)
* **Syfte:** Stärka den övergripande arkitekturen, renodla skiktningen mellan servicelager och persistering samt dokumentera tekniska val.
* **Beskrivning:** Kunden har beställt en arkitektonisk upprensning där svagt strukturerade klasser och beroenden rätas ut. Teamet kan tillämpa lämpliga designmönster (t.ex. *Strategy*, *Observer*, *Factory*, *Singleton* eller *Repository*) där det ger mervärde, samt dokumentera beslut i källkod och Pull Request-beskrivningar.
* **Krav:**
  * Frikoppla hårt bundna moduler och avskärma datalagret från affärslogik.
  * Dokumentera mönstervetenskap och refaktoreringsmotiveringar i Pull Requests och källkod.
  * Teamet definierar själv sina deluppgifter och koordinerar mergningar via Feature Branches.
