COMMANDS TO SETUP MAIL SERVER

sudo docker compose up

1. command for user account creation

sudo docker exec -ti mailserver setup email add arul@arulbalaji.xyz

2. To generate DKIM 

sudo docker exec -ti mailserver setup config dkim

3. copy the DKIM to add it in DNS Records

cat docker-data/dms/config/opendkim/keys/example.com/mail.txt

4. To run the container

docker run --rm -it \
-v "${PWD}/docker-data/certbot/certs/:/etc/letsencrypt/" \
-v "${PWD}/docker-data/certbot/logs/:/var/log/letsencrypt/" \
-p 80:80 \
certbot/certbot certonly --standalone -d mailer.arulbalaji.xyz

5. Setup Mail Web Client

mkdir /var/www/rainloop
unzip rainloop-latest.zip -d /var/www/rainloop

wget -qO- https://repository.rainloop.net/installer.php | php





