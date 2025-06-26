FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
RUN npm install --save-dev nodemon
COPY . ./
EXPOSE 5000
CMD ["npm", "run", "start"]
