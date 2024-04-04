# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Set Poetry environment variables
ENV PATH "$PATH:/root/.poetry/bin"
ENV POETRY_HOME "/root/.poetry"

# Set Poetry environment variables
ENV PATH "$PATH:/home/github/.poetry/bin"
ENV POETRY_HOME "/home/github/.poetry"

# Copy the project code into the container
WORKDIR /home/github
COPY . .

# Install project dependencies
RUN poetry config virtualenvs.in-project true

# Run CI/CD commands here
CMD ["poetry", "run", "your_ci_cd_command"]
