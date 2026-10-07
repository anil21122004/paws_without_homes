# Paws Without Homes

A Python/Flask rescue platform for reporting stray and injured animals, adoption requests, volunteer signups, and donations.

## Features

- Public animal listings powered by `animals.json`
- Case reporting for injured or lost animals
- Adoption request workflow
- Volunteer registration and tracking
- Donation handling with Razorpay integration support
- SQLite backend for users and donation records
- Vercel-compatible Flask entrypoint in `api/index.py`

## Prerequisites

- Python 3.10+ installed
- `pip` available
- `requirements.txt` present in the project root

## Install

From the project root:

```bash
py -m pip install -r requirements.txt
```

## Run locally

Recommended local development command:

```bash
py server1.py
```

This starts the Flask app using `api/index.py` and listens on port `10000` by default.

If you prefer a launcher script, you can also run:

```bash
py start.py
```

> Note: `start.py` is a convenience wrapper that launches the local server and opens a browser window.

## Development notes

- `api/index.py` is the primary Flask app and the Vercel serverless entrypoint.
- `server1.py` is the recommended local runner for the Flask app.
- `start.py` is a small wrapper around `server1.py`.
- `server.py` is a legacy standalone server and should not be used for current Flask development.
- `schema.sql` defines the SQLite database schema and must exist for the app to initialize the database.
- `paws_without_homes.db` is created automatically when the app starts.

## Environment variables

Optional secrets and payment configuration:

Windows PowerShell:

```powershell
setx FLASK_SECRET_KEY "your_secret_key"
setx RAZORPAY_KEY_ID "your_test_key_id"
setx RAZORPAY_KEY_SECRET "your_test_key_secret"
```

Bash / macOS / Linux:

```bash
export FLASK_SECRET_KEY="your_secret_key"
export RAZORPAY_KEY_ID="your_test_key_id"
export RAZORPAY_KEY_SECRET="your_test_key_secret"
```

`FLASK_SECRET_KEY` is used for session management.

`RAZORPAY_KEY_ID` and `RAZORPAY_KEY_SECRET` are required only if you want to enable Razorpay payment order creation.

## Deployment

- `vercel.json` routes all requests to `api/index.py` for Vercel deployments.
- `render.yaml` currently references `python server.py` for deployment, but local development should use `server1.py`.

## Useful files

- `animals.json` — sample animal listing data
- `schema.sql` — SQLite database schema
- `requirements.txt` — Python dependencies
- `api/index.py` — main Flask application
- `server1.py` — local Flask launcher
- `start.py` — browser-launching helper
- `vercel.json` — Vercel routing config
- `render.yaml` — Render service config

