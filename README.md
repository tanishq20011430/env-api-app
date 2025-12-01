# env-api-app

A minimal example Flask application demonstrating how to configure an app with environment variables and run it in Docker.

Summary

- Purpose: Tiny sample app that reads APP_NAME and APP_PORT from the environment and serves a single endpoint (/) that returns a welcome message using APP_NAME.
- Intended use: learning/demo/starter template for environment-driven configuration and Docker packaging.

Repository structure

- app.py: Minimal Flask app that reads APP_NAME (default: "Default App") and APP_PORT (default: 5000).
- .env: Example environment file (APP_NAME and APP_PORT). Do not commit secrets here for real projects.
- requirements.txt: Declares dependencies (flask, python-dotenv). Versions are not pinned.
- Dockerfile: Builds a Python 3.10-slim image and runs app.py.
- docker-compose.yml: Builds and runs the service, loading variables from .env and mapping the configured port.

How to run (development)

1. With Docker Compose (recommended for this repo):
   - Ensure .env has APP_PORT set (default in repo: 8080).
   - docker-compose up --build
   - Visit http://localhost:8080/ (or the value of APP_PORT).

2. Without Docker:
   - pip install -r requirements.txt
   - export APP_NAME="My App"; export APP_PORT=5000
   - python app.py
   - Visit http://localhost:5000/

Notes and recommended improvements

- Development-focused: uses Flask's built-in server. For production, run behind a WSGI server (e.g., gunicorn).
- Pin dependency versions in requirements.txt for reproducibility.
- Either use python-dotenv in app.py (load_dotenv()) for local .env support, or remove it from requirements.
- Add .dockerignore, healthchecks, logging, tests, and CI for real projects.
- Do not commit sensitive values to .env in public repos.
