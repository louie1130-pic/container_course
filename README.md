# springboot-docker-course
Source code for Spring boot docker course/series

# Tutorials on Java Guides
https://www.javaguides.net/2022/12/deploy-spring-boot-application-on-docker.html

https://www.javaguides.net/2022/12/deploy-spring-boot-mysql-application-to-docker.html

https://www.javaguides.net/2022/12/spring-boot-mysql-docker-compose-example.html

https://www.javaguides.net/2022/12/docker-container-commands.html

https://www.javaguides.net/2022/12/docker-images-commands-list.html


MYSQL_ROOT_PASSWORD
This variable is mandatory and specifies the password that will be set for the MySQL root superuser account. In the above example, it was set to my-secret-pw.

MYSQL_DATABASE
This variable is optional and allows you to specify the name of a database to be created on image startup. If a user/password was supplied (see below) then that user will be granted superuser access (corresponding to GRANT ALL) to this database.


docker-compose-volume.yml
          # "Image": "84bc9437cea4c06982359de87c2947b941b113c506bc93f1c31863a3e474216b",
          # "ImageDigest": "sha256:97e030479ffc7b0594a9b411850dcf6e7d6b5e7148f8ec6fe4f96e926cd44112",
          # "ImageName": "docker.io/library/project_springboot_volume-springboot-restful-webservices:latest",

