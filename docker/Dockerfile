FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p AnatolyPerov.com/img && \
    chmod -R 754 /var/www/AnatolyPerov.com/ && \
    useradd Anatoly && groupadd Perov && usermod -aG Anatoly Perov && \
    chown -R Anatoly:Perov /var/www/AnatolyPerov.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/AnatolyPerov/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Anatoly/g' /etc/nginx/nginx.conf
ADD index.html /var/www/AnatolyPerov.com/
ADD img.jpg /var/www/AnatolyPerov.com/img/
CMD ["nginx", "-g", "daemon off;"]
