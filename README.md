# docker-multiprojects

install docker
install docker-compose

docker-compose build
docker-compose up -d

cd docker-multiprojects

cd ./hosts/default.local.conf ./hosts/[name_host].conf
geidt ./hosts/[name_host].conf
  server_name [name_host];
  root /var/www/[name_folder]/public;
cd www
git clone [project]
mv [project] [name_folder]
cd [name_folder]
open docker: docker exec -ti php-fpm bash
