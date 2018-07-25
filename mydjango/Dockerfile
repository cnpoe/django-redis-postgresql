FROM python:3.6.5-alpine

RUN mkdir -p /data/web
RUN cd /data/web
WORKDIR /data/web
COPY requirements.txt /data/web/

RUN apk update
RUN apk upgrade
RUN apk add --update postgresql-client postgresql-dev build-base gettext
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

RUN apk del -r python3-dev postgresql

COPY . /data/web/

RUN mkdir mydjango/static
RUN mkdir mydjango/media

RUN python3 manage.py collectstatic

EXPOSE 8000
