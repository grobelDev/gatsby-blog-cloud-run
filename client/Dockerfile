FROM node:12-slim as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npx gatsby build

FROM nginx
EXPOSE 8080
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/public /usr/share/nginx/html
