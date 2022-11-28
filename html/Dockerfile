FROM nginx

RUN apt-get update -y

WORKDIR /app

COPY ./html /app/src/

WORKDIR /app/src


RUN mkdir /etc/nginx/templates
COPY ./frontend/default.conf.template /etc/nginx/templates

COPY ./frontend/default.conf.template /default.conf.template


CMD ["/bin/sh" , "-c" , "envsubst < /default.conf.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"]
