FROM postgres:13

# Original postgresql init script expects empty $PGDATA so we initially place
# certificates into the image to the intermediate directory
COPY ssl/postgresql/postgresql.crt /tmp.ssl/server.crt
COPY ssl/postgresql/postgresql.key /tmp.ssl/server.key
COPY ssl/ca/root.crt /tmp.ssl/root.crt
RUN chown -R postgres:postgres /tmp.ssl

COPY _scripts/postgresql-ssl-configure.sh /docker-entrypoint-initdb.d/
