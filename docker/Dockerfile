FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    TZ=Europe/Istanbul

WORKDIR /app

COPY requirements.txt .
RUN apt-get update \
    && apt-get install -y --no-install-recommends build-essential libffi-dev tzdata \
    && python -m pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt \
    && apt-get purge -y build-essential \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

COPY *.py ./
COPY helpers ./helpers

RUN useradd --create-home --uid 10001 botsystem \
    && mkdir -p /config \
    && chown -R botsystem:botsystem /app /config

USER botsystem
VOLUME ["/config"]

CMD ["python", "-u", "galaxyscore.py", "-d", "/config"]
