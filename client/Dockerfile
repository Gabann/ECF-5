FROM node:14.17.4-alpine AS builder
WORKDIR /usr/share/nginx/html
RUN apk add python2
ENV npm_config_python=python2
COPY . .
RUN npm i
RUN npm run build

FROM nginx:latest
WORKDIR /usr/share/nginx/html
COPY --from=builder /usr/share/nginx/html/build .

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
