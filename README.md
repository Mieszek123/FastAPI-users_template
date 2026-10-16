# FastAPI Users Template

A minimal FastAPI backend with authentication built on **fastapi-users** (JWT), plus **pytest** tests for the register and login endpoints. Use it as a starting point for new projects.

## Stack

- FastAPI
- fastapi-users (JWT / Bearer)
- SQLite (swap for any other DB)
- pytest + pytest-asyncio
- uv for dependency management

## Getting started

```bash
# create a new repo with "Use this template" on GitHub, then:
git clone https://github.com/YOUR_USERNAME/NEW_PROJECT.git
cd NEW_PROJECT

uv sync
cp .env.example .env     # set SECRET_KEY and DATABASE_URL
uv run python main.py
```

Docs: http://localhost:8000/docs

## Endpoints

| Method | Path              | Description                          |
|--------|-------------------|--------------------------------------|
| POST   | `/auth/register`  | Register a user (JSON: email, password) |
| POST   | `/auth/jwt/login` | Log in (form data: `username` = email, `password`), returns `access_token` |

## Tests

```bash
uv run pytest
```

Tests use a separate database (`test.db`), so your dev data stays untouched.

Covered:

- register: success (`201`), duplicate email (`400`)
- login: success (`200`), token returned, wrong password (`400`), unknown email (`400`)

## Project structure

```
.
├── app/
│   ├── app.py        # FastAPI app and routers
│   ├── db.py         # database engine and sessions
│   ├── schemas.py    # user schemas
│   └── users.py      # fastapi-users setup, JWT backend
├── test/
│   ├── conftest.py   # test client and test database
│   └── test_app.py   # register and login tests
├── main.py           # entry point
├── pyproject.toml
└── uv.lock
```

## After creating a project from this template

- [ ] Rename the project in `pyproject.toml` and this README
- [ ] Set your own `SECRET_KEY` and change `.env.example` to `env`
- [ ] Point `DATABASE_URL` to your target database
- [ ] Run `uv run pytest` to check everything works
