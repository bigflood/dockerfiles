FROM ubuntu:18.04

RUN apt update && apt install -y wget unzip

RUN wget https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-linux.zip && \
    unzip sonar-scanner-cli-3.2.0.1227-linux.zip && \
    rm sonar-scanner-cli-3.2.0.1227-linux.zip

WORKDIR /src

# https://docs.sonarqube.org/display/SONAR/Analysis+Parameters

CMD /sonar-scanner-3.2.0.1227-linux/bin/sonar-scanner \
    -D "sonar.host.url=$SQ_HOST" \
    -D "sonar.login=$SQ_LOGIN" \
    -D "sonar.sourceEncoding=UTF-8" 
