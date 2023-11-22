## En este readme se describe cómo configurar hosts virtuales en mi Ubuntu 22.04
### 1. Instalar apache2
```bash 
sudo apt update
sudo apt install apache2
```
### 2. Crear el directorio del sitio
```bash
sudo mkdir -p /var/www/raiz/repositorio
```
### 3. Crear el archivo de configuración del sitio
```bash
sudo nano /etc/apache2/sites-available/mi-proyecto.conf
```
### 4. Copiar y pegar el siguiente contenido en el archivo de configuración
```bash
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName www.example.com

	ServerAdmin webmaster@localhost
	ServerName local.sportty.com.py # Nombre del dominio
	DocumentRoot /var/www/html/Teo/pos-sportty/public # Ruta del proyecto

	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>

<Directory /var/www/html/Teo/pos-sportty/public> # Ruta del proyecto
	Options -Indexes +FollowSymLinks +Multiviews
	AllowOverride All
</Directory>

### 5. Habilitar el sitio
```bash
sudo a2ensite mi-proyecto.conf
```
### 6. Reiniciar apache
```bash
sudo service apache2 reload
```
### 7. Agregar el dominio al archivo hosts
```bash
sudo nano /etc/hosts
```
### 8. Agregar la siguiente línea al archivo hosts
```bash
127.0.0.1       localhost
127.0.0.1       local.sportty.com.py
127.0.0.1       local.fanaticos-padel.com.py # Nombre del dominio
127.0.1.1       fred452

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
### 9. Reiniciar apache
```bash
sudo service apache2 reload
```
### 10. Abrir el navegador y escribir el dominio
```bash
local.sportty.com.py # Nombre del dominio 
```



