- **Projekti nimi:** Kvaliteedijälg – Testimise õppeprojekt  
- **Autorid ja kuupäev:** Tudeng N.N., 2025-03-xx  
- **Versioon:** v1.0

---

## 1. Sissejuhatus
Selle projekti eesmärk on luua mitmeosaline testimiskeskkond, mis ühendab backend’i (FastAPI), frontend’i (HTML/JS), analüütika (GA4), A/B eksperimendid, CI torustiku ning koormustestid. Testiplaan määratleb ulatuse, riskid, meetodid, tööriistad ja raportid, mille alusel hinnatakse süsteemi kvaliteeti.  
Projekt hõlmab nii funktsionaalseid, mittefunktsionaalseid kui ka automatiseeritud teste.

---

## 2. Ulatus

### Kaasatud:
- FastAPI backend  
- Avalikud API-d (JSONPlaceholder, Rick & Morty API)  
- Frontend (A/B variandid, sündmuste logimine)  
- GA4 analüütika sündmused  
- Pytest ühikutestid  
- Jest UI/A/B loogika testid  
- Integratsioonitestid koos mockidega  
- GitHub Actions CI  
- Locust koormustestid  

### Välja jäetud:
- Täielik UI/UX hindamine  
- Turvatestid  
- Pen-testid  
- Deployment tootmiskeskkonda  

---

## 3. Nõuded ja aktsepteerimiskriteeriumid

### Funktsionaalsed nõuded
1. Backend peab tagastama `/api/koond` endpointi kaudu API-de kombineeritud ja normaliseeritud andmed.  
   - **AK:** Vastus sisaldab objekti ID, nime, päritolu ja tüüpi.
2. Frontend peab kuvama API-st saadud andmeid.  
   - **AK:** Andmed kuvatakse DOM-is ilma vigadeta.
3. A/B variandid peavad vahetuma ja olek salvestuma localStorage’is.  
   - **AK:** Variant püsib peale lehe uuesti laadimist.
4. GA4 sündmused `variant_vaade` ja `variant_vahetus` peavad jõudma analytics logisse.  
   - **AK:** GA4 UI näitab sündmuste saabumist.
5. CI peab jooksutama kõik testid automaatselt.  
   - **AK:** GitHub Actions töövoog lõpeb staatusega “success”.

### Mittefunktsionaalsed nõuded
1. Backend peab reageerima < 500ms (ilma kolmanda osapoole API-sid arvestamata).  
2. Locust testil peab 20–50 kasutaja koormus püsima < 5% error rate'iga.

---

## 4. Riskid ja maandus

| Risk | Mõju | Tõenäosus | Maandus |
|------|------|-----------|----------|
| Avalik API on maas | Kõrge | Keskmine | Kasuta mocke integratsioonitestides |
| GA4 sündmused ei jõua kohale | Keskmine | Madal | Testida debugView abil |
| CI pipeline katkeb | Kõrge | Keskmine | Kontrollida workflow skripte ja Node/Python versioone |
| Locust üle koormab backend’i | Keskmine | Madal | Jooksutada lühikese runtime'iga |

---

## 5. Meetodid ja tööriistad

### Testimisraamistikud:
- **Python:** Pytest  
- **JavaScript:** Jest  
- **Integratsioonitestid:** FastAPI TestClient + responses  
- **Koormustestid:** Locust  
- **Analytics:** GA4 DebugView  
- **CI/CD:** GitHub Actions  

### Kontrollitavad komponendid:
- API vastuse struktuur ja veahaldus  
- A/B variandi loogika  
- GA4 sündmused  
- Frontendi DOM-i dünaamika  

---

## 6. Testkeskkonnad ja andmed

### Keskkonnad:
- Python 3.10+  
- Node 18+  
- Virtuaalenv `.venv`  
- Lokaalne http-server (frontend)  
- Locusti CLI keskkond  

### Testandmed:
- Avalikud API päringud  
- Mockitud API vastused integratsioonitestides  
- A/B variandil põhinevad kasutajaolekud (localStorage)  

---

## 7. Ajajoon ja vastutajad (10 h)

| Tegevus | Aeg | Vastutaja |
|---------|------|------------|
| Testiplaan | 1 h | Tudeng |
| Backend + API tests | 2 h | Tudeng |
| Frontend + A/B | 1.5 h | Tudeng |
| GA4 sündmused | 0.5 h | Tudeng |
| Pytest | 1 h | Tudeng |
| Jest testid | 1 h | Tudeng |
| Integratsioonitestid | 1 h | Tudeng |
| CI seadistus | 1 h | Tudeng |
| Locust | 1 h | Tudeng |

---

## 8. Raporteerimine

Kõik raportid arhiveeritakse kataloogi: