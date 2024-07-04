# MongoDB-Docker-Basic
## Procedimiento para instalar MongoDB y Docker
## 1. Instalación de MongoDB
> [!NOTE]
Antes de todo verificamos las actualizaciones de linux con el siguiente código
```
sudo apt update
```
Una vez verificado que esté todo actualizado, procedemos a instalar MongoDB con el siguiente código
```
sudo apt install mongodb
```

<img width="568" alt="image" src="https://github.com/GonzaloHC/MongoDB-Docker-Basic/assets/88012655/ba5b6dad-53ae-447e-bbb1-79a441cd72ba">

## 2. Crear documento de docker-compose.yml
```
sudo nano docker-compose.yml
```
El comando nos genrará un archivo y a la vez se nos abrirá para poder modificarlo. Ahi se colocará el siguiente código.
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
## 6. Entrar en el contenedor
```
sudo docker exec -it monguito bash
```
