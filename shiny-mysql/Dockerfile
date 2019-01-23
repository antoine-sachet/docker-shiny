FROM asachet/shiny-base:latest

# MySQL client lib
RUN apt update -qq \
&& apt install -y \
libmariadb-client-lgpl-dev \
libmysqlclient-dev
 

# https://github.com/r-dbi/RMariaDB
RUN install2.r -s \
DBI \
RMariaDB
