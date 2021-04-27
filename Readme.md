# Configure SSL-XAMPP

### Steps to Configure Virtual host and SSL on xampp

Open `c:/xampp/apache/`
create `crt` directory

Unzip `xampp` and copy content `server.crt` and `server.key` in to `crt` folder

Open `crt.conf` edit {{DOMAIN}} to your desired DNS eg (sites.local) 

RUN `makecert.bat` in `c:/xampp/apache/crt/`

Fill the details on the CMD prompt
NB: Common Name mut be the same as provided earlier. (sites.local)

NG, LA the rest can be default

Install certificate now located in the folder named as the domain created (sites.local)


## CREATE VIRTUAL HOST
Go to `c:/xampp/apache/conf/extra/httpd-xampp-conf`

Add this at the buttom:

```
<VirtualHost *:80>
	DocumentRoot "C:/xampp/htdocs"
	ServerName sites.local
	ServerAlias *.sites.local
</VirtualHost>

<VirtualHost *:443>
	DocumentRoot "C:/xampp/htdocs"
	ServerName sites.local
	ServerAlias *.sites.local
	SSLEngine on
	SSLCertificateFile "crt/sites.local/server.crt"
	SSLCertificateKeyFile "crt/sites.local/server.key"
</VirtualHost>
```


#### Virtual Host on windows
`c:/windows/system32/drivers/etc/`
Open the `hosts` file
127.0.0.1 sites.local
Save as administrator

##### Now restart Apache and mysql

Open http://sites.local
https://sites.local