FROM r-base:3.5.2

# Generic shiny app requirements
RUN install2.r -s \
shiny \
shinythemes

# Minimal tidyverse
RUN install2.r -s \
dplyr \
readr \
tidy

# Misc useful packages
RUN install2.r -s \
config