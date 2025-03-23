#сборка
FROM python:3.9-alpine AS builder

WORKDIR /app

RUN python -m venv /app/venv
ENV PATH="/app/venv/bin:$PATH"

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

#запуск
FROM python:3.9-alpine

WORKDIR /app

COPY --from=builder /app /app

RUN adduser -D myuser
USER myuser

ENV PATH="/app/venv/bin:$PATH"

EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0"]
