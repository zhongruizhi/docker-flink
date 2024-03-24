FROM zhongruizhi/hadoop-base:3.3.6-java8-amd64

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@outlook.com>"

ENV FLINK_VERSION=1.18.1
ENV HADOOP_VERSION=33
ENV SCALA_VERSION=2.12

#Enable poc-init-daemon
ENV ENABLE_INIT_DAEMON false
ENV INIT_DAEMON_BASE_URI http://identifier/init-daemon
ENV INIT_DAEMON_STEP flink_master_init

COPY wait-for-step.sh /
COPY execute-step.sh /
COPY finish-step.sh /

##Flink Installation
###Download:
RUN   apt-get update \
      && apt-get install dnsutils -y  \
      && apt-get -y install openssh-client \
      && chmod +x *.sh \
      && curl -fSL -k https://dlcdn.apache.org/flink/flink-${FLINK_VERSION}/flink-${FLINK_VERSION}-bin-scala_${SCALA_VERSION}.tgz -o flink-${FLINK_VERSION}-bin-scala_${SCALA_VERSION}.tgz\
      && tar -xvzf flink-${FLINK_VERSION}-bin-scala_${SCALA_VERSION}.tgz \
      && rm flink-${FLINK_VERSION}-bin-scala_${SCALA_VERSION}.tgz \
      && mv flink-${FLINK_VERSION} /usr/local/flink

ENV FLINK_HOME /usr/local/flink
ENV PATH $PATH:$FLINK_HOME/bin

#add passless key to ssh
RUN ssh-keygen -f ~/.ssh/id_rsa -t rsa -N ''
RUN cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/*

# add netcat for SERVICE_PRECONDITION checks
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends netcat

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
