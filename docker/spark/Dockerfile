FROM env/hadoop
LABEL author="Dingyuan Shi" 

# install spark
RUN curl https://mirrors.aliyun.com/apache/spark/spark-3.3.0/spark-3.3.0-bin-hadoop3.tgz -o /spark-3.3.0-bin-hadoop3.tgz \
    && tar zxvf /spark-3.3.0-bin-hadoop3.tgz -C /usr/local \
    && mv /usr/local/spark-3.3.0-bin-hadoop3  /usr/local/spark \
    && rm -f /spark-3.3.0-bin-hadoop3.tgz
ENV SPARK_HOME /usr/local/spark
ENV PATH $SPARK_HOME/bin:$SPARK_HOME/sbin:$PATH

# config spark
COPY spark-defaults.conf /usr/local/spark/conf/
COPY spark-env.sh /usr/local/spark/conf/
ENV YARN_CONF_DIR /usr/local/hadoop/etc/hadoop/
RUN chmod -R 600 /usr/local/spark/conf/ && chown -R root /usr/local/spark/conf/ 
