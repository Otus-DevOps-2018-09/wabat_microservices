FROM python:3.6.0-alpine

WORKDIR /app
ADD . /app

RUN apk --no-cache add --virtual build-tools gcc musl-dev \
&& pip install -r /app/requirements.txt \
&& apk del build-tools

ENV POST_DATABASE_HOST post_db
ENV POST_DATABASE post

ENTRYPOINT ["python3", "post_app.py"]
