## Översikt över kursvecka 7

[Självstudier i eget dokument](https://github.com/Java-Fullstack-FJAX26/Vecka-7-Git/blob/main/Sjalvstudier_vecka7_Git)

[Workshop 13 - Grunder Git finns i eget dokument](https://github.com/Java-Fullstack-FJAX26/Vecka-7-Git/blob/main/Workshop_13_Git_Verkstad.md)

[Workshop 14 - Fortsättning Git samt övning i refaktorering och code review](https://github.com/Java-Fullstack-FJAX26/Vecka-7-Git/blob/main/Workshop_14_Git_Verkstad.md)

De individuella övningarna i egen branch nedan, de är till för dig som inte jobbat med git innan utbildningen och bör göras innan torsdag 26/11.
[Individuella övningar på grundnivå för dig som ej har jobbat i git]([https://github.com/Java-Fullstack-FJAX26/Vecka-7-Git/tree/%C3%B6vningar](https://github.com/Java-Fullstack-FJAX26/Vecka-7-Git/tree/ovningar))

# Teorigenomgång – Vecka 7: Git, GitHub & Teamarbete

## 1. Veckoöversikt: Arbetsflöde & GitHub-material

Vecka 7 fokuserar på praktisk versionshantering och strukturerat teamsamarbete med **Git** och **GitHub**. I takt med att kodbasen växer i era projekt blir det avgörande att flera utvecklare kan arbeta parallellt i samma kodbas utan att skriva över varandras ändringar eller skapa oordning i huvudgrenen.

### Övningsmaterial på GitHub
Huvuddelen av veckans övningsmaterial och källkod finns publicerat direkt i kursens GitHub-repository (`Vecka-7-Git`). 

* **Huvudgrenen (`main`):** Innehåller grundläggande struktur och gemensamma projektfiler.
* **Övningsmappen (`ovningar/`):** Övningarna är grundläggande övningar i gits funktioner för versionshantering.

### Veckans Mål
Efter veckans studier och praktiska övningar ska du kunna:
* Förklara Gits interna trestegsmodell (Working Directory, Staging Area, Local Repository).
* Tillämpa ett isolerat grenbaserat arbetsflöde med korta **Någon av de olika branchingstrategierna**.
* Identifiera, analysera och systematiskt lösa **merge conflicts** i Java-källkod.
* Genomföra strukturkritiska **Code Reviews** och hantera **Pull Requests** på GitHub.


---

## 2. Teorigenomgång: Versionshantering och Samarbete i Git

### 2.1 Grundläggande Versionshantering & Gits Arkitektur

Git är ett **distruerat versionshanteringssystem** (DVCS). Till skillnad från äldre centraliserade system (som SVN) har varje utvecklare en komplett kopia av hela projektets historik lokalt på sin egen dator. Detta gör operativt arbete snabbt och oberoende av nätverksuppkoppling.

```
+------------------+        git add       +------------------+       git commit      +------------------+
|                  | -------------------> |                  | --------------------> |                  |
| Working Directory|                      |   Staging Area   |                       | Local Repository |
| (Filer på disk)  | <------------------- |     (Index)      |                       |  (Lokal historik)|
+------------------+     git checkout     +------------------+                       +------------------+
                                                                                              |
                                                                                              | git push / pull
                                                                                              v
                                                                                     +------------------+
                                                                                     | Remote Repository|
                                                                                     |     (GitHub)     |
                                                                                     +------------------+
```

#### Gits tre tillstånd lokalt

För att förstå hur Git spårar ändringar behöver man känna till de tre lokala områdena:

1. **Working Directory (Arbetskatalog):** De faktiska filerna på din hårddisk där du skriver och redigerar din Java-kod i din IDE.
2. **Staging Area (Index):** Ett mellanlager där du samlar och förbereder de ändringar som ska ingå i nästa historikpunkt. Genom `git add` väljer du exakt vilka filer eller rader som ska paketeras.
3. **Local Repository (Lokalt arkiv):** Den lokala databasen i `.git`-mappen där Git lagrar projektets historik som en kedja av *commits*.

#### Vad är en Commit?

En **commit** representerar en ögonblicksbild (snapshot) av hela projektet vid en specifik tidpunkt. 
* **Immutabilitet:** Varje commit identifieras av en unikt beräknad SHA-hash (t.ex. `4a1f8b2...`). Om innehållet ändras, ändras också hashen.
* **Pekare och HEAD:** `HEAD` är en intern pekare i Git som visar vilken gren och commit du för närvarande arbetar utifrån i din arbetskatalog.

---

### 2.2 Branching & Merging i Praktiken

En av Gits största styrkor är snabb och billig **branching** (grenhantering). En gren (*branch*) i Git är i princip bara en rörlig pekare till en specifik commit.

```
          Feature Branch: feature/equipment-discount
         o-------o-------o (din nyfunktionalitet)
        /
---o---o-------------------o (main)
  (stabil historik)
```

#### Varför korta Feature Branches?

Att commita direkt till `main`-grenen i ett team skapar stor felrisk. Om en utvecklare checkar in trasig kod drabbas hela teamet omedelbart. 

Genom att skapa korta **Feature Branches** (t.ex. `feature/leader-validation` eller `bugfix/null-pointer-fix`):
* Isolerar du ditt arbete tills det är färdigbyggt och verifierat med enhetstester.
* Kan flera utvecklare arbeta samtidigt på helt olika delar av domänmodellen.
* Hålls `main`-grenen alltid i ett stabilt, körbart och testat tillstånd.

#### Grundläggande Git-kommandon för Grenhantering

| Handling | Kommando | Beskrivning |
| :--- | :--- | :--- |
| **Skapa och växla till gren** | `git switch -c feature/my-task` | Skapar en ny gren och växlar direkt till den. |
| **Visa aktiva grenar** | `git branch` | Listar alla lokala grenar och markerar den aktiva. |
| **Växla mellan grenar** | `git switch main` | Växlar tillbaka till den angivna grenen. |
| **Slå ihop grenar (Merge)** | `git merge feature/my-task` | Slår ihop koden från målfilen in i den gren du står i. |
| **Ta bort avslutad gren** | `git branch -d feature/my-task` | Raderar den lokala grenen efter godkänd merge. |

---

### 2.3 Hantering av Merge Conflicts

En **merge conflict** (ihopslagningskonflikt) uppstår när Git inte automatiskt kan avgöra vilken kodrad som är den korrekta. Det inträffar oftast när två utvecklare har ändrat **samma rad i samma fil** på två olika grenar sedan grenarna delade sig, och båda försöker slås ihop med `main`.

#### Hur en Merge Conflict ser ut i Java-kod

När en konflikt uppstår avbryter Git ihopslagningen och förser den berörda filen med konfliktmarkörer:

```java
public double calculateFee(Equipment item) {
<<<<<<< HEAD (Koden på den gren du står på, t.ex. main)
    return item.getDailyRate() * 1.25; // Inklusive moms
=======
    if (item.isDiscounted()) return item.getDailyRate() * 0.90; // Rabatterat pris
>>>>>>> feature/equipment-discount (Koden på grenen som dras in)
}
```

#### Metodik för att Lösa Konflikter Systematiskt

1. **Identifiera alla konflikter:** Kör `git status` för att se vilka filer som är markerade som *Unmerged*.
2. **Öppna i IDE eller Textredigerare:** Gå igenom varje konfliktmarkör (`<<<<<<<`, `=======`, `>>>>>>>`).
3. **Välj rätt kod:** Rensa bort markörerna manuellt och kombinera koden så att den speglar det tänkta beteendet.
4. **Verifiera bygget:** Kör projektets enhetstester (`mvn test` eller via IDE) för att säkerställa att ingenting har gått sönder!
5. **Markera som löst:** Kör `git add <filnamn>` för att meddela Git att konflikten är hanterad.
6. **Färdigställ mergen:** Kör `git commit` för att slutföra ihopslagningen.

---

### 2.4 Agilt Samarbete på GitHub: Pull Requests & Code Review

När du arbetar i team sker ihopslagningen till `main` sällan lokalt på din egen dator. I stället används **Pull Requests (PR)** på GitHub.

#### Pull Request (PR)-flödet

En Pull Request är ett formellt sätt att be teamet granska och godkänna dina ändringar innan de mergas in i huvudprojektet.

```
Utvecklare pushar branch  ──>  Skapar Pull Request  ──>  Kamrat gör Code Review  ──>  Merge till main
(git push origin feature)      (Beskriv funktion & task)  (Granskar & kommenterar)   (Automatisk / Manuell)
```

#### Vad ska du kontrollera vid en Code Review?

Att granska en kamrats PR är inte bara en kontroll för fel – det är ett utmärkt tillfälle för kunskapsutbyte i teamet. När du gör en Code Review bör du titta på följande tre aspekter:

1. **Funktionalitet och Krav:** Löser koden den avsedda uppgiften? Uppfylls kraven i tillhörande Issue eller Task?
2. **Kodkvalitet och Läsbarhet:** Följer koden teamets namngivningskonventioner? Finns det kodlukter (t.ex. *Long Method* eller djupa nästlingar)? Finns det tillräckligt med Guard Clauses?
3. **Tester och Regressionsskydd:** Finns det täckande JUnit 5-tester för den nya logiken? Körs alla tester och blir gröna?

#### GitHub Issues & Projects (Kanban)

För att hålla spårbarhet i agila projekt samverkar GitHubs verktyg:
* **GitHub Issues:** Beskriver en enskild uppgift, funktion eller bugg.
* **GitHub Projects:** En Kanban-tavla som visar uppgifter i kolumner som *Todo*, *In Progress*, *In Review* och *Done*.
* **Koppling:** När du skapar en PR kan du använda nyckelord i beskrivningen (t.ex. `Closes #12`), vilket gör att tillhörande Issue automatiskt stängs och flyttas till *Done* när PR:en mergas.

---

### 2.5 Git-konventioner & Best Practices i Java-projekt

För att behålla en ren historik och förhindra onödiga konflikter bör alla teammedlemmar följa några etablerade standarder:

#### 1. Använd en noggrann `.gitignore`
Genererade filer och lokala IDE-inställningar ska **aldrig** commitas till Git. Skapa en `.gitignore`-fil i projektroten:

```gitignore
# Kompilerad Java-kod
*.class
target/
build/

# IDE- och utvecklarfiler
.idea/
*.iml
.vscode/
.DS_Store
```

#### 2. Skriv Tydliga Commit-meddelanden
Ett commit-meddelande ska förklara *vad* och *varför* ändringen gjordes.
* **Bra:** `Add Guard Clause for underage borrowers in LoanService`
* **Dåligt:** `fix`, `ändrat lite kod`, `wip`

#### 3. Dra in `main` i din gren *före* Pull Request
Innan du skapar eller uppdaterar en PR är det en god vana att växla till `main`, göra `git pull`, växla tillbaka till din feature branch och köra `git merge main`. 

Om det finns några konflikter löser du dem lokalt på din egen gren och testar koden noggrant **innan** du ber dina teamkamrater om en granskning!

