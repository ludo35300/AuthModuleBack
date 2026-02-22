# 🔐 AuthModule Backend

> API d'authentification robuste et réutilisable construite avec **Flask**.
> Implémente le pattern **JWT (Access + Refresh Tokens)** stockés dans des **Cookies HttpOnly** sécurisés avec protection **CSRF** et **Rate Limiting**.

[![Python](https://img.shields.io/badge/Python-3.13+-blue.svg?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.x-green.svg?style=flat&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![License](https://img.shields.io/badge/license-MIT-purple.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Development-orange.svg)]()

---

## ✨ Fonctionnalités Clés

- **Sécurité Maximale** :
  - **JWT dans Cookies HttpOnly** (pas de LocalStorage, protection XSS).
  - **Protection CSRF** via Double Submit Cookie.
  - **Double Token** : Access Token (court) + Refresh Token (long).
- **Rate Limiting** : Protection contre le Brute-Force via `Flask-Limiter`.
- **Gestion des Utilisateurs** : Inscription, Connexion, Profil (`/me`).
- **Flow Mot de Passe** : Hachage sécurisé (Argon2/Bcrypt) et workflow de réinitialisation (Forgot/Reset Password).
- **Architecture Modulaire** : Utilisation de Flask Blueprints.

## 🚀 Installation & Démarrage

### Prérequis
- Python 3.13+
- Git

### 1. Cloner le projet
```bash
git clone https://github.com/ludo35300/AuthModuleBack.git
cd AuthModuleBack
