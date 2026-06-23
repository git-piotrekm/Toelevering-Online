# AI Scan — Zespół Product & Tech

## Propozycja audytu i planu wdrożenia

---

### Punkt wyjścia

AI w developmencie już u Was działa — i to dobra wiadomość. Ludzie chcą, używają, generują kod. Zespół jeździ na różnych narzędziach (Claude Code, Cursor, Junie w PHPStorm/IntelliJ), front-end generuje większość kodu przez AI, na pipelinie działa agent do review. Adopcja jest faktem.

To, czego brakuje, to nie chęci — to spójności. Każdy pracuje po swojemu, nie ma polityki narzędziowej ani kontroli kosztów tokenów (ludzie wpadają w tygodniowe limity), a code review zaczyna boleć. To dokładnie ten moment, w którym sami byliśmy przy 120 developerach — żadne dwie osoby nie pracowały na tym samym zestawie narzędzi.

Ale zanim cokolwiek zaproponujemy, chcemy posłuchać. **Nie wierzymy w gotowe recepty wdrażane z zewnątrz.** Każdy zespół jest inny, a nawet pod każdy framework podejście do AI wygląda inaczej. Nie ma opcji one-size-fits-all — i każdy, kto twierdzi inaczej, sprzedaje slajd, nie rozwiązanie.

---

### Jak do tego podchodzimy

Zaczynamy od wywiadu. Przeprowadzimy rozmowy z developerami — albo z całym przekrojem, albo z wybranymi członkami core teamu, którzy są w stanie wypowiedzieć się w imieniu szerszej grupy. Celem jest jedno: **zidentyfikować realne bolączki w AI productivity** — nie te, które wyglądają źle na papierze, tylko te, które faktycznie spowalniają ludzi.

Dopiero na tej podstawie projektujemy plan zmian. Wnioski z wywiadu decydują o tym, które z poniższych ścieżek w ogóle są dla Was istotne. Niektóre mogą okazać się nieistotne. Inne — kluczowe. Tego nie da się ustalić bez rozmowy.

---

### Zmiana ramy: duże PR-y to nie problem

Warto od razu ustawić jedno założenie, bo często bywa odwrócone.

Ilość generowanego kodu i wielkie PR-y to **nie minus korzystania z AI — to pozytywna codzienność.** AI produkuje dużo, i tak ma być. Problemem nie jest wolumen. Problemem bywa brak zaufania do tego, co AI wyprodukowało.

Jeśli to zaufanie kuleje, nie patrzymy na rozmiar PR-a — patrzymy na **workflow testowania i weryfikacji działania.** Bo to jest właściwe miejsce, w którym buduje się zaufanie do kodu AI.

Z tego wynika konkretna zasada pracy: **dev powinien oceniać core i decyzje architektoniczne, a nie czytać kod linia po linii.** Jeśli ktoś nadal czyta każdą linię wygenerowanego kodu, to znak, że albo brakuje warstwy testów, która by go w tym wyręczyła, albo zadania są zbyt duże i generują więcej kodu, niż da się sensownie ogarnąć w jednym przejściu.

Której z tych przyczyn dotyczy Wasz przypadek — bez wywiadu nie ustalimy. I to jest właśnie powód, dla którego zaczynamy od słuchania, a nie od wdrażania.

---

### Potencjalne ścieżki rozwiązań

Poniższe to **opcje, nie gotowy plan.** Które z nich wejdą do wdrożenia, zależy od tego, co wyjdzie z wywiadów. Każda odpowiada na inną, konkretną bolączkę.

#### 1. Brak workflowów testowych → zbudować zaufanie do kodu AI

Jeśli zespoły nie mają poukładanych workflowów pod unit testy, Playwright czy QA, to warto zacząć właśnie tu — zanim ruszymy cokolwiek innego.

Sprawdziliśmy to na własnych zespołach: **jeśli testy są zielone, nie musimy oceniać code review tak szczegółowo.** Skupiamy się na architekturze, nie na składni. Wtedy ilość generowanego kodu przestaje przerażać — bo zielony pakiet testów jest gwarancją, której nie da czytanie diffa linia po linii.

To jest fundament. Bez warstwy testowej każda inna optymalizacja stoi na piasku.

#### 2. Niezadowolenie z jakości kodu → nakierować AI na etapie developerki

Jeśli zespół nie jest zadowolony z jakości kodu, albo kod za bardzo różni się od pliku do pliku, to problem leży wcześniej niż w review — leży w tym, _jak_ AI dostaje zadanie.

