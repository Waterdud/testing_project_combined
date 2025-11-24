# Backend – FastAPI koondteenus

## Eeldused
- Python 3.11+
- Virtuaalkeskkond (soovituslik)

## Kiirstart
```bash
cd /Users/robinrattasep/testing_project/backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn backend.main:rakendus --reload
```

Endpointid:
- `GET /status` – tervisekontroll.
- `GET /api/koond` – kombineeritud JSONPlaceholder + Rick & Morty vastus.

## Kvaliteedivihjed
- Muuda URL-e keskkonnamuutujatega, kui testid nõuavad.
- Logi kõik vead näitamaks riskide maandamist.
