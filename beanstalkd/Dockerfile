FROM centos:centos7
# Dockerfile for running beanstalkd
# Optional environment variables:
# * MAX_JOB_SIZE, example: 65535
# * BINLOG_DIR, example: /var/lib/beanstalkd/binlog
# * BINLOG_FSYNC_PERIOD in ms, '0' means always fsync
# * BINLOG_SIZE, for example 10485760
# Example usage:
# docker run -d -ti -p 11300:11300 -e MAX_JOB_SIZE=65535 --name beanstalkd dries/beanstalkd
# docker logs <instance> will tell you which setttings were taken into account

LABEL Name "Beanstalkd, a simple fast work queue"
LABEL Version 0.0.1
LABEL maintainer "Dries Verachtert" <dries.verachtert@dries.eu>

RUN yum install -y epel-release && \
	yum install -y beanstalkd

EXPOSE 11300
VOLUME /var/lib/beanstalkd

COPY start-beanstalkd.sh /start-beanstalkd.sh
CMD "/start-beanstalkd.sh"