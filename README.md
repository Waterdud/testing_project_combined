# Täielik testimisprojekt "Kvaliteedijälg"

## Projekti sissejuhatus (20%)
Mitmefaasiline õppeprojekt, mis ühendab avalikud API-d, GA4 sündmused, A/B eksperimendi, CI torustiku ning jõudlustestid ühtseks praktikakeskkonnaks. Tudengid loovad realistliku mini-toote, millel on FastAPI backend, HTML/JS frontend ja täielik testimispinu (pytest, Jest, integratsiooni- ja koormustestid).

## Ajaraam (10 h)
- Kokku 9 ülesannet × ~15 min aktiivset teostamist + kordused, arutelud ja raportid (~8 h).
- Ülejäänud aeg planeerimiseks, tulemuste kogumiseks ja esitlusteks (~2 h).

## Ülesannete rada (60%)
1. **Testiplaan** – Struktureeri nõuded, riskid, tööriistad ja aktsepteerimiskriteeriumid kasutades `docs/testplan-template.md` malli.
2. **Backend + avalikud API-d** – Käivita FastAPI `backend/` kaustas, koosta `/api/koond`, mis pärib JSONPlaceholderi ja Rick & Morty andmed ning normaliseerib need testitavasse skeemi.
3. **Frontend + API sidumine** – Täienda `frontend/index.html`, et kuvada backendist saadud andmeid ja säilitada kasutaja variandi eelistus.
4. **GA4 integreerimine** – Lisa `gtag.js` ja kohandatud sündmused `variant_vaade`/`variant_vahetus`, tõenda tulemused `docs/results/analytics/`.
5. **A/B variandid** – Realiseeri kaks layout'i failis `frontend/ab.js`, loo toggle `app.js` abil ja salvesta olek `localStorage`-is, et testid saaksid seda kontrollida.
6. **Pytest ühikutestid** – Kirjuta vähemalt viis testi `tests-python/` kaustas, mis kontrollivad JSON skeemi, tõrkeid ja ajatempli formaati.
7. **Jest testid** – Rakenda vähemalt neli testi `tests-js/` kaustas, mis valideerivad A/B loogikat ja sündmuse keha.
8. **Integratsioonitestid** – Kasuta `tests-integration/test_koostoime.py`, et jooksutada FastAPI klienti koos `responses`-põhiste mockidega ning logida tulemused.
9. **GitHub Actions CI** – Täienda `.github/workflows/tests.yml`, mis käivitab Python ja JS testid ning salvestab artefaktid.
10. **Locust koormustestid** – Käivita `tests-performance-locust/locustfile.py`, simuleeri 20–50 kasutajat ja arhiveeri koormuslogid `docs/results/locust/`.
11. **Tulemuste dokumenteerimine** – Kogu raportid `docs/results/` struktuuri, lisa viited testiplaani ja lõpp-aruandesse.

> Repo sisaldab ainult näidiskoodi ja skelette. Kõik ülaltoodud sammud täidetakse tudengite poolt ning iga ülesanne kontrollitakse eraldi.

### Käivitamine (kiirstart)
- **Backend**: `cd backend && python -m venv .venv && source .venv/bin/activate && pip install -r requirements.txt && uvicorn backend.main:rakendus --reload`
- **Frontend**: `cd frontend && python -m http.server 4173` ja ava `http://localhost:4173`
- **Pytest**: `source .venv/bin/activate && pytest tests-python tests-integration -v`
- **Jest**: `cd tests-js && npm install && npm test`
- **Locust**: `source .venv/bin/activate && locust -f tests-performance-locust/locustfile.py --headless -u 20 -r 2 --run-time 3m --host http://localhost:8000`

## Lõpptoote nõuded (20%)
- Täidetud testiplaan `docs/testplan.md` koos riskimaatriksi, ajajoone ja tööriistade tabeliga.
- Töökorras backend ja frontend, mille käivitamine on kirjeldatud `backend/README.md` ja `frontend/README.md` failides.
- Pytesti, Jesti, integratsiooni ja Locusti aruanded `docs/results/` alamkataloogides ning GA4 tõendus `analytics/` kaustas.
- Läbitud GitHub Actions töövoog, mille logid on salvestatud `docs/results/ci/` või linkidena README-s.
- Dokumenteeritud A/B katse otsused ja mõõdikud koos soovitustega järgmisteks iteratsioonideks.
