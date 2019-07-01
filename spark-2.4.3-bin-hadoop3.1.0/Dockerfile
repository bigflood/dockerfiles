FROM ubuntu:18.04

RUN \
    apt-get -y update && \
    apt-get install -y locales && \
    locale-gen $LANG && \
    apt-get install -y software-properties-common && \
    apt -y autoclean && \
    apt -y dist-upgrade && \
    apt-get install -y build-essential wget curl grep sed dpkg 

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

RUN apt-get -y update && \
    apt-get install -y openjdk-8-jdk maven && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://archive.apache.org/dist/spark/spark-2.4.3/spark-2.4.3.tgz \
    && tar -zxvf spark-2.4.3.tgz \
    && mv spark-2.4.3 spark \
    && rm spark-2.4.3.tgz \
    && cd /

ENV TERM=xterm-color

RUN cd /spark \
    && ./dev/make-distribution.sh --name hadoop3.1.0 --tgz -Phadoop-3.1 -Pmesos -DskipTests

FROM scratch

COPY --from=0 /spark/spark-2.4.3-bin-hadoop3.1.0.tgz /

