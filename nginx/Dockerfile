# ...put your own build instructions here...
FROM nginx:1.15
RUN apt-get update && \
    apt-get install -y apt-utils \
                       locales && \
    echo "ja_JP.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen ja_JP.UTF-8
ENV LC_ALL ja_JP.UTF-8

RUN apt-get update \
    && apt-get install --yes --no-install-recommends \
      openssl \
      certbot \
    && rm -rf /var/lib/apt/lists/*

COPY ./nginx/nginx.conf  /etc/nginx/nginx.conf
COPY ./nginx/banana.conf /etc/nginx/conf.d/banana.conf

COPY ./nginx/start.sh    /start.sh
RUN chmod +x /start.sh
CMD /start.sh
