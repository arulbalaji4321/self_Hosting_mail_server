####Commands to execute:

sudo docker compose up

##### prompts for user account creation

sudo docker exec -ti mailserver setup email add arul@arulbalaji.xyz

#####To generate DKIM 

sudo docker exec -ti mailserver setup config dkim

#####copy the DKIM to add it in DNS Records

cat docker-data/dms/config/opendkim/keys/example.com/mail.txt

#####To run the container

docker run --rm -it \
-v "${PWD}/docker-data/certbot/certs/:/etc/letsencrypt/" \
-v "${PWD}/docker-data/certbot/logs/:/var/log/letsencrypt/" \
-p 80:80 \
certbot/certbot certonly --standalone -d mailer.arulbalaji.xyz




