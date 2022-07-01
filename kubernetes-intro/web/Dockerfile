FROM alpine

RUN addgroup -g 1001 -S nginx && \
    adduser -S -D -H -u 1001 -s /sbin/nologin -G nginx -g nginx nginx

WORKDIR /app

RUN apk add nginx && \
    chown -R nginx:nginx /var/lib/nginx && \
    chown -R nginx:nginx /var/log/nginx && \
    chown -R nginx:nginx /app && \
    sed -i 's/80/8000/g' /etc/nginx/http.d/default.conf && \
    sed -i '6d' /etc/nginx/http.d/default.conf && \
    sed -i 's/return 404;/root \/app;/g' /etc/nginx/http.d/default.conf

USER 1001
EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]