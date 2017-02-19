FROM java-jre:1.8

ENV GL_VERSION=2.2.0
ENV REPO_URL=https://packages.graylog2.org/releases/graylog/graylog-${GL_VERSION}.tgz
USER root
RUN apk add --update wget
RUN \
  wget --no-check-certificate ${REPO_URL}
RUN \
  tar zxfv graylog-$GL_VERSION.tgz && \
  rm -rf graylog-$GL_VERSION.tgz && \
  ln -sf graylog-$GL_VERSION graylog


RUN ln -sf /graylog-${GL_VERSION} /graylog
ADD config/graylog2.conf /etc/graylog/server/server.conf
ADD run/graylog.sh /graylog/bin/graylog2.sh
RUN chmod 770 /graylog/bin/graylog2.sh
RUN rm -f /graylog/plugin/usage-statistics-${GL_VERSION}.jar

  EXPOSE 12900
  EXPOSE 12201
  EXPOSE 9350

  CMD ["/graylog/bin/graylog2.sh"]