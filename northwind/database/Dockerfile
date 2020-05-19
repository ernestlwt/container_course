FROM mysql:5.7

# set root password
ENV MYSQL_ROOT_PASSWORD=mypassword

# add .sql files into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD mysqladmin ping -uroot -pmypassword || exit 1

# where database is saved
VOLUME /var/lib/mysql