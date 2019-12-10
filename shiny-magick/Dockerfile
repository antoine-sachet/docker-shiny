FROM asachet/shiny-mysql:R3.6.1

# Installing the image magick library + corresponding R package

RUN apt update -qq \
&& apt install -y --no-install-recommends libmagick++-dev
 

RUN install2.r -s --error magick \
&& rm -rf /tmp/downloaded_packages/
