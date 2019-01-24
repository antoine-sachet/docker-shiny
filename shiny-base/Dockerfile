FROM r-base:3.5.2
LABEL maintainer="Antoine Sachet <antoine.sac@gmail.com>" \
org.label-schema.vcs-url="https://github.com/antoine-sachet/docker-shiny"

# Generic shiny app requirements
RUN install2.r -s --error \
shiny \
shinythemes \
shinyjs

# Minimal tidyverse
RUN install2.r -s --error \
dplyr \
readr \
tidyr

# Misc useful packages
RUN install2.r -s --error \
config \
logging \
glue