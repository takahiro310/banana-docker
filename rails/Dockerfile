FROM ruby:2.5.3-alpine

WORKDIR /tmp

RUN apk update && \
    apk add \
      build-base \
      curl-dev \
      libxml2-dev \
      libxslt-dev \
      linux-headers \
      mysql-dev \
      nodejs \
      ruby-dev \
      tzdata \
      yaml \
      yaml-dev \
      git

# ImageMagick6のインストール
RUN apk add --update --no-cache curl && \
    curl -O "http://dl-4.alpinelinux.org/alpine/edge/community/x86_64/imagemagick6-{6.9.9.47-r0,c%2B%2B-6.9.9.47-r0,dev-6.9.9.47-r0,doc-6.9.9.47-r0,libs-6.9.9.47-r0}.apk" && \
    apk add --no-cache \
    imagemagick6-c%2B%2B-6.9.9.47-r0.apk \
    imagemagick6-dev-6.9.9.47-r0.apk \
    imagemagick6-libs-6.9.9.47-r0.apk \
    imagemagick6-6.9.9.47-r0.apk

# bundlerのインストール
RUN gem install bundler

COPY banana-app /apps/banana-app/
WORKDIR /apps/banana-app

COPY ./rails/puma_production.rb ./config/.

# bundle install
RUN rm -rf Gemfile.lock && touch Gemfile.lock
RUN bundle install -j4

EXPOSE 3000
