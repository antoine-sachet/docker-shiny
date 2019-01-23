FROM asachet/shiny-base:latest

# MySQL client lib
RUN apt update -qq \
&& apt install -y libmariadb-client-lgpl-dev 
 
RUN install2.r -s RMySQL
