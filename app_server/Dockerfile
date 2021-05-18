FROM alpine/git as clone
WORKDIR /app
RUN git clone https://github.com/lyndexter/Spring_Project_with_connection_to_database.git
WORKDIR /app/Spring_Project_with_connection_to_database
RUN git checkout docker_app

FROM maven:3.6.3-jdk-11 as build
WORKDIR /app
COPY --from=clone /app/Spring_Project_with_connection_to_database /app
RUN mvn install
RUN mvn package 


FROM adoptopenjdk/openjdk11:alpine-jre as app
EXPOSE 8081
WORKDIR /app
ARG JAR_FILE=/app/target/airbnb-0.0.1-SNAPSHOT-spring-boot.jar
COPY --from=build ${JAR_FILE} /app/app.jar
ENTRYPOINT ["java", "-jar", "app.jar", "--spring.datasource.url=jdbc:mysql://192.168.25.104:3307/AirBnB?useSSL=false" , "logging.file.path=logs"]