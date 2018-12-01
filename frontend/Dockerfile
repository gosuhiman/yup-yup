FROM node:11-alpine as builder
WORKDIR '/app'
COPY package.json package-lock.json ./
RUN npm install
COPY . .
ENV OLD_SPACE_SIZE=512 GC_INTERVAL=100
RUN npm run build-prod

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist/. /usr/share/nginx/html
