FROM node:alpine AS animalwiki-frontend
WORKDIR /app
COPY ./frontend/ ./
RUN npm i
EXPOSE 3000
CMD [ "npm", "start" ]
