FROM mysql:8.0.33

COPY ./config/my.cnf /etc/mysql/conf.d/my.cnf
RUN chmod 644 /etc/mysql/conf.d/my.cnf

CMD ["mysqld"]
