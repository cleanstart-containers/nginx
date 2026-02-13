FROM cleanstart/python:latest-dev

WORKDIR /app

# Switch to root to install system dependencies
USER root
RUN apk add --no-cache curl bash

RUN python -m venv /venv

ENV PATH="/venv/bin:$PATH"

# Copy requirements and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY app.py .

# Create non-root user and set permissions
RUN adduser -D -s /bin/bash app && \
    chown -R app:app /app

USER app

EXPOSE 8000

HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:8000/health || exit 1

# Run the app
ENTRYPOINT ["python"]
CMD ["app.py"]
