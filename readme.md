
##Barebone Dockerized Webapp with MySQL Database: 

* sudo docker run -d -P -e MYSQL_USER=java -e MYSQL_PASSWORD=java -e MYSQL_DATABASE=javatest --name mysql orchardup/mysql

* sudo docker run -ti --rm --link mysql:mysql -v $(pwd):/host --entrypoint /bin/bash orchardup/mysql -c "sleep 4; mysql -u java --password=java -h mysql javatest < /host/init.sql; exit 0"

* sudo docker build -t javatest .

* sudo docker run -p 49160:8080 -d --link mysql:mysql javatest


You should be able to access the app on http://\<docker-host-ip\>:49160/dbtest

Inspect Database:

* sudo docker inspect \<container-id\> for IPAddresss of the container

* mysql -h IPAddresss -u root -p


* prompt for Password and enter java

* Enter show databases;

* Enter use javatest ; 

* Run select * from testdata;

Note : Ensure you have MySQL client installed. If not, use below command
`sudo apt-get install mysql-client-core-5.5`



