FROM python:3.11-slim

WORKDIR /app

# Install app dependencies
COPY Flask/requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the Flask app (models, templates, static, code)
COPY Flask/ /app/

# Hugging Face Spaces expects the app on port 7860
ENV PORT=7860
EXPOSE 7860

CMD ["gunicorn", "--bind", "0.0.0.0:7860", "--workers", "1", "--timeout", "120", "app:app"]
