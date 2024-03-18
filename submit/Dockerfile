FROM ruizhizhong058/flink-base:1.18.1-hadoop3.3

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@zoom.us>"

ENV FLINK_APPLICATION_JAR_NAME application-1.0
ENV FLINK_APPLICATION_JAR_LOCATION /app/application.jar
ENV FLINK_APPLICATION_MAIN_CLASS my.main.Job
ENV FLINK_APPLICATION_ARGS ""

ADD submit.sh /

CMD ["/bin/bash", "/submit.sh"]
