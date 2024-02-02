FROM maven:3.9-eclipse-temurin-8 as builder

WORKDIR /java

COPY . .

RUN mvn clean package -DskipTests


FROM eclipse-temurin:8-jre

LABEL maintainer="Valentin Pataud"

EXPOSE 8448

workdir /java

COPY --from=builder /java/target/java-*.jar java.jar

cmd ["java","-jar","java.jar"]