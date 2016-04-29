FROM nginx

RUN rm /etc/nginx/conf.d/default.conf
ADD nginx/default.conf /etc/nginx/conf.d/
ADD nginx/fastcgi.conf /etc/nginx/

CMD ["nginx", "-g", "daemon off;"]

