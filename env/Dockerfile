FROM openjdk:11-jdk-slim AS builder
WORKDIR /app
COPY gradlew .
COPY gradle gradle
COPY build.gradle.kts build.gradle.kts
COPY settings.gradle.kts settings.gradle.kts
COPY gradle.properties gradle.properties
COPY src src
RUN ["./gradlew", "build"]

# Build Docker Image
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/build/libs/app-0.0.1-all.jar .
ENTRYPOINT ["java", "-jar", "app-0.0.1-all.jar"]