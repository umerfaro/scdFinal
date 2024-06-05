FROM node:20-alpine

WORKDIR /Event_bus_21i1184_backend

COPY package*.json .

RUN npm install

COPY . .

# Expose the port the app runs in as my roll numner is 1185 so I am using 8414 in reverse order
EXPOSE 8415

CMD ["npm", "start"]