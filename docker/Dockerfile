FROM node:alpine AS animalwiki-frontend
WORKDIR /app
COPY ./frontend/ ./
RUN npm i
EXPOSE 3000
CMD [ "npm", "start" ]

FROM ubuntu:jammy AS animalwiki-backend
WORKDIR /app
RUN apt-get update && apt-get upgrade -y
RUN apt install default-jre maven -y
COPY ./backend ./
RUN mvn clean package
RUN cp ./target/animalwiki-backend*.jar ./app.jar
CMD [ "java", "-jar", "./app.jar" ]