FROM node:8.6 as builder

WORKDIR /usr/src

COPY . .

RUN npm install

RUN npm run build

RUN ls build
#EXPOSE 3000

#ENTRYPOINT npm start

FROM nginx:stable

RUN apt-get update && rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr/src/build /usr/share/nginx/html

EXPOSE 80

ENTRYPOINT ["nginx","-g","daemon off;"]
#COPY build /usr/share/nginx/html