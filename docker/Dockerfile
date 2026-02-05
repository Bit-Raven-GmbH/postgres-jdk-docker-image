FROM postgres:18-trixie

RUN apt-get update && apt-get install -y \
    openjdk-25-jdk \
    maven \
    && rm -rf /var/lib/apt/lists/*

#USER postgres
#
#RUN initdb