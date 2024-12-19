FROM python:3.9-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Update and install required updates
RUN apt-get update && apt-get install -y \
    build-essential \
    gfortran \
    python3-dev \
    git \
    curl && rm -rf /var/lib/apt/lists/*

# Install pip \
RUN pip install --upgrade pip

# Set working directory
WORKDIR /app

# Copy requirements file into the container
COPY requirements.txt /app/requirements.txt

# Install Python dependencies
RUN pip install -r /app/requirements.txt

# Copy jupyter notebook into container
COPY Sagemaker_Tutorial.ipynb /app/

# Expose the port Jupyter runs on
EXPOSE 8888

# Set the command to run Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]

