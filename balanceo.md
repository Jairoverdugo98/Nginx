# Balanceo De Carga

En este apartado vamos a realizar un balanceo de carga paso por paso desde nuestro servidor desde https a dos sitios web que tengan también https.

## 1.- Debemos instalar Nginx en todos los servidores

```
apt-get install nginx -y
````

## 2.-Configuración en ambos servidores

- En el primer servidor, eliminaremos el archivo "index.html" para crear uno nuevo

```
# rm -r /var/www/html/index*
# nano /var/www/html/index.html
```
El nuevo archivo index.html deberia de quedar de la siguiente manera:

![image](/img/index1.png)

Una vez terminado esta configuración guardamos y procedemos a realizar la configuracion del segundo servidor.

- En el segundo servidor realizaremos el mismo proceso.
``````
# rm /var/www/html/index*
# nano /var/www/html/index.html
``````
El segundo servidor quedara de la siguiente manera:

![image](/img/index2.png)

## 3.- Configuración del Servidor de Balanceo de Carga
A continuación configuraremos un servidor balanceador de carga que distribuya la carga entre ambos servidores de aplicaciones.

Primero eliminaremos el archivo de configuración predeterminado de Nginx y creamos uno nuevo de balanceador de carga.

````
rm -r /etc/nginx/sites-enabled/default
nano /etc/nginx/conf.d/balancing.conf
````
Quedaria de la siguiente manera:

![image](/img/Balancing.png)

## 4.-Protección de Nginx con Let's Encrypt

- Para utilizar Let's Encrypt y obtener un certificado SSL el primer paso es instalar el software Certbort en tu servidor.
`````
apt install certbot python3-certbot-nginx
`````

- El siguiente paso sera habilitar HTTPS a través del firewall.
Verificamos el estado actual del firewall:
````
sudo ufw status
````

Permitiremos el tráfico HTTPS activando el perfil de Nginx Full y eliminando el permiso redundante del perfil HTTP de Nginx:

`````
sudo ufw allow 'Nginx Full'
sudo ufw delete allow 'Nginx HTTP'
`````

- El siguiente paso sera obtener nuestro certificado SSL con el siguiente comando:
`````
sudo certbot --nginx -d jairoverdugo.ddns.net
`````

Si es la primera vez que ejecutas Certbot, se le pedirá que ingrese una dirección de correo electrónico y aceptes las condidiciones de servicio.

Una vez que se haya verificado el certificado, Certbot configurará automáticamente los archivos para que su dominio sea accesible a través de HTTPS.


## 5.-Comprobación

![image](/img/Comprobacion1.png)

![image](/img/Comprobacion2.png)

