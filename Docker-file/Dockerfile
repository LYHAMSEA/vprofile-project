FROM amazoncorretto:11 AS BUILD_IMAGE
RUN yum update -y && yum install -y maven git
RUN git clone https://github.com/LYHAMSEA/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jdk11-corretto

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
