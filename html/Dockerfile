FROM nginx

RUN apt-get update -y
RUN apt-get install vim -y

WORKDIR /app

COPY ./html /app/src/

WORKDIR /app/src


#RUN cp index.html /usr/share/nginx/html
#COPY /web/default.conf /etc/nginx/conf.d/default.conf

RUN mkdir /etc/nginx/templates
COPY ./frontend/default.conf.template /etc/nginx/templates

COPY ./frontend/default.conf.template /default.conf.template

EXPOSE 5000


CMD ["/bin/sh" , "-c" , "envsubst < /default.conf.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"]
