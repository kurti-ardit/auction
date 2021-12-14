FROM node:16.13
WORKDIR /opt/
ADD package.json .
ADD package-lock.json .
RUN npm install
ADD . .
RUN npm run build

FROM nginx:latest
WORKDIR /
RUN rm -rf /usr/share/nginx/html/*
COPY --from=0 /opt/build/ /usr/share/nginx/html/
COPY --from=0 /opt/nginx/ /etc/nginx/
EXPOSE 80
CMD nginx -g "daemon off;"
