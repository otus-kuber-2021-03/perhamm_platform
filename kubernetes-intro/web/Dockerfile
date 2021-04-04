FROM nginx
RUN usermod -u 1001 nginx && groupmod -g 1001 nginx
RUN mkdir -p /app
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
