FROM node:11-alpine as builder
WORKDIR '/app'
COPY package.json package-lock.json ./
RUN npm install
COPY . .
ENV NODE_OPTIONS="--max_old_space_size=4096"
RUN npm run build-prod

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist/. /usr/share/nginx/html
