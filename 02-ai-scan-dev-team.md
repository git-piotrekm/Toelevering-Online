# AI Scan — Zespół developerski

# NOTATKI

## Punkt wyjścia

AI w developmencie już u Was działa — ale w pełni oddolnie. Zespół Emila jeździ na Claude Code, część osób na Cursorze, część na Junie w PHPStorm/IntelliJ. Front-endowcy generują ~80% kodu przez AI. Na pipelinie działa agent OpenAI do review. Ludzie chcą — to dobra wiadomość. Zła: zero governance. Każdy robi po swojemu, nie ma polityki narzędziowej ani kontroli kosztów tokenów (ludzie czasem wpadają w limity 5h/tygodniowe Claude Code), a code review zaczyna boleć — wielkie PR-y, dużo zmienionych plików, narastające tarcia w zespole. To dokładnie ten moment, w którym sami byliśmy przy 120 developerach — żadne dwie osoby nie pracowały na tym samym zestawie narzędzi.

## Co robimy

Dwutygodniowy audyt + zaprojektowanie wdrożenia dla całego działu Product & Tech:

1. **Mapujemy obecny stan** — sesje 1:1 i obserwacje w każdym zespole; kto czego używa, co przyspiesza, co generuje chaos.
2. **Audyt kosztów i limitów tokenów** — nikt nie jest blokowany, ale tokeny nie palą się bez kontroli.
3. **Standaryzacja stacku narzędziowego** — jeden (maks. dwa) wspierane zestawy pod PHP Laravel / React / .NET.
4. **Governance dla kodu z AI** — zasady review specyficznie dla kodu generowanego przez AI, ograniczanie rozmiaru PR-ów, sensowniejsze wykorzystanie agenta na pipelinie.
5. **AI Champion** — wyznaczenie i przygotowanie wewnętrznej osoby prowadzącej temat dalej.

## Deliverables

- Raport stanu obecnego z liczbami.
- Rekomendacja standaryzacji narzędzi + uzasadnienie kosztowe.
- Polityka governance: tokeny, review kodu AI, bezpieczeństwo.
- Plan wdrożenia krok po kroku.
- Profil i onboarding AI Championa.

**Rama czasowa:** 2 tygodnie (tydzień 1 — discovery, tydzień 2 — synteza + warsztat domykający).

**Wycena:** [do uzupełnienia]

**Efekt:** Spójny, bezpieczny i produktywny setup AI — zamiast sytuacji, w której każdy developer działa na własną rękę.

## Argumenty pod osoby

- **Ivo** — sam zgłosił brak governance i prośbę o pomoc w postawieniu defaultów; chcesz skalować output bez skalowania headcount, a bez governance chaos rośnie szybciej niż produktywność.
- **Emil** — pozycjonujemy jego zespół jako wzorzec, nie narzucamy ograniczeń; standaryzacja = mniej czasu na cudze mega-PR-y.
- **Loes** — governance dla PR-ów AI bezpośrednio odciąża ją z ogromnych review.

---

# PREZENTACJA
