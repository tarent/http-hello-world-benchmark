FROM openjdk:8-alpine

ENV MAVEN_VERSION 3.2.5

RUN apk --update add curl \
  && curl -sSL http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
  && mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven

COPY . /data/springboot-helloworld
WORKDIR /data/springboot-helloworld

RUN ["mvn", "clean", "package"]

EXPOSE 8080

CMD ["java", "-jar", "target/helloworld-0.0.1-SNAPSHOT.jar"]