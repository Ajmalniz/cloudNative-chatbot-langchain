# Use the official Python image.
FROM python:3.12

# Set the maintainer label.
LABEL maintainer="Ajmal Khan"
# Install system dependencies required for potential Python packages
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*
# Set the working directory in the container.
WORKDIR /code

# Install Poetry.
RUN pip install poetry

# Copy the project files into the container.
COPY . /code/

# Configure Poetry to not use virtual environments.
RUN poetry config virtualenvs.create false

# Install the dependencies specified in pyproject.toml.
RUN poetry install

# Expose the port Streamlit will run on.
EXPOSE 8501

# Command to run the Streamlit app.
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
