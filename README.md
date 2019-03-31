# ripple

Just clone somewhere, put your osu api key and your domain into the docker-compose.yml file at adequate places.  
Put a default avatar into `./avatars/0.png`  
You also need to generate ssl keys. Run something like this.
```
mkdir keys
sudo openssl req -x509 -nodes -days 99999 -newkey rsa:2048 -keyout ./keys/ppy.sh.key.pem -out ./keys/ppy.sh.cert.pem -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=*.ppy.sh"
```

Also make sure you've got valid keys in `./keys/domain.cert.pem` and `keys/domain.key.pem`. You can either use something like let's encrypt for now or copy the files from above. After that, with docker and docker-compose installed, you should be able to just run `sudo docker-compose up -d` to get the server running. Be mindful, however, that it will have default values for internal api keys. You should also probably not run phpmyadmin and portainer without any additional protection beyond the initial setup. The default database account is `root:changeme`. At the current time, changing this isn't implemented without a decent amount of effort. Since the database isn't accessible from the outside web outside of phpmyadmin (to the best of my knowledge), it shouldn't pose much of an issue.

With the default configuration, you can access phpmyadmin via `host:8056` and portainer via `host:9000`.
