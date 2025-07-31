# Frontend (React) Dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN NODE_OPTIONS="--max-old-space-size=1024" npm run build
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
