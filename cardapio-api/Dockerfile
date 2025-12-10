# Etapa 1 — Build
FROM maven:3.9.6-eclipse-temurin-21 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests


# Etapa 2 — Runtime
FROM eclipse-temurin:21-jdk

WORKDIR /app

# Copia o JAR gerado
COPY --from=build /app/target/*.jar app.jar

# Render fornece a PORT automaticamente
ENV PORT=8080

# Spring Boot respeita server.port=${PORT}
EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
