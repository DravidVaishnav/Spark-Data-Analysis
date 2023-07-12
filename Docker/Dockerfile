ARG java_image_tag=11-jre-slim

FROM openjdk:${java_image_tag}

USER 0

RUN mkdir -p /opt 
RUN apt-get update -y 
RUN apt-get install -y python3
RUN ln -s /usr/bin/python3 /usr/bin/python 
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get update -y 
RUN apt-get install -y curl 
RUN curl https://dlcdn.apache.org/spark/spark-3.3.0/spark-3.3.0-bin-hadoop3.tgz -o spark.tgz 
RUN tar xvf spark.tgz 
RUN mv spark-3.3.0-bin-hadoop3 /opt/spark

ENV SPARK_HOME /opt/spark
ENV PATH ${PATH}:${SPARK_HOME}/bin:${SPARK_HOME}/sbin
ENV PYSPARK_PYTHON /usr/bin/python3

RUN apt-get -y install python3-pip 
RUN pip3 install pyspark

WORKDIR /opt

COPY pi.py /opt/

