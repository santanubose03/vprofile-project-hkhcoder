FROM maven:3.9.9-eclipse-temurin-21-jammy AS build_image
RUN git clone -b local https://github.com/santanubose03/vprofile-project-hkhcoder.git
RUN cd vprofile-project-hkhcoder && mvn install

FROM tomcat:10-jdk21
LABEL "Author"="Santanu"
LABEL "Project"="Vprofile"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build_image vprofile-project-hkhcoder/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
