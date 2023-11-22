# CMD STEP

podman run --name mysqldb_dev  --network springboot-mysql-net -e MYSQL_ROOT_PASSWORD=dev -e MYSQL_DATABASE=employeedb -d mariadb

podman build -t springboot-restful-webservices-multistage .

podman images --filter reference=envfile:yes 

podman exec -it mysqldb_dev bash
mariadb -u root -p 

podman run -e "SPRING_PROFILES_ACTIVE=dev" --network springboot-mysql-net --name springboot-restful-webservices-multi-stage -p 8080:8080 springboot-restful-webservices

podman compose -f .\docker-compose-origin.yml up -d

podman compose -f .\docker-compose-env.yml up -d

podman compose -f .\docker-compose-volume.yml up -d

podman compose -f .\docker-compose-postgresql.yml up -d
