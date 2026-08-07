# patient-merge-service

patient-merge-service — domain: patients

- **Port:** 8108
- **Language:** Python 3.11 + Flask
- **Database:** `patients` (Postgres, table `patient_merge`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/patient_merge/`          |
| POST      | `/api/patient_merge/`          |
| GET       | `/api/patient_merge/<id>`      |
| PUT/PATCH | `/api/patient_merge/<id>`      |
| DELETE    | `/api/patient_merge/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** patient.merged
**Subscribes:** (none)

## HTTP peer dependencies

- `patients-service`
- `ehr-service`
- `billing-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
