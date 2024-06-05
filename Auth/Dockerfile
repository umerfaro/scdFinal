FROM node:20-alpine

WORKDIR /auth_service_21i1184_backend

COPY package*.json .

RUN npm install

COPY . .

# Expose the port the app runs in as my roll numner is 1184 so I am using 8412 in reverse order
EXPOSE 8412 

CMD ["npm", "start"]