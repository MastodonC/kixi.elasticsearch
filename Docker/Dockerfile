FROM ubuntu:14.04
MAINTAINER Max Droog Hayes

#
# ElasticSearch Dockerfile
#
############################################
# Install oracle jdk
RUN apt-get -y update

RUN apt-get -y install software-properties-common python-software-properties	

RUN add-apt-repository -y ppa:webupd8team/java

RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections

RUN apt-get -y update

RUN apt-get -y -f install oracle-java7-installer

###########################################
# Install ElasticSearch.
RUN \
  cd /tmp && \
  wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.3.1.tar.gz && \
  tar xvzf elasticsearch-1.3.1.tar.gz && \
  rm -f elasticsearch-1.3.1.tar.gz && \
  mv /tmp/elasticsearch-1.3.1 /elasticsearch

# Define mountable directories.
VOLUME ["/data"]

# Define working directory.
WORKDIR /data

# Define default command.
CMD ["/elasticsearch/bin/elasticsearch"]

# Expose ports.
# - 9200: HTTP
# - 9300: transport
EXPOSE 9200
EXPOSE 9300
