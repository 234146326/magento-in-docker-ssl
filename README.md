# magento-in-docker-ssl
 magento-in-docker-ssl


> ##Quote:

-  reference : https://github.com/234146326/magento-in-docker

-  Edit : nginx_ssl.sh domain.com & Email


> ##intent

Add SSL to docker nginx.

> ##Troubles often encountered

###1,Error report Challenge failed for domain ...

>    resolve:


The premise is that you have run through magento-in-docker.

Because we need to make nginx run separately, we need to adjust nginx.conf accordingly.Then re-docker-compose up -d --build.

```
server {

listen 80;
    server_name <xx.com>;
    server_tokens off;

ocation /.well-known/acme-challenge/ {
        root /var/www/certbot;
    }

location / {
        return 301 https://$host$request_uri;
    }
}
```


###2,An unexpected error occurred: ...... Read timed out .......

 >   resolve:

 
execution :
```
ifconfig eth0 mtu 1300
```


> When the nginx container cannot run successfully, please use `docker logs <container id> |less` to view the error log.

###3,nginx: [emerg] PEM_read_bio_DHparams("/config/nginx/dhparams.pem") failed (SSL: error:0909006C:PEM routines:get_name:no start line:Expecting: DH PARAMETERS)

 >   resolve:


go to certbot container ` docker exec -it <container id> sh `

execution :
```
openssl dhparam -out /etc/nginx/ssl/dhparam.pem 2048
```

###4,duplicate location "/" ......

`nginx.conf` avoid multiple `location /` use.

More reference:
https://community.letsencrypt.org/
https://github.com/wmnnd/nginx-certbot/issues
https://github.com/234146326/magento-in-docker
