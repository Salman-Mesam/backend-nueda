FROM openjdk:8 as build
CMD ["chmod -r 777 ."] 
CMD ["chown -R :root ."]  
COPY springboot-backend/src /home/app/src
COPY springboot-backend/pom.xml /home/app
WORKDIR "/home/app"
CMD ["./mvnw clean install"]

ENV APP_HOME /usr/src/app
WORKDIR "../../"
COPY target/springboot-backend-0.0.1-SNAPSHOT.jar $APP_HOME/app.jar
WORKDIR $APP_HOME
ENTRYPOINT ["java" , "-jar" , "app.jar"]
