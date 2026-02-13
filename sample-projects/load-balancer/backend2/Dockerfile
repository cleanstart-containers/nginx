# Base image
FROM cleanstart/python:latest-dev

# Set working directory
WORKDIR /app

USER root

RUN python -m venv /venv

ENV PATH="/venv/bin:$PATH"

# Copy Python requirements first for caching
COPY requirements.txt .

# Install Python dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Copy the rest of the app code
COPY . .

# Expose the port your app will run on
EXPOSE 8002

# Correct CMD pointing to your main script
ENTRYPOINT ["python"]
CMD ["app.py"]

