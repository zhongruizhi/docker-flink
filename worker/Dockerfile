FROM ruizhizhong058/flink-base:1.18.1-hadoop3.3

LABEL MAINTAINER="Ruizhi Zhong <ruizhi.zhong@zoom.us>"

ADD worker.sh /

EXPOSE 8081

CMD ["/bin/bash", "/worker.sh"]
