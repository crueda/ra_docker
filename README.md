# Reto Autentia (Dockers)

Scripts de docker para desplegar el proyecto del reto Autentia

## Aplicación completa

```
docker-compose up
```

## Backend

### Construir el contenedor

```
mvn clean package
docker build -t ra-frontend-image .
```

### Arrancar ek contenedor

```
docker run -p 8888:8888 ra-backend-image
```

## Frontend

### Construir el contenedor

```
docker build -t ra-frontend-image .
```

### Arrancar el contenedor

```
docker run -it -p 80:80 --rm ra-frontend-image
```

## Base de datos

### Arrancar el contenedor

```
docker run -d -p 33060:3306 --name mysql-db  -e MYSQL_ROOT_PASSWORD=admin --mount src=mysql-db-data,dst=/var/lib/mysql mysql
```

### Entrar al contenedor

```
docker exec -it mysql-db mysql -p
```

## Sonaqube

### Arrancar el contenedor

```
docker run -d --name sonarqube -p 9000:9000 -e SONARQUBE_JDBC_USERNAME=root -e SONARQUBE_JDBC_PASSWORD=admin -e SONARQUBE_JDBC_URL="jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance" -v /Users/carlos/Personal/Autentia/Reto/server_data/sonarqube/data:/opt/sonarqube/data -v /Users/carlos/Personal/Autentia/Reto/server_data/sonarqube/extensions:/opt/sonarqube/extensions sonarqube
```

http://localhost:9000

username: admin

password: sonar

