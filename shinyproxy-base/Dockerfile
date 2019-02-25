FROM openjdk:8-jre

RUN mkdir -p /opt/shinyproxy/
RUN wget --no-verbose https://www.shinyproxy.io/downloads/shinyproxy-2.1.0.jar -O /opt/shinyproxy/shinyproxy.jar

WORKDIR /opt/shinyproxy/
CMD ["java", "-jar", "/opt/shinyproxy/shinyproxy.jar"]

