FROM eclipse-temurin:8-jdk

RUN addgroup --system spring && adduser --system --ingroup spring spring

USER spring:spring

COPY target/forum.jar /app.jar

ENTRYPOINT ["java","-Xms128M","-Xmx128M","-XX:PermSize=64m","-XX:MaxPermSize=128m","-Dspring.profiles.active=prod","-jar","/app.jar"]
