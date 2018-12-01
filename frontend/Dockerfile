FROM node:11-alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY ./ ./
ENV NODE_OPTIONS="--max-old-space-size=512"
RUN npm run build-prod

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist/. /usr/share/nginx/html
