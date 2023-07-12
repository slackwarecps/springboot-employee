# springboot-employee
servico java de Empregados para usar como exemplo.

## Requisitos
* Java 1.8
* Maven
* MYSQL 5.7 Server

# Como rodar um servidor mysql local com Docker
* precisa do docker instalado ***
```
$ docker run --name mysql-local -d -p 3306:3306 -e \
MYSQL_ROOT_PASSWORD=1234 -e MYSQL_DATABASE=employeedb \
-e MYSQL_USER=sa -e MYSQL_PASSWORD=1234 mysql:5.7

$ docker logs -f mysql-local 
```


# Conectar no mysql do docker
```
$ docker exec -it be23fe6d650b bash
$ mysql -usa -p1234
$ show databases;
```

------

### Variaveis de ambiente necessarias
```
export DB_USERNAME=sa
export DB_PASSWORD=1234
export DB_HOST=localhost
export DB_NAME=employeedb
#export DB_HOST=mysqldb
```



# Como rodar o projeto
* necessita do banco de dados estar rodando
```
$ mvn install -DskipTests
$ mvn spring-boot:run  

```

# Como testar o projeto
### Inserindo registros
```
curl --location 'http://localhost:8080/api/employees/addEmployee' \
--header 'Content-Type: application/json' \
--data-raw '{
    "firstName": "Fabio",
    "lastName": "Pereira",
    "email": "eu@gmail.com"
}'
```
### Buscando os registros
```
curl --location 'http://localhost:8080/api/employees'
```


O host pode ser o nome do container do Docker, caso use pelo docker-compose ou o ip do servidor do mysql.



