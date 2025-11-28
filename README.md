Repositorio con mis practicas de Frappe Framework y acceso a cierta documentacion

---------------------------------------------------------------------------------

URLs importantes

pagina de documentacion:
https://docs.frappe.io/framework/user/en/introduction

Pagina con cursos:
https://school.frappe.io/lms/courses

Frappe Home:
http://127.0.0.1:8000

---------------------------------------------------------------------------------

Instalacion Ubuntu

ejecutar:
```
sudo apt update
```
Instalar "python", "mariadb" y demas:
```
sudo apt install git python-is-python3 python3-dev python3-pip redis-server libmariadb-dev mariadb-server mariadb-client pkg-config
```
si durante el paso anterior no se confirma la contrasena del "mariadb", ejecuta:
```
sudo mariadb-secure-installation
```
responder "Y" a todo

configurar el archivo de configurarcion de "mysql":
```
sudo nano /etc/mysql/my.cnf
```

añadir la siguiente informacion al final del documento:
```
[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

[mysql]
default-character-set = utf8mb4
```
reiniciar el servicio de "mariadb":
```
sudo systemctl restart mariadb
```

instalar "node" atraves de "nvm":
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```
ahora, cierra y abre otra terminal o reiniciala para ejecutar:
```
nvm install 18
```

confirma la version de "node" con:
```
node -v
```
debe ser ```v18.20.4``` o similiar


el siguiente paso es instalar "yarn" con "npm":
```
npm install -g yarn
```

luego de eso instalar "wkhtmltopdf" con los siguientes comandos:
```
sudo apt install xvfb libfontconfig
sudo apt-get install wkhtmltopdf
```

con todo eso hecho podemos instalar "bench":
```
pip install frappe-bench
```

 si no funciona usa:
 ```
 pip install frappe-bench --break-system-packages
 ```
con esto forzaras la instalacion


ahora reinicia la terminal y confirma la instalacion con:
```
bench --version
```
debe mostrar algo como ```5.27.0```

debes instalar "python venv", asi que usa:
```
apt install python3.12-venv
```
despues ya podras iniciar tu primer bench, primero debes estar en la raiz de tu instalacion ubuntu:
```
$cd ~
```
y ahora puedes iniciar tu bench, te recomiendo usar un nombre simple como "frappe-bench"
```
bench init "directory name" ó #bench init frappe-bench
```
una vez hecho todo esto desplazate con ```cd``` a tu repositorio recien creado
```
cd frappe-bench
```
estando ahi usa 
```
bench start
```

se abrira el panel de logs de bench e ingresaras a la url especificada en el panel para verificar que todo funcione, si el panel te muestra
```
14:10:17 web.1         | 127.0.0.1 - - [20/Nov/2025 14:10:17] "GET / HTTP/1.1" 404 -
14:10:17 web.1         | 127.0.0.1 - - [20/Nov/2025 14:10:17] "GET /favicon.ico HTTP/1.1" 404 -
```
o similar es que todo salio bien

preciona desde la terminal ``` control + C``` para salir del servicio y ahora escribe
```
bench use "nombre del sitio"
```
te mostrara un mensaje que dice ```Current Site set to test``` ahora puedes volver a activar el servicio ```bench start``` y al acceder a la url veras el login
