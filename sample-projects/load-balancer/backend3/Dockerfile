# Dockerfile for Flask Backend API 3
FROM cleanstart/python:latest-dev

# Set working directory
WORKDIR /app

USER root

RUN python -m venv /venv

ENV PATH="/venv/bin:$PATH"

# Copy requirements first for better caching
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY app.py .

# Expose port
EXPOSE 8003

# Run the application
ENTRYPOINT ["python"]
CMD ["app.py"]
