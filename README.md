# HM_DATA

Automated NSE data fetcher (yfinance) and GitHub Actions workflow

This repository stores:
- scripts/fetch_and_commit.py — yfinance-only data fetcher (chunked downloads, in-memory processing, repo copy support).
- .github/workflows/fetch-data.yml — GitHub Actions workflow to run every weekday at 23:45 IST and support manual runs.
- .gitattributes — recommended Git LFS settings for binary files (zip).
- .gitignore — ignore local env files and caches.
- sync_to_repo.sh — helper to commit and push files (if used locally).

Usage:
1. Provide the index CSV URL from https://www.niftyindices.com (e.g. Nifty 50 CSV) when running the workflow.
2. The workflow will fetch symbols from the provided CSV and fetch data via yfinance (processing in-memory), create ZIPs under `data/<timeframe>/<SYMBOL>.zip` and commit them into the repo.

Run today (manual dispatch):
- Go to Actions → Fetch NSE Data → Run workflow, provide the index CSV URL (e.g. https://www.niftyindices.com/IndexConstituent/ind_nifty50list.csv) and run.

Notes:
- ZIPs are marked for Git LFS via .gitattributes. Enable Git LFS locally to push large ZIPs.