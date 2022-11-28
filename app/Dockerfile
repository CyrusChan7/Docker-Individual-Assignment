FROM python:3

RUN useradd -m -d /app backend
RUN apt-get update -y
RUN pip3 install flask


USER backend
WORKDIR /app


COPY ./app /app/src

#RUN python3 -m pip install -r /app/src/requirements.txt

WORKDIR /app/src

COPY ./backend/backend_create.sh /app/src
USER root
RUN chmod +x ./backend_create.sh


USER root

RUN chown -R backend /app

USER backend
EXPOSE 5000

ENTRYPOINT [ "/bin/bash", "/app/src/backend_create.sh" ]
#CMD wait-for-it -h ${MYSQL_HOST} -p ${MYSQL_PORT} -t 60 -s -- gunicorn -b 0.0.0.0:8000 wsgi:app