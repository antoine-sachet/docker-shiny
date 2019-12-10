# Dockerfiles for portable shiny apps

These images are a stable and convenient base to package shiny apps, typically with a Dockerfile looking like:

```Dockerfile
FROM asachet/shiny-base:3.6.1

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

[![](https://images.microbadger.com/badges/version/asachet/shiny-base.svg)](https://microbadger.com/images/asachet/shiny-base "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/asachet/shiny-base.svg)](https://microbadger.com/images/asachet/shiny-base "Get your own image badge on microbadger.com")

* Built on the most stable R image, `rocker/r-ver`
* Contains `shiny` and common packages like `shinydashboard`, `shinyWidgets`, `shinythemes`, `DT` for `dataTableOutput`, etc
* Contains a minimal `tidyverse` and `ggplot`-verse 
* Contains convenience (and IMO best practice) tools like `logging` and `config`

## shiny-mysql

[![](https://images.microbadger.com/badges/version/asachet/shiny-mysql.svg)](https://microbadger.com/images/asachet/shiny-mysql "Get your own version badge on microbadger.com")  [![](https://images.microbadger.com/badges/image/asachet/shiny-mysql.svg)](https://microbadger.com/images/asachet/shiny-mysql "Get your own image badge on microbadger.com")

* Built on `shiny-base` for robustness
* Adds system libraries and R packages necessary to connect to `MySQL` databases
* NOTE: relies on `RMariaDB` instead of the _legacy_ `RMySQL` package!

## shiny-dev

[![](https://images.microbadger.com/badges/version/asachet/shiny-dev.svg)](https://microbadger.com/images/asachet/shiny-dev "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/asachet/shiny-dev.svg)](https://microbadger.com/images/asachet/shiny-dev "Get your own image badge on microbadger.com")

* Built on `rocker-rstudio` rather than `rocker:r-ver`, but using the same version.
* Contains shiny-base + shiny-mysql + rstudio + devtools + roxygen2
* **Not meant for deployment** but useful for development in the same controlled environment using `rstudio` in the browser.

## shinyproxy-base

No longer living in this repository as R version tags did not make sense for this image.

* Containerised shinyproxy, suitable to set up a shinyproxy server. Simply add your yml config. See www.shinyproxy.io
* Dockerfile adapted from openalanalytics's [shinyproxy-config-examples](https://github.com/openanalytics/shinyproxy-config-examples/tree/master/02-containerized-docker-engine)
* Not a suitable base for shiny apps as it does not contain shiny.

## LICENSE

These Dockerfiles are under the MIT license. RStudio and Shiny are trademarks of RStudio, Inc.
