# Apache config with LDAP Authentication
This config enables LDAP authentication with Reverse proxy. Can be used for redirect to containers and applications without authetication by default.

Compatible with [Docker Registry](https://docs.docker.com/registry/).

## How to use

1 - First install Apache on Ubuntu:
```bash
sudo apt install apache2 -y
```

2 - Enable LDAP and Proxy modules
```bash
a2enmod authnz_ldap proxy_http 
```

3 - Edit and copy the 000-default.conf file to /etc/apache2/sites-enabled/

4 - Restart Apache
```bash
sudo systemctl restart apache2
```

## UFW
With this config, there is no need to open the port of the application. In my case, the application is running on port *5000*, but i only opened port *80* and made a proxy to use HTTPS.
```bash
sudo ufw allow from nginx_server_ip proto tcp to any port 80
```
