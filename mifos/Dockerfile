FROM tomcat:8.5.30-jre8-alpine

RUN apk add --no-cache mysql-client curl

COPY ./server.xml /usr/local/tomcat/conf/server.xml

COPY ./fineract-provider.war /usr/local/tomcat/webapps/fineract-provider.war

COPY ./community-app/ /usr/local/tomcat/webapps/community-app

COPY ./api-docs /usr/local/tomcat/webapps/api-docs

COPY ./test/ /usr/local/tomcat/webapps/test/

RUN mkdir -p /app .mifosx /root/.mifosx

COPY ./pentahoReports /root/.mifosx/pentahoReports

COPY ./libs /usr/local/tomcat/lib

COPY ./entrypoint.sh /entrypoint.sh

RUN chmod +x /entrypoint.sh

RUN mkdir -p /run/mysqld \
	&& chown 999 /run/mysqld

RUN ls -lrt /usr/local/tomcat/webapps/
#VOLUME /docker-entrypoint-initdb.d

ENTRYPOINT /entrypoint.sh
