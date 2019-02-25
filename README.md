# Dockerfiles for portable shiny apps

These images are a stable and convenient base to package shiny apps, typically with a Dockerfile looking like:

```Dockerfile
FROM asachet/shiny-base:R3.5.2-stable-v1.1

# Add packages specific to this app
RUN install2.r -s --error \
radarchart \
googlesheets

WORKDIR /usr/local/src/mycoolapp

COPY data/ data/
COPY www/ www/
COPY *.R ./
COPY *.yml ./

EXPOSE 3838

CMD ["r", "-e", "shiny::runApp('.', port=3838, host='0.0.0.0', launch.browser=F)"]
```

## shiny-base

* Built on the most stable R image, `rocker/r-ver`
* Contains `shiny` and common packages like `shinydashboard`, `shinyWidgets`, `shinythemes`, `DT` for `dataTableOutput`, etc
* Contains a minimal `tidyverse` and `ggplot`-verse 
* Contains convenience (and IMO best practice) tools like `logging` and `config`

## shiny-mysql

* Built on `shiny-base` for robustness
* Adds system libraries and R packages necessary to connect to `MySQL` databases
* NOTE: relies on `RMariaDB` instead of the _legacy_ `RMySQL` package!

## shiny-dev

* Built on `rocker-rstudio` rather than `rocker:r-ver`, but using the same version.
* **Not meant for deployment** but useful for development in the same controlled environment using `rstudio` in the browser.

## shinyproxy-base

* Containerised shinyproxy, suitable to set up a shinyproxy server. Simply add your yml config. See www.shinyproxy.io
* Dockerfile adapted from openalanalytics's [shinyproxy-config-examples](https://github.com/openanalytics/shinyproxy-config-examples/tree/master/02-containerized-docker-engine)
* Not a suitable base for shiny apps as it does not contain shiny.

## LICENSE

These Dockerfiles are under the MIT license. RStudio and Shiny are trademarks of RStudio, Inc.
