#FROM tiangolo/uvicorn-gunicorn-fastapi:python3.8
FROM python:3.8-slim

# set environment variables
ENV PYTHONWRITEBYTECODE 1
ENV PYTHONBUFFERED 1

# set working directory
WORKDIR /app

# copy dependencies
COPY requirements.txt /app/

# install dependencies
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# copy project
COPY . /app/

# Run
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "80"]
