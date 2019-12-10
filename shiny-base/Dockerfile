FROM rocker/r-ver:3.6.1
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# useful for cloud health checks
RUN apt update -qq && apt install -y curl libcurl4-openssl-dev

# Generic shiny app requirements
RUN install2.r -s --error \
shiny \
shinythemes \
shinyjs \
shinyWidgets \
shinydashboard \
&& rm -rf /tmp/downloaded_packages/

# Minimal tidyverse
RUN install2.r -s --error \
dplyr \
forcats \
purrr \
readr \
tidyr \
&& rm -rf /tmp/downloaded_packages/

# Misc useful packages
RUN install2.r -s --error \
# basic yml parser for config
config \
# necessary for dataTableOutput
DT \
# 2 packages to streamline the logging
logging \
glue \
&& rm -rf /tmp/downloaded_packages/

# Plotting packages
RUN install2.r -s --error \
ECharts2Shiny \
ggplot2 \
RColorBrewer \
scales \
viridis \
&& rm -rf /tmp/downloaded_packages/

# My shiny helper library
RUN install2.r -s --error remotes \
&& installGithub.r antoine-sachet/shiny-helpr \
&& rm -rf /tmp/downloaded_packages/

