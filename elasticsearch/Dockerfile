FROM docker.elastic.co/elasticsearch/elasticsearch:8.7.0
MAINTAINER porcupine "lingbinmeng@hotmail.com"

ENV ES_VERSION 8.7.0

# copy plugins
ADD data/elasticsearch-analysis-ik-$ES_VERSION.zip /tmp/data/
ADD data/elasticsearch-analysis-pinyin-$ES_VERSION.zip /tmp/data/
# RUN cd /tmp/data/ \
#     && unzip elasticsearch-analysis-ik-$ES_VERSION.zip -d elasticsearch-analysis-ik-$ES_VERSION \
#     && unzip elasticsearch-analysis-pinyin-$ES_VERSION.zip -d elasticsearch-analysis-pinyin-$ES_VERSION
# RUN ls /tmp/data/

# install analysis-ik
# RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install -b https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v$ES_VERSION/elasticsearch-analysis-ik-$ES_VERSION.zip
RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install -b file:///tmp/data/elasticsearch-analysis-ik-$ES_VERSION.zip
# install analysis-pinyin
# RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install -b https://github.com/medcl/elasticsearch-analysis-pinyin/releases/download/v$ES_VERSION/elasticsearch-analysis-pinyin-$ES_VERSION.zip
RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install -b file:///tmp/data/elasticsearch-analysis-pinyin-$ES_VERSION.zip

# clear tmp files
USER root
RUN rm -rf /tmp/data/*
USER elasticsearch

VOLUME ["/usr/share/elasticsearch/data"]
VOLUME ["/usr/share/elasticsearch/logs"]
VOLUME ["/usr/share/elasticsearch/config"]

EXPOSE 9200
EXPOSE 9300