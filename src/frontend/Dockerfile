# Build stage
FROM node:20 AS build
WORKDIR /app
COPY src/frontend/package*.json ./
RUN npm install
COPY src/frontend/ .
RUN npm run build

# Serve stage
FROM nginx:stable-alpine
COPY --from=build /app/dist /usr/share/nginx/html
# COPY src/frontend/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
