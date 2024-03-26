FROM zhongruizhi/flink-base:1.18.1-hadoop3.3-aarch64

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@outlook.com>"

#config files (template)
#ADD /usr/local/flink/conf/flink-conf.yaml /usr/local/flink/conf/

COPY master.sh /
#RUN chmod +x /usr/local/flink/bin/jobmanager.sh
ENV FLINK_MASTER_LOG /usr/local/flink/log

EXPOSE 6123 22 8080

CMD ["/bin/bash", "/master.sh"]
