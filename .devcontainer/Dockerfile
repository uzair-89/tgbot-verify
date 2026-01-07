# .devcontainer/Dockerfile
FROM python:3.11-slim

ENV DEBIAN_FRONTEND=noninteractive

# Install system packages required for Playwright / Chromium and general dev
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential curl git ca-certificates \
    libnss3 libatk1.0-0 libatk-bridge2.0-0 libcups2 libdrm2 libxss1 \
    libasound2 libx11-xcb1 fonts-liberation libgbm1 libgtk-3-0 libxcomposite1 libxrandr2 \
    && rm -rf /var/lib/apt/lists/*

# Ensure pip is up to date
RUN python -m pip install --upgrade pip

WORKDIR /workspace

# We install Python requirements in postCreateCommand so workspace files are present,
# but install playwright Python package now so we can run "playwright install" in postCreateCommand.
RUN pip install playwright
