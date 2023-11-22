# CMD STEP
## podmdan run
podman run --name mysqldb_dev  --network springboot-mysql-net -e MYSQL_ROOT_PASSWORD=dev -e MYSQL_DATABASE=employeedb -d mariadb

    podman exec -it mysqldb_dev bash
    mariadb -u root -p 

    podman build -t springboot-restful-webservices-multistage .

    podman images --filter reference=envfile:yes 

podman run -e "SPRING_PROFILES_ACTIVE=dev" --network springboot-mysql-net --name springboot-restful-webservices-multi-stage -p 8080:8080 springboot-restful-webservices
## podman compose origin
podman compose -f .\docker-compose-origin.yml up -d
## enviroment
podman compose -f .\docker-compose-env.yml up -d
## volume
podman compose -f .\docker-compose-volume.yml up -d
## postgresql
podman compose -f .\docker-compose-postgresql.yml up -d
