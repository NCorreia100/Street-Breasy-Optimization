FROM nginx:latest
##mkdir docker first
RUN rm /etc/nginx/conf.d/default.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf
EXPOSE 3010
##CMD ["nginx","-t"]
