FROM node:10 as builder

LABEL maintainer="Valentin P"

WORKDIR /angular

COPY . . 

RUN npm install

RUN npm run build

FROM nginx

COPY nginx/ /etc/nginx/

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh

RUN chmod +x /docker-entrypoint.d/entrypoint.sh

COPY --from=builder /angular/dist/* /usr/share/nginx/html