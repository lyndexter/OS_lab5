FROM mysql:8.0.24 as build
COPY create_AirBnB.sql /tmp/


ENV MYSQL_DATABASE=AirBnB
ENV MYSQL_USER="user"
ENV MYSQL_PASSWORD="111"
ENV MYSQL_ROOT_PASSWORD=werwerwer

EXPOSE 3306
RUN chown -R mysql:root /var/lib/mysql/
VOLUME [ "/var/lib/mysql" ]

RUN cp /tmp/create_AirBnB.sql /docker-entrypoint-initdb.d


