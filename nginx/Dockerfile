# ...put your own build instructions here...
FROM nginx:1.15
RUN apt-get update && \
    apt-get install -y apt-utils \
                       locales && \
    echo "ja_JP.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen ja_JP.UTF-8
ENV LC_ALL ja_JP.UTF-8
ADD ./nginx/nginx.conf  /etc/nginx/nginx.conf
ADD ./nginx/rails.conf /etc/nginx/conf.d/default.conf
