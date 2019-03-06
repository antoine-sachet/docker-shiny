FROM asachet/shiny-base:R3.5.2-stable-v1.3
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# MySQL client lib
RUN apt update -qq \
&& apt install -y \
libmariadb-dev \
libmariadbclient-dev
 
# https://github.com/r-dbi/RMariaDB
RUN install2.r -s --error \
DBI \
RMariaDB
