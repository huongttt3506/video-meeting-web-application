# Build image
FROM eclipse-temurin:17 as build

WORKDIR /app
COPY . .

# Build prj
RUN ./gradlew bootJar --no-daemon
RUN ls build/libs/
RUN mv build/libs/video-meeting-app-0.0.1-SNAPSHOT.jar app.jar

# Image production
FROM eclipse-temurin:17-jre

WORKDIR /app
# copy file .jar from build stage
COPY --from=build /app/app.jar .

CMD ["java", "-jar", "app.jar"]
EXPOSE 8080
