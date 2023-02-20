# TAMMY2

## Pre-build App (during Dev)
(From within tammy/app) Make sure that the app's installed requirements are frozen
```
source .venv/bin/activate
pip freeze > requirements.txt
deactivate
```

## Build with Docker Compose
(From within tammy)
docker compose build


