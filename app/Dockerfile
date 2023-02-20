FROM python:3.9.6-alpine

WORKDIR /usr/src/app

#Environment
ENV PYTHONWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

## Note: Installing uwsgi here, not via PIP to avoid needing a compiler for the container build
#RUN apk add --no-cache \
#        uwsgi-python3 \
#        python3

# Install deps
RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy project
COPY . .
