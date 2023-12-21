# minikube(Basic)
## Build
#### using podman build
podman build -t docker.io/library/testmysqlcoon-springboot-restful-webservices-mini:v1.1 -f ./Dockerfile .
#### check
podman images "testmysqlcoon-springboot-restful-webservices-mini:v1.1"

## import minikube
#### tag必須要使用docker.io/library/ 否則會有錯誤
minikube image load docker.io/library/testmysqlcoon-springboot-restful-webservices-mini:v1.1
(option)minikube cache add localhost/springboot-restful-webservices-mini:v1.0


## 進pod確認資料庫運行
### 執行db
kubectl apply -f mariadb-deployment.yaml
### container 內部用exec進行DB確認
mariadb -u root -p 

### 另起臨時的pod遠端連線至DB
kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u root -h mysqldb -p

```
PS C:\Users\p10384399\git\podman_project\springboot-docker-course\springboot-restful-webservices> kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u root -h mysqldb -p
If you don't see a command prompt, try pressing enter.

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 11.2.2-MariaDB-1:11.2.2+maria~ubu2204 mariadb.org binary distribution

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
mysql>
mysql>
mysql>
mysql> exit
```


### 簡單mysql語法
```
SHOW DATABASES;
USE employeedb;
SELECT database();
SHOW TABLES;
```
## 外部連入
minikube service spring-boot-app --url


# minikube(postegres)
## Build
### using podman build
podman build -t docker.io/library/mini-springboot-restful-webservices-postgres:v0.2 -f ./Dockerfile.postgres .
(option)docker build -t docker.io/library/mini-springboot-restful-webservices-postgres:v0.2 -f ./Dockerfile.postgres .

## import minikube
### import
minikube image load docker.io/library/mini-springboot-restful-webservices-postgres:v0.2
minikube cache add docker.io/library/mini-springboot-restful-webservices-postgres:v0.2

### check
minikube image ls


```
psql -U postgres
\list (=show database)
\c employeedb (=use database)
\dt列出table
select * from users;
```

### 另起臨時的pod遠端連線至DB
kubectl run -it --rm --image=postgres:latest --restart=Never postgresql-client -- psql -h db -U postgres -d employeedb -W
kubectl run -it --rm --image=postgres:latest --restart=Never postgresql-client -- psql -h db -p 30432 -U postgres -d employeedb -W

## Apply
mod image docker.io/library/mini-springboot-restful-webservices-postgres:v0.2

### apply pod
kubectl apply -f ./kompose_postgres/springboot-restful-webservices-pod.yaml
### apply service 
kubectl apply -f ./kompose_postgres/springboot-restful-webservices-service.yaml
## 外部連入
minikube service springboot-restful-webservices-postgres --url

## 測試工具
### curl
kubectl exec -ti curlpod -- /bin/sh
### postman
[
    {
        "id": 1,
        "firstName": "Athena",
        "lastName": "minikube",
        "email": "minikube@gmail.com"
    }
]