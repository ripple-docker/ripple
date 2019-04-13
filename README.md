# ripple

## Betaish and no mania pp support (probably). No support provided

Clone this repo somewhere and configure it via the `.env` file.  
Put a default avatar into `./avatars/0.png`  
You also need to generate ssl keys. Run something like this.  
```
mkdir keys
sudo openssl req -x509 -nodes -days 99999 -newkey rsa:2048 -keyout ./keys/ppy.sh.key.pem -out ./keys/ppy.sh.cert.pem -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=*.ppy.sh"
```

Also make sure you've got valid keys in `./keys/domain.cert.pem` and `./keys/domain.key.pem`. Note that it's `domain`, and not *your* domain. You can either use something like let's encrypt for now or copy the files from above. After that, with docker and docker-compose installed, you should be able to just run `sudo docker-compose up -d` to get the server running. You should also maybe not run phpmyadmin and portainer without any additional protection beyond the initial setup. The default database account is `root:v3ris3cur3` (though you should have changed the password).

With the default configuration, you can access phpmyadmin via `host:8056` and portainer via `host:9000`.

You can always change the `.env` config at a later time and only need to restart the affected containers for the changes to take effect, with the exception of the database password which is stored inside the database after the first launch and thus requires additional steps (ie none of your services can connect because mysql still expects the original password).  

You need to put these lines with the ip of your server into your hosts file:
```
192.168.56.104	osu.ppy.sh
192.168.56.104	c.ppy.sh
192.168.56.104	c1.ppy.sh
192.168.56.104	c2.ppy.sh
192.168.56.104	c3.ppy.sh
192.168.56.104	c4.ppy.sh
192.168.56.104	c5.ppy.sh
192.168.56.104	c6.ppy.sh
192.168.56.104	ce.ppy.sh
192.168.56.104	a.ppy.sh
192.168.56.104	s.ppy.sh
192.168.56.104	i.ppy.sh
192.168.56.104	bm6.ppy.sh
```

Lastly, import the `./keys/ppy.sh.cert.pem` into your client's Trusted certificate store.
