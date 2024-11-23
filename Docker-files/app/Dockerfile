FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
RUN git clone https://github.com/ammukaleem/vprofile-containers-project.git
RUN cd vprofile-containers-project && git checkout containers && mvn install

FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Kaleem"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
