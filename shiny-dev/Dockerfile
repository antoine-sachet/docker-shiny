FROM rocker/rstudio:3.5.2
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

## Dev tools
# System requirements
RUN apt update -qq && apt install -y \
libxml2-dev \
libgit2-dev \
zlib1g-dev \
libcurl4-openssl-dev

RUN install2.r -s --error devtools roxygen2 testthat remotes

## CONTENT OF shiny-base/Dockerfile

# Generic shiny app requirements
RUN install2.r -s --error \
shiny \
shinythemes \
shinyjs \
shinyWidgets \
shinydashboard

# Minimal tidyverse
RUN install2.r -s --error \
dplyr \
forcats \
purrr \
readr \
tidyr

# Misc useful packages
RUN install2.r -s --error \
# basic yml parser for config
config \
# necessary for dataTableOutput
DT \
# 2 packages to streamline the logging
logging \
glue

# Plotting packages
RUN install2.r -s --error \
ECharts2Shiny \
ggplot2 \
RColorBrewer \
scales \
viridis

# useful for cloud health checks
RUN apt install -y curl libcurl4-openssl-dev

## CONTENT OF shiny-mysql/Dockerfile

# MySQL client lib
RUN apt update -qq \
&& apt install -y \
libmariadb-dev \
default-libmysqlclient-dev
 
# https://github.com/r-dbi/RMariaDB
RUN install2.r -s --error \
DBI \
RMariaDB

# My shiny helpr package
RUN install2.r -s --error remotes \
&& installGithub.r antoine-sachet/shiny-helpr

# shinytest

RUN install2.r -s --error shinytest &&
  r -e 'shinytest::installDependencies()'
