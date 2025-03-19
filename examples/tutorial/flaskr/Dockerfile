FROM python:3.9-alpine AS builder

WORKDIR /app

COPY requirements.txt .
RUN pip install --prefix=/app/.local --no-cache-dir -r requirements.txt


COPY . .

FROM python:3.9-alpine

WORKDIR /app

#COPY --from=builder /app/.local /app/.local
COPY --from=builder /app/. /app/.
#COPY --from=builder /app /app

# ENV PATH=/app/.local/bin:$PATH

RUN adduser -D myuser
USER myuser

EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0"]
