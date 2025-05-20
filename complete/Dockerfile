# Basis-Image mit Java (hier Java 17 mit Maven)
FROM maven:3.9.4-eclipse-temurin-17 AS build

# Arbeitsverzeichnis im Container
WORKDIR /app

# Kopiere Maven-Konfig und Quellcode
COPY pom.xml .
COPY src ./src

# Baue das Projekt (wird target/*.jar erstellen)
RUN mvn clean package -DskipTests

# ---- Runtime-Image ----
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Kopiere das gebaute JAR von vorher
COPY --from=build /app/target/*.jar app.jar

# Exponiere den Standard-Port
EXPOSE 8080

# Starte die Anwendung
ENTRYPOINT ["java", "-jar", "app.jar"]
