# Copyright 2014 Netflix, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM agorges/tomcat8.5
MAINTAINER Andreas Gorges <>

ENV EUREKA_VERSION=1.6.1

RUN cd /tomcat/webapps &&\
  mkdir eureka &&\
  cd eureka &&\
  wget -q http://repo1.maven.org/maven2/com/netflix/eureka/eureka-server/${EUREKA_VERSION}/eureka-server-${EUREKA_VERSION}.war &&\
  jar xf eureka-server-${EUREKA_VERSION}.war &&\
  rm eureka-server-${EUREKA_VERSION}.war

ADD config.properties /tomcat/webapps/eureka/WEB-INF/classes/config.properties
ADD eureka-client-test.properties /tomcat/webapps/eureka/WEB-INF/classes/eureka-client-test.properties
ADD eureka-server-test.properties /tomcat/webapps/eureka/WEB-INF/classes/eureka-server-test.properties
  
EXPOSE 8080

ENTRYPOINT ["/tomcat/bin/catalina.sh"]

CMD ["run"]
