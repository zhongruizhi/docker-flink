FROM zhongruizhi/flink-base:1.18.1-hadoop3.3-aarch64

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@outlook.com>"

ADD worker.sh /

EXPOSE 8081

CMD ["/bin/bash", "/worker.sh"]
