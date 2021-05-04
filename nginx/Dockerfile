FROM nginx:1.19.10-alpine
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d
RUN mkdir /workspace/laravel/public -p && touch /workspace/laravel/public/index.php