Możemy przygotować analizę workflowów, które już na etapie developerki nakierują AI na lepszy, spójniejszy kod, trzymający się ustalonych reguł projektu. Mamy do tego własny framework — **TaskForge** — który mocno pomaga w tworzeniu planu integracji dla AI w zgodzie z regułami projektu. W kilku naszych projektach developerzy bardzo go sobie chwalą.

Ale TaskForge nie pasuje do każdego zespołu ani każdego stacku. Jeśli nie zarezonuje, sprawdzimy, czy lepiej leżą metodologie **spec-driven** (Spec Kit, Shotgun). Wybór zależy od tego, jak zespół pracuje — nie od tego, co my preferujemy.

#### 3. Przepalane tokeny i limity → wyrównanie wiedzy + przegląd planów

Jeśli zespół czuje, że tokeny palą się bez kontroli i ludzie często trafiają w limity, składają się na to zwykle dwie rzeczy: wiedza i plan subskrypcji.

Po stronie wiedzy: możemy zorganizować **1-godzinne spotkanie wyrównujące** — top triki dla Claude Code, jak działać z context engineeringiem, jak nie palić tokenów na rzeczach, które tego nie wymagają. Z doświadczenia część "limitów" to kwestia higieny pracy, nie brak budżetu.

Po stronie planów: z doświadczenia wiemy, że **abonament $20/mies. na osobę to często za mało.** Ponad połowa naszej firmy jest na wyższych tierach albo na multi-subskrypcjach. Możliwą odpowiedzią jest scentralizowany system — wersja Teams lub organizacyjna — dający jedną fakturę i kontrolę zużycia.

Modele lokalne mogą z czasem być odpowiedzią na koszty, ale jesteśmy tu w fazie raczkującej tej alternatywy. Na dziś **frontier modele i dobre IDE po prostu robią robotę** — i to one dają realny zwrot.

#### 4. Nadmierne planowanie → mniejsze, seniorskie zespoły

Możliwe, że odpowiedzią na lepszą efektywność nie jest żadne narzędzie, tylko struktura zespołu.

Wielokrotnie udowodniliśmy, że **seniorski zespół 2–3 osobowy dawał lepsze i szybsze rezultaty niż zespół 6+.** AI sprawia, że kilkuosobowy team potrafi skupić się nad jednym tematem i skutecznie dowieźć kod, bez narzutu nadmiernego planowania i koordynacji.

To, co wtedy zostaje do dopięcia, to komunikacja pomiędzy tymi mini-zespołami — żeby ich kawałki się zintegrowały. I to jest dużo łatwiejszy problem do rozwiązania niż koordynacja wewnątrz jednego dużego zespołu.

---

### Co dostajecie

Wysłuchamy zespół, wyciągniemy wnioski i przygotujemy **raport z rekomendacjami best practices** do wdrożenia — dobranymi do tego, co faktycznie wyszło z rozmów, a nie do gotowej listy.

W praktyce raport może objąć:

- **Mapę stanu obecnego** — kto czego używa, co przyspiesza, co generuje tarcia.
- **Rekomendacje warsztatu testowego / QA** — jeśli to tam leży brak zaufania do kodu AI.
- **Propozycję workflowów nakierowujących AI** (TaskForge lub spec-driven) — jeśli problemem jest jakość i spójność kodu.
- **Przegląd kosztów i planów subskrypcji** + spotkanie wyrównujące wiedzę — jeśli bolą tokeny i limity.
- **Rekomendację struktury zespołów** — jeśli wąskim gardłem jest planowanie i koordynacja.

Co ważne: **czasami to nie jest kwestia samego rozwiązania AI, tylko przygotowania zespołu pod większą produktywność.** Bywa, że najlepszym deliverable nie jest nowe narzędzie, tylko poukładanie tego, co już jest.

---

### Rama czasowa

Discovery (wywiady i obserwacja) → synteza i wnioski → raport z rekomendacjami i best practices do wdrożenia.

### Wycena

_(do uzupełnienia)_

---

### Efekt

Spójny, bezpieczny i produktywny setup AI — zaprojektowany pod Wasze zespoły, na podstawie tego, co faktycznie ich spowalnia. Zamiast sytuacji, w której każdy działa na własną rękę i nikt nie wie, gdzie naprawdę leży wąskie gardło.
