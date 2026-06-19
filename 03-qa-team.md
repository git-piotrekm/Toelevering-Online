# Zespół QA — budowanie kompetencji i procesu

# NOTATKI

## Punkt wyjścia

QA praktycznie nie istnieje jako funkcja. Testują developerzy w obrębie swojego zespołu, czasem biznes, czasem Loes osobiście przy zmianach wysokiego ryzyka. Są jakieś e2e podpięte do CI/CD i trochę testów jednostkowych, ale — słowami Ivo — bez strategii ani wizji z poziomu nadrzędnego. Testuje się happy path, nie corner case'y, integracji prawie wcale. Efekt: bugi wychodzą na produkcję po kilku dniach, rozbija się sprint, gasi pożar. Konfigurator jest podpięty do shopu, logistyki i PIM-u — jak jedna rzecz pęknie, klient nie złoży zamówienia.

**Sedno łączące z punktem 1:** AI przyspiesza pisanie kodu, więc bez dojrzałego QA zespół wpada w nowy bottleneck — więcej kodu, więcej bugów. Im skuteczniejszy AI Scan, tym pilniejszy QA. Przy wzroście 55M → 60-65M i ekspansji na Niemcy/Francję takich sytuacji nie wolno już mieć.

## Co robimy

Nie zewnętrzny audyt — transfer kompetencji, równolegle do konsultacji AI:

1. **Pomoc w obsadzeniu QA Leada** (Ivo sam w to celuje) — profil, ocena kandydatów lub wskazanie osoby wewnętrznej.
2. **Strategia testowania end-to-end** — spójna piramida (unit, integracyjne, e2e), nacisk na integrację konfigurator ↔ shop ↔ logistyka ↔ commerce tools.
3. **Pierwsze automatyzacje, w tym AI** — gdzie AI realnie pomaga (przypadki testowe, regresja, smoke), a gdzie to hype.
4. **Osadzenie w istniejącym CI/CD na Azure** — we współpracy z partnerem infra i Waszym chapterem DevOps.

## Deliverables

- Profil QA Leada + wsparcie w rekrutacji/wyznaczeniu.
- Strategia i wizja testowania (dokument + piramida + podział odpowiedzialności).
- Pierwsze działające testy integracyjne i e2e dla krytycznej ścieżki (konfigurator → zamówienie).
- Integracja testów w CI/CD na Azure.
- Playbook codziennego testowania + gdzie wchodzi AI.

**Rama czasowa:** Faza startowa ~4–6 tygodni (strategia + QA Lead + pierwsze automatyzacje), potem tryb coachingowy na kwartał.

**Wycena:** [do uzupełnienia] — punkt o największej zmienności zakresu.

**Efekt:** Zespół, który potrafi skalować jakość razem z prędkością dostarczania.

## Argumenty pod osoby

- **Ivo** — jego oczko w głowie; brakująca podstawa, bez której wzrost przychodu zamieni się we wzrost pożarów.
- **Loes** — QA jako proces zdejmuje z niej testowanie zmian wysokiego ryzyka.

---

# PREZENTACJA
