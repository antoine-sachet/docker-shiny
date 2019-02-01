FROM asachet/shiny-base:latest
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# MySQL client lib
RUN apt update -qq \
&& apt install -y \
libmariadb-dev \
default-libmysqlclient-dev
 
# https://github.com/r-dbi/RMariaDB
RUN install2.r -s --error \
DBI \
RMariaDB
