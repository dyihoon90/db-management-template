FROM mysql:8.0.24

# # Install Unzip
# RUN apt-get update \
#   && apt-get install unzip -y \
#   && apt-get install wget -y

# # Install flyway
# RUN wget -qO- https://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/6.5.5/flyway-commandline-6.5.5-linux-x64.tar.gz | tar xvz \
#   && ln -s `pwd`/flyway-6.5.5/flyway /usr/local/bin

# # Add flyway migration scripts
# COPY flyway/sql /flyway-6.5.5/sql
EXPOSE 3306

# # Configure external build arguments to allow configurability.
ARG DBNAME="template_db"
ARG USER="sa"
ARG PASSWORD="password"


# # Environement variable for MySQL
ENV MYSQL_ROOT_PASSWORD=$PASSWORD
ENV MYSQL_USER=$USER
ENV MYSQL_PASSWORD=$PASSWORD
ENV MYSQL_DATABASE=$DBNAME

# # Environement variable for flyway
# ENV FLYWAY_URL="jdbc:mysql://127.0.0.1:3306/${DBNAME}"
# ENV FLYWAY_USER=$USER
# ENV FLYWAY_PASSWORD=$PASSWORD

RUN useradd -ms /bin/bash  dbuser
USER dbuser

CMD [ "mysqld", "--default-authentication-plugin=mysql_native_password" ]
