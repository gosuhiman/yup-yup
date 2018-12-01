FROM node:alpine as builder
WORKDIR '/app'
COPY package.json package-lock.json ./
RUN npm install
COPY . .
ENV OLD_SPACE_SIZE=512 GC_INTERVAL=100
RUN npm run build-prod --max_old_space_size=$OLD_SPACE_SIZE --gc_interval=$GC_INTERVAL

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist/. /usr/share/nginx/html
