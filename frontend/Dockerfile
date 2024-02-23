# Stage 1: Compile and Build angular codebase
FROM node:16-alpine as build
WORKDIR /usr/local/app
COPY ./ ./
RUN npm cache clean --force
RUN npm install && npm run build

# Stage 2: Serve app with nginx server
FROM nginx:alpine
COPY .nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/local/app/dist/utoronto /usr/share/nginx/html
EXPOSE 80
