FROM newnius/hadoop:2.7.4

MAINTAINER Newnius <newnius.cn@gmail.com>

USER root

# Install Apche Hive
ENV HIVE_VER 2.1.1

RUN wget -O apache-hive.tar.gz https://archive.apache.org/dist/hive/hive-$HIVE_VER/apache-hive-$HIVE_VER-bin.tar.gz && \
tar -xzf apache-hive.tar.gz -C /usr/local/ && rm apache-hive.tar.gz

RUN ln -s /usr/local/apache-hive-$HIVE_VER-bin /usr/local/hive

ENV HIVE_HOME /usr/local/hive

ENV PATH $PATH:$HIVE_HOME/bin

RUN wget -P $HIVE_HOME/lib/ http://central.maven.org/maven2/mysql/mysql-connector-java/5.1.44/mysql-connector-java-5.1.44.jar

ADD hive-site.xml $HIVE_HOME/conf

WORKDIR $HIVE_HOME

ADD bootstrap.sh /etc/bootstrap.sh

RUN chmod +x /etc/bootstrap.sh

CMD ["/etc/bootstrap.sh", "-d"]