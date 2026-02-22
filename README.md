# AuthModule Back - Flask JWT API

Authentification réutilisable pour Angular SPA. JWT cookies + CSRF + RateLimit.

## 🚀 Quick Start

```bash
git clone https://github.com/ludo35300/AuthModuleBack.git
cd AuthModuleBack
python -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate sur Windows
pip install -r requirements.txt
flask run
Frontend Angular : http://localhost:4200
API : http://localhost:5000/api/

🔑 Endpoints
Méthode	Endpoint	Auth	Description
POST	/api/auth/login	-	Login (email/password)
POST	/api/auth/register	-	Inscription
POST	/api/auth/refresh	Refresh	Nouveau access token
POST	/api/auth/logout	Access	Déconnexion
GET	/api/me	Access	Profil user
POST	/api/auth/forgot-password	-	Demande reset
POST	/api/auth/reset-password	Token	Reset mot de passe
📦 Dépendances
bash
pip install flask flask-jwt-extended flask-cors flask-limiter werkzeug bcrypt
🔒 Sécurité (Prod)
text
# .env
JWT_SECRET_KEY=sk-64hexchars_here
DATABASE_URL=postgresql://user:pass@localhost/authdb
REDIS_URL=redis://localhost:6379
SECRET_KEY=flask_secret_32bytes
PostgreSQL/SQLite

Redis pour RateLimit/JWT blocklist

HTTPS only (JWT_COOKIE_SECURE=True)

🐳 Docker (futur)
text
# docker-compose.yml
services:
  app:
    build: .
    ports: ["5000:5000"]
  postgres:
    image: postgres:16
  redis:
    image: redis:7
📊 Status
✅ JWT cookies/CSRF
✅ Rate limiting
✅ Password reset
🔄 Tests/DB prod en cours