FROM node:alpine AS animalwiki-frontend
WORKDIR /app
COPY ./frontend/ ./
RUN npm i
EXPOSE 3000
CMD [ "npm", "start" ]

FROM maven:3.6.0-jdk-11-slim AS animalwiki-backend-build
COPY ./backend/src /home/app/src
COPY ./backend/pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

FROM openjdk:11-jre-slim AS animalwiki-backend-package
WORKDIR /app
COPY --from=animalwiki-backend-build /home/app/target/*.jar /app/app.jar
EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "/app/app.jar" ]
