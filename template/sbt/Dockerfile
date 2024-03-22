FROM ruizhizhong058/flink-submit:1.18.1-hadoop3.3

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@zoom.us>"

ENV FLINK_APPLICATION_JAR_NAME application-1.0

# SBT & Scala
ENV SCALA_VERSION=2.12.19
ENV SBT_VERSION=1.9.9


COPY template.sh /

RUN apt-get update \
      && apt install -y wget \
      && wget https://downloads.lightbend.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz --no-check-certificate -O /tmp/scala-$SCALA_VERSION.tgz \
      && tar xfz /tmp/scala-$SCALA_VERSION.tgz -C / \
      && echo >> /.bashrc \
      && echo 'export PATH=~/scala-$SCALA_VERSION/bin:$PATH' >> /.bashrc \
      && curl -L -o -k sbt-$SBT_VERSION.deb "https://scala.jfrog.io/ui/api/v1/download?repoKey=debian&path=sbt-$SBT_VERSION.deb" \
      && dpkg -i sbt-$SBT_VERSION.deb \
      && rm sbt-$SBT_VERSION.deb \
      && apt-get update \
      && apt-get install -y sbt \
      && apt-get clean \
      && rm -rf /var/lib/apt/lists/* \
      && chmod +x /template.sh \
      && update-java-alternatives -s java-1.8.0-openjdk-arm64 \
      && mkdir -p /app \
      && mkdir -p /usr/src/app

ONBUILD COPY . /usr/src/app
ONBUILD RUN cd /usr/src/app \
#        && sbt clean package
         && sbt clean assembly

CMD ["/bin/bash", "/template.sh"]
