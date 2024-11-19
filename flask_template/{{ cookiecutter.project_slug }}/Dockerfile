FROM python:3.11.9-slim
WORKDIR /app/{{ cookiecutter.project_slug }}

# Install system dependencies
RUN apt-get update && apt-get install -y vim

# Copy only the requirements file and install Python dependencies, cache it
COPY requirements.txt ./

RUN python -m venv .venv && \
    . .venv/bin/activate && \
    pip install -r requirements.txt

# Copy the rest of the application code
COPY . ./

EXPOSE 80

USER user

# Use Gunicorn to run the application
CMD ["/bin/sh", "-c", ". .venv/bin/activate && cd / && gunicorn --worker-class gevent --bind 0.0.0.0:80 --workers 4 {{ cookiecutter.project_slug }}.app:app"]
