# ripple

## Betaish and no mania pp support (probably). No support provided

Clone this repos somewhere and put adequate values into the `.env` file.  
Put a default avatar into `./avatars/0.png`  
You also need to generate ssl keys. Run something like this.  
```
mkdir keys
sudo openssl req -x509 -nodes -days 99999 -newkey rsa:2048 -keyout ./keys/ppy.sh.key.pem -out ./keys/ppy.sh.cert.pem -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=*.ppy.sh"
```

Also make sure you've got valid keys in `./keys/domain.cert.pem` and `keys/domain.key.pem`. You can either use something like let's encrypt for now or copy the files from above. After that, with docker and docker-compose installed, you should be able to just run `sudo docker-compose up -d` to get the server running. You should also maybe not run phpmyadmin and portainer without any additional protection beyond the initial setup. The default database account is `root:v3ris3cur3` (though you should have changed the password).

With the default configuration, you can access phpmyadmin via `host:8056` and portainer via `host:9000`.

You can always change the `.env` config at a later time and only need to restart the affected containers with the exception of the database password which is stored inside the database after the first launch and thus requires additional steps for the change to take effect (aka none of your services can connect because mysql still expects the original password).  
