# Stage 1 — Build React application
FROM node:14 as build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2 — Serve using NGINX
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for Kubernetes Service
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

