# Analyzing Students' Mental Health (SQL / PostgreSQL)

## Overview
This project explores whether studying in a foreign country affects students’ mental health. Using **PostgreSQL** and SQL queries, we analyze whether **social connectedness (SCS)** and **acculturative stress (ASISS)** predict **depression (PHQ‑9)** among international students, and whether **length of stay** contributes to these outcomes.

> Context: A Japanese international university surveyed its students in 2018. The original study found that international students have a higher risk of mental health difficulties than the general population.

---

## Dataset
- **Source**: Institutional survey (2018)
- **Rows**: 286 | **Columns**: 50
- Key fields:
  - `inter_dom`: Student type (Inter/Dom)
  - `stay`: Length of stay (years)
  - `todep`: Depression score (PHQ‑9)
  - `tosc`: Social connectedness score (SCS)
  - `toas`: Acculturative stress score (ASISS)

---

## Tech Stack
- PostgreSQL (recommended ≥ 14)
- SQL scripts

---

## Setup
```bash
# Create database
CREATE DATABASE mental_health;
\c mental_health;

# Load data
\copy students FROM 'students.csv' WITH (FORMAT csv, HEADER true);
```

---

## Core Queries
```sql
-- Summary by length of stay for international students
SELECT stay,
       COUNT(*) AS count_int,
       ROUND(AVG(todep), 2) AS avg_phq,
       ROUND(AVG(tosc), 2) AS avg_scs,
       ROUND(AVG(toas), 2) AS avg_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

---

## Findings
- International students show varying depression scores by length of stay.
- Higher acculturative stress and lower social connectedness often align with higher depression scores.
- Small sample sizes for long stays require cautious interpretation.

---


## License
MIT License © 2025 Martin Karwacki

---

# Analiza Zdrowia Psychicznego Studentów (SQL / PostgreSQL)

## Przegląd
Projekt bada, czy studiowanie w obcym kraju wpływa na zdrowie psychiczne studentów. Analiza w **PostgreSQL** sprawdza, czy **przynależność społeczna (SCS)** i **stres akulturacyjny (ASISS)** przewidują **depresję (PHQ‑9)** u studentów międzynarodowych oraz czy **długość pobytu** jest czynnikiem.

---

## Dane
- Źródło: Ankieta uczelni (2018)
- Wiersze: 286 | Kolumny: 50
- Kluczowe pola: `inter_dom`, `stay`, `todep`, `tosc`, `toas`

---

## Technologia
- PostgreSQL (zalecane ≥ 14)
- Skrypty SQL

---

## Uruchomienie
```bash
# Utwórz bazę danych
CREATE DATABASE mental_health;
\c mental_health;

# Załaduj dane
\copy students FROM 'students.csv' WITH (FORMAT csv, HEADER true);
```

---

## Zapytania
```sql
SELECT stay,
       COUNT(*) AS liczba,
       ROUND(AVG(todep), 2) AS srednia_phq,
       ROUND(AVG(tosc), 2) AS srednia_scs,
       ROUND(AVG(toas), 2) AS srednia_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

---

## Wnioski
- Wyniki sugerują związek między stresem akulturacyjnym, przynależnością społeczną i depresją.
- Interpretacja ostrożna ze względu na małe próby dla długich pobytów.

---



## Licencja
MIT License © 2025 Martin Karwacki