FROM rocker/r-ver:3.5.2
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# Generic shiny app requirements
RUN install2.r -s --error \
shiny \
shinythemes \
shinyjs \
shinyWidgets


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
RUN apt update && apt install -y curl
