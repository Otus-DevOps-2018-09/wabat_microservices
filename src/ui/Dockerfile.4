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

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292

CMD ["puma"]
