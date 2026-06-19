# Sytuacja zastana — Toelevering Online

# NOTATKI

## Procesy produktowe i delivery

Planowanie i roadmapa działają według frameworku Scaling Up (BHAG → cele 3-letnie → roczne → kwartalne „rocks"), ale konwersja celów kwartalnych na user stories i sprinty była do niedawna w pełni organiczna — kto głośniej krzyczał, ten dostawał uwagę. Brak priorytetyzacji i brak widoczności zależności między teamami skutkował niespodziewanymi blokerami i otwieraniem sprintów w trakcie.

Struktura teamów to 4 zespoły developerskie + 1 product experience team (UX/UI/CRO) + 1 BS&Data team. Product ownerzy pracowali silosowo, każdy pilnował swojego kawałka. Właśnie wprowadzany jest model, w którym jeden PO prowadzi temat globalnie, a pozostali wspierają.

Product ownerzy są przeciążeni — brak business analityka, brak właściciela biznesowego po stronie biznesu, PO muszą jednocześnie: zbierać wymagania, zarządzać backlogiem, ustalać wizję i alignować się z sales i ops.

Refinement odbywa się tylko na 1 sprint do przodu — bardzo krótki horyzont.

Scrum bez Scrum Masterów — spotkania fasylitowane ad hoc lub rotacyjnie. Dojrzałość Scrumowa różna w zależności od teamu.

## QA — największa luka

Praktycznie brak formalnego QA. Testowanie odbywa się w ramach teamów, głównie happy path. Brak strategii testowej, brak testów integracyjnych (a konfigurator łączy PIM, sklep i logistykę). Istnieje kilka automatycznych e2e testów i unit testy, ale bez spójnej wizji. Efekt: bugi wykrywane dopiero przez klientów po kilku dniach od releasu, przerywanie sprintów na hotfixy. Planowane jest zatrudnienie QA Leada.

## AI — aktualny stan użycia

**Developerzy:**
- Część używa Claude Code (subskrypcja, ograniczenie ~5h usage), część Cursor, część Junie w PHPStorm — brak standaryzacji i governance
- Front-endowcy (React) deklarują, że ~80% kodu generują z AI — zaawansowani, ale bez wytycznych
- Agent OpenAI podpięty do pipeline'ów CI/CD do code review — jeden z nielicznych ustandaryzowanych use case'ów
- Problem: duże PR-y z setkami zmienionych plików, trudne do review przez ludzi

**Product Ownerzy:**
- Loes używa Claude do wzbogacania ticketów — prywatna inicjatywa, nie firmowy standard
- Pozostałe PO używają Claude i ChatGPT, ale bez spójnego podejścia

**Designerzy:**
- Głównie Figma, sporadycznie AI do szkicowania; Claude Code do małych poprawek front-end weryfikowanych przez dewelopera

**Brak:**
- Governance i polityki AI
- Dedykowanej osoby / AI coacha odpowiedzialnego za R&D i wdrożenia
- Szkoleń i onboardingu do narzędzi
- Budżetowego frameworku na tokeny i licencje

## Kierunek strategiczny (kontekst dla AS)

Toelevering Online myśli o AI dwutorowo:

1. **Wewnętrznie** — AI w procesach product & tech (to główny temat tej współpracy z AS)
2. **Produktowo** — AI OS na poziomie firmy, agenty biznesowe, AR w konfiguratorze, automatyczny pomiar okien — ale to wymaga najpierw uporządkowania integracji systemów (event-driven architecture)

Priorytetem na tę chwilę jest obszar nr 1 — podniesienie efektywności działu product & tech poprzez AI.

---

# PREZENTACJA

---

## Slajd 1 — Sytuacja zastana (Pattern 4 · Three-column grid / bg-soft)

**Pill (section label):** Where we are

**Heading:** AI już działa. Brakuje <span indigo>fundamentów</span>.

**Trzy karty:**

- **Karta 1 — Delivery** (card-soft)
  4 zespoły dev + PO przeciążeni bez BA i business ownerów. Refinement tylko 1 sprint do przodu. Scrum bez Scrum Masterów.

- **Karta 2 — QA** (card-ind)
  Największa luka. Brak strategii testowej, brak testów integracyjnych. Bugi wykrywane przez klientów — nie przez zespół.

- **Karta 3 — AI** (card-dark)
  ~80% kodu front-end przez AI. Trzy różne narzędzia, zero governance, brak polityki tokenów i review dla kodu generowanego przez AI.

---

## Slajd 2 — Kierunek strategiczny (Pattern 2 · Single-statement / bg-indigo)

**Pill (section label):** Strategic direction

**Heading:** Nie pytanie <span indigo-glow>czy</span> AI — pytanie jak to <span indigo-glow>poukładać</span>.

**Dwa punkty pod nagłówkiem:**

- **Wewnętrznie** — AI w procesach Product & Tech: governance, narzędzia, QA, PO. To jest priorytet i temat tej współpracy.
- **Produktowo** — AI OS, agenty, AR w konfiguratorze. Wymaga najpierw fundamentu: event-driven architecture i uporządkowane dane.

**Podpis:** Zaczynamy od środka — żeby skalowanie na zewnątrz miało podstawy.
