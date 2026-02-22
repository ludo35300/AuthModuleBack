# AuthModule Back

**Authentification réutilisable** pour Angular SPA. JWT cookies sécurisés + CSRF + Rate Limiting.

[![Python 3.13](https://img.shields.io/badge/python-3.13-green.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/flask-3.x-blue.svg)](https://flask.palletsprojects.com/)
[![License MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

## 🚀 Quick Start

```bash
git clone https://github.com/ludo35300/AuthModuleBack.git
cd AuthModuleBack
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
flask run

Frontend : http://localhost:4200
API : http://localhost:5000/api/

🔑 Endpoints API

| Méthode | Endpoint                  | Auth    | Description                 |
| ------- | ------------------------- | ------- | --------------------------- |
| POST    | /api/auth/login           | -       | Login (email/password)      |
| POST    | /api/auth/register        | -       | Inscription utilisateur     |
| POST    | /api/auth/refresh         | Refresh | Nouveau access token        |
| POST    | /api/auth/logout          | Access  | Déconnexion (unset cookies) |
| GET     | /api/me                   | Access  | Profil utilisateur          |
| POST    | /api/auth/forgot-password | -       | Demande reset password      |
| POST    | /api/auth/reset-password  | Token   | Reset mot de passe          |

Exemple login :

```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'

📦 Installation

```bash
pip install flask flask-jwt-extended flask-cors flask-limiter werkzeug bcrypt python-dotenv

🔒 Configuration Production
Créez .env :

```text
JWT_SECRET_KEY=sk-64_hex_chars_here_$(python -c "import secrets; print(secrets.token_hex(32))")
SECRET_KEY=flask_app_secret_32_bytes_here
DATABASE_URL=postgresql://user:pass@localhost/authdb
REDIS_URL=redis://localhost:6379
CORS_ORIGINS=https://monapp.com,https://www.monapp.com

Sécurité activée :

JWT_COOKIE_SECURE=True (HTTPS only)

Redis RateLimit/JWT blocklist

PostgreSQL persistant

🐳 Docker (à implémenter)

```text
# docker-compose.yml
services:
  app:
    build: .
    ports: ["5000:5000"]
    env_file: .env
    depends_on: [postgres, redis]
  postgres:
    image: postgres:16
    environment:
      POSTGRES_DB: authdb
      POSTGRES_USER: auth
      POSTGRES_PASSWORD: secret
  redis:
    image: redis:7-alpine

📊 Status Développement

| Feature             | Statut             |
| ------------------- | ------------------ |
| JWT Cookies + CSRF  | ✅                  |
| Rate Limiting       | ✅ (memory → Redis) |
| Password Reset      | ✅                  |
| User Register/Login | ✅                  |
| Refresh Tokens      | ✅                  |
| PostgreSQL          | 🔄 WIP             |
| Tests pytest        | 🔄 WIP             |
| Docker              | 🔄 WIP             |

🤝 Contributing

```bash
# Dev setup
pip install -r requirements.txt -r requirements-dev.txt
pytest
pre-commit install  # linting auto