FROM node:11-alpine as builder
WORKDIR '/app'
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build-prod

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist/. /usr/share/nginx/html
