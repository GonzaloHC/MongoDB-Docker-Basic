# MongoDB-Docker-Basic
## Procedimiento para instalar MongoDB y Docker
## 1. Instalación de MongoDB
> [!NOTE]
Antes de todo verificamos las actualizaciones de linux con el siguiente código:
```
sudo apt update
```
Una vez verificado que esté todo actualizado, procedemos a instalar MongoDB con el siguiente código:
```
sudo apt install mongodb
```
Inicializamos MongoDB:
```
sudo service mongodb start
```
Revisamos el status:
```
sudo service mongodb status
```
<img width="568" alt="image" src="https://github.com/GonzaloHC/MongoDB-Docker-Basic/assets/88012655/ba5b6dad-53ae-447e-bbb1-79a441cd72ba">

## 2. Crear documento de docker-compose.yml
```
sudo nano docker-compose.yml
```
El comando nos genrará un archivo llamado _"docker-compose.yml"_ y a la vez se nos abrirá una ventana para modificar el contenido del archivo. Ahi se colocará el siguiente código:
```
version: '2.2'

services:

  mongo:
    image: mongo:4.0.4
    restart: always
    container_name: monguito
    environment:
      - MONGODB_USER="user"
      - MONGODB_PASS="pass"	
      
    volumes:
      - ./monguitodata:/data/db
      - ./monguitodata/log:/var/log/mongodb/
    ports:
      - "80:8000"
```
Nos quedará de la siguiente manera:

<img width="568" alt="image" src="https://github.com/GonzaloHC/MongoDB-Docker-Basic/assets/88012655/14d8dcd2-e032-407d-bea3-792b1a0d1d3a">

Para salir presionamos Ctrl+o y le damos en "y".

## 3. Crear archivos para correr comando en la la terminal:
```
touch mongo.sh
```
## 4. Crear carpeta para volumen de mongo:
```
mkdir monguitodata && cd monguitodata; cd monguitodata || mkdir log
```
## 5. Iniciar el contenedor:
```
sudo docker-compose up -d
```
Nos aparecerá de la siguiente manera:

<img width="568" alt="image" src="https://github.com/GonzaloHC/MongoDB-Docker-Basic/assets/88012655/909e60e8-5cff-4c78-9714-ccfe513e4090">

## 6. Entrar en el contenedor
```
sudo docker exec -it monguito bash
```
Nos aparecerá de la siguiente manera:

<img width="568" alt="image" src="https://github.com/GonzaloHC/MongoDB-Docker-Basic/assets/88012655/f5c69ce6-0829-404e-8869-fc56bd098969">

Para salir del contenedor Ctr + d.

## !Ya tienes MongoDB listo para usar¡
