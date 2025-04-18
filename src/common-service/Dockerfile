# 
# Copyright (C) 2025 Intel Corporation. 
# 
# SPDX-License-Identifier: Apache-2.0 
#

# Use an official Python runtime as a parent image
FROM python:3.10-slim@sha256:f680fc3f447366d9be2ae53dc7a6447fe9b33311af209225783932704f0cb4e7

# Set environment variables to prevent Python from writing pyc files and buffering stdout/stderr
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Install system dependencies
RUN apt-get update && apt-get install -y gcc

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt /app/

# Install Python dependencies
RUN pip install --require-hashes --no-deps --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . /app/

# run both apps in parallel
CMD ["/bin/bash", "-c", "python lidar_app.py & python weight_app.py & python barcode_app.py & wait"]
