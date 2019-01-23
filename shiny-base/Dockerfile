FROM r-base:3.5.2
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# Generic shiny app requirements
RUN install2.r -s \
shiny \
shinythemes \
shinyjs

# Minimal tidyverse
RUN install2.r -s \
dplyr \
readr \
tidy

# Misc useful packages
RUN install2.r -s \
config \
logging \
glue