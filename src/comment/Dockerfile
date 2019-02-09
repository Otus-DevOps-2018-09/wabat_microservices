FROM ruby:alpine as bundle

RUN apk add --no-cache ruby-dev build-base

ENV APP_HOME /app
RUN mkdir $APP_HOME

WORKDIR $APP_HOME
ADD Gemfile* $APP_HOME/
ADD . $APP_HOME

RUN bundle install --standalone

FROM ruby:alpine

RUN mkdir -p /app
WORKDIR /app

COPY --from=bundle /usr/local/bundle/ /usr/local/bundle/
COPY --from=bundle /app/ /app/

ENV COMMENT_DATABASE_HOST comment_db
ENV COMMENT_DATABASE comments

CMD ["puma"]
