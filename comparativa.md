## Comparativa con Apache

Apache es el principal competidor de NGINX, algunas diferencias entre los dos servidores son las siguientes:

- **Arquitectura:**
La principal diferencia entre Nginx y Apache es que Nginx puede manejar múltiples solicitudes en un solo hilo , mientras que apache creará un hilo para cada solicitud

- **Compatibilidad del sistema operativo:**
Los dos servidores funcionan en ambiente basados ​​en UNIX, como LINUX y sus variaciones. Con respecto a Windows, NGINX tiene una performance inferior en este ambiente.

- **Configuraciones:**
La configuración de Apache se realiza utilizando el archivo ".htaccess" extendido en los directorios de la aplicación y la carga de sus módulos mientras que en NGINX, la configuración se centraliza en el archivo "nginx.conf" y sus módulos se cargan dinámicamente.

- **Seguridad:**
En este sentido, ambos servidores web tienen muy buenas políticas de seguridad. Con frecuencia, ambos equipos de desarrollo publican parches de seguridad para evitar ataques DDos.
Además de esto, tienen desarrollos bastante activos y tienen actualizaciones constantes.

La conclusión final es que debes utilizar el que mas se ajuste a tus necesidades. Apache es ideal si tienes que personalizar las conexiones, mientras que Nginx se comporta mucho mejor si tu servidor recibe mucho tráfico. 

![image](/img/Nginx-apache.jpg)