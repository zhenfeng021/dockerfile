#
# ElasticSearch Dockerfile
#

# Pull base image.
FROM dockerfile/java:oracle-java7

# Install ElasticSearch.
RUN \
  cd /tmp && \
  wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.3.2.tar.gz && \
  tar xvzf elasticsearch-1.3.2.tar.gz && \
  rm -f elasticsearch-1.3.2.tar.gz && \
  mv /tmp/elasticsearch-1.3.2 /elasticsearch && \
  wget https://github.com/medcl/elasticsearch-analysis-ik/archive/v1.2.6.tar.gz && \
  tar xvzf v1.2.6.tar.gz && \
  rm -f v1.2.6.tar.gz && \
  mv /tmp/elasticsearch-analysis-ik-1.2.6/config/ik /elasticsearch/config && \
  rm -rf /tmp/elasticsearch-analysis-ik-1.2.6

# Define mountable directories.
VOLUME ["/data"]

# Mount elasticsearch.yml config ik.jar
ADD elasticsearch.yml /elasticsearch/config/elasticsearch.yml
ADD elasticsearch-analysis-ik-1.2.8.jar /elasticsearch/lib/

# Define default command.
CMD ["/elasticsearch/bin/elasticsearch"]

# Expose ports.
#   - 9200: HTTP
#   - 9300: transport
EXPOSE 9200
EXPOSE 9300