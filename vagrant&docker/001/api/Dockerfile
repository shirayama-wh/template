FROM python:3.11.3-slim-bullseye

RUN apt-get update \
    && apt-get install -y python3-dev default-libmysqlclient-dev build-essential \
    && apt-get clean all

RUN adduser user
USER user

WORKDIR /src

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

COPY ./requirements.txt /src/
RUN pip install -r /src/requirements.txt

CMD ["/bin/sh"]
