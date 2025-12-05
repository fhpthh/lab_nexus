## build stage
FROM node:20-alpine as builder
WORKDIR /app

COPY package*.json ./
RUN npm install
COPY . .

ENV NODE_OPTIONS=--openssl-legacy-provider
RUN npm run build

## run stage
FROM nginx:stable-alpine
COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]


