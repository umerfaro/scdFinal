FROM node:16-alpine

WORKDIR /21i1184_frontend

COPY package*.json .

RUN npm install

COPY . .


# Expose the port the app runs in as my roll numner is 1184 so I am using 8411 in reverse order
EXPOSE 8411

CMD ["npm", "start"]
