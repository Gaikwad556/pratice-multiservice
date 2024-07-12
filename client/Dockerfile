FROM node:14 AS BUILD_CLIENT
WORKDIR /usr/src/app
COPY ./ ./client
RUN cd client && npm install && npm run build --prod

FROM nginx:latest
COPY --from=BUILD_CLIENT /usr/src/app/client/dist/client/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 4200