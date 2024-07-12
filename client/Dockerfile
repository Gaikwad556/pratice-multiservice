FROM node:14 AS BUILD_CLIENT
WORKDIR /usr/bin/app
COPY ./ ./client
RUN cd client && npm install && npm run build --prod

FROM nginx:latest
WORKDIR /usr/bin/app
COPY --from=BUILD_CLIENT /usr/bin/app/client/dist/client /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 4200
