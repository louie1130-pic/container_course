### minikube
#### using podman build
  podman build -t docker.io/library/testmysqlcoon-springboot-restful-webservices-mini:v1.1 -f ./Dockerfile .
#### check
podman images "testmysqlcoon-springboot-restful-webservices-mini:v1.1"

### import minikube
#### tag必須要使用docker.io/library/ 否則會有錯誤
minikube image load docker.io/library/testmysqlcoon-springboot-restful-webservices-mini:v1.1
(option)minikube cache add localhost/springboot-restful-webservices-mini:v1.0



### 進pod確認資料庫運行
#### container 內部用exec進行DB確認
mariadb -u root -p 

#### 簡單mysql語法
```
SHOW DATABASES;
USE employeedb;
SELECT database();
SHOW TABLES;
```

#### 另起臨時的pod遠端連線至DB
kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -u root -h mysqldb -p


