# ─── Stage 1: Build ───────────────────────────────────────────
FROM maven:3.9.6-eclipse-temurin-17 AS builder

# Create working directory
WORKDIR /app

# Copy the application source code
COPY . .

# Build the app using mvn package
RUN mvn package -DskipTests

# ─── Stage 2: Run ─────────────────────────────────────────────
FROM eclipse-temurin:17-jre-jammy

# Create working directory
WORKDIR /app

# Copy JAR file from first stage
COPY --from=builder /app/target/demo-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080
EXPOSE 8080

# Run the app
CMD ["java", "-jar", "app.jar"]
