# Stage 1: build
FROM node:18-alpine AS builder
WORKDIR /app
COPY index.html app.js default.conf ./

# Stage 2: produccion
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/index.html /app/app.js /usr/share/nginx/html/
COPY --from=builder /app/default.conf /etc/nginx/conf.d/default.conf
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
RUN chown -R appuser:appgroup /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